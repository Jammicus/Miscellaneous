# 12 factor App

## Code base

* One codebase tracked in revision control, many deploys
* There is always a one to one correlation between the codebase and the app:
	* If there are multiple codebases, its not an app, its a distributed system. Each component in a distributed system is an app, and each can individually comply with twelve-factor
	* Multiple apps sharing the same code is a violation of twelve-factor. The solution here is to factor shared code into libraries, which can be included through the dependancy manager.
* There is only one codebase per app, but there will be many deploys of the app. 
* A deploy is a running instance of the app., including the developers local copy. 
* The codebase is the same across all deploys, although different versions may be active in each deploy.  (Eg, developer has commits not deployed.)

![](12%20factor%20App/Screen%20Shot%202018-01-14%20at%2011.36.43.png)

## Dependencies

* Explicitly declare and isolate dependancies. 
* Most programming languages offer a packaging system for distributing support libraries, (eg, ruby gems)
* Libraries installed through a packaging system can be installed system wide (aka site packages) or scoped into the directory containing the app (Vendoring or bundling)
* 12 factor app never relies on implicit existence of system wide packages.
* All dependencies are exactly, viral a dependency declaration manifest. 
* It uses a dependent isolation tool during execution to ensure that no implicit dependencies “leak in” from the surrounding system. 
* The full and exploit dependency specification is applied uniformly to both production and development.
* As an example, gem file can be used to specify versions of the dependancy. 
* 12 factor apps also do not reply on the implicit existence of any system tools, such as Curl. While they exist on many, they may not exist on a few. We have no control where the app may run in the future. 
* If an app needs to shell out  to a system tool, that tool should be ventured into the app.

- - - -

## Config

* Config should be stored in the environment
* An apps config is everything that is likely to vary between deploys (staging, production, dev).
* Config includes:
	* Resource handles to the database, memcached and other backing services
	* Credentials to external services such as Amazon s3 or Twitter
	* Per-deploy values such as the canonical hostname fore ploy.
* Apps sometimes stored config constants in code. This is a direct violation of twelve-factor, which requires strict separation of config from code.
* Config varies substantially across deploys, code does not.
* Litmus test for whether an app has all config correctly factored out of the code is whether the codebase could be made open source at any moment, without compromising any credentials.
* Config does not include internal application config, such as  code modules are connected in spring. 
* Another approach to config is the use of config files which are not checked into revision control, such as config/database.yml. 
	* However this has the weakness of accidentally being merged in
* Twelve factor app stores config in environment variables (Often shortened to env vars or env
	* This is good as they are language and OS-agnostic 
* Environment vars should be full orthogonal to other env vars. They should NOT be grouped together as “environments”. They should be independently managed for each deploy 

- - - -
## Backing Services

*  Treat backing services as attached resources
* Backing service = any service the app consumes over the network as part of its normal operation (Eg, datastore, messaging/queing system, SMTP services,Backing services  caching systems.)
* The code for twelve-factor app makes no distinction between local and third party services
* Both are attached resources, accessed via a URL or other lkocator/credentials stored in the config
* A deploy of the 12 atop app should be able to swap out a local MySQL database with one managed by a third party (Eg Amazon RDS) without any changes to the apps code. 
* Each distinct backing service is a resource. Eg, each MySQL database is a resource on its own. 
* 12-factor app treats these databases as attached resources. which indicates their loose coupling to the deploy they are attached to.
* Resources can be attached to and detached from deploys at will. 
	* Eg if a database fails, you should be able to plug in a new database without any code changes
	
![](12%20factor%20App/Screen%20Shot%202018-01-18%20at%2010.00.13.png)
 
- - - -
## Build, Release, Run

>  Strictly separate build and run stages  

* Codebases are transformed into a non-development deploy through three stages:
	* The build stage -> Transformation which converts a code repo into an executable bundle known as a build.  Using the version of the code at a commit specified by the deployment process, the build stage fetches vendors dependencies and compiles binaries and assets
	* The release stage takes the build produced by the build stage and combines it with the deploys current config. The resulting release contains both the build and the config and is read for immediate execution in the execution environment 
	* The run stage (AKA runtime) runs the app in the execution environment, by launching some set of the apps processes against a selected release.
* The 12factor app uses strict separation between the build, release and run stages.
	* Eg, its impossible to make changes to the code at runtime, since there is no way to propagate those changes back to the build stage.
* Every release should always have a unique release ID, such as a timestamp of the release, or an incrementing number (eg v100). Releases are an append-only ledger and a release cannot be mutated once it is created. Nay change must create new release
* Builds are initiated by the app developers whenever new code is deployed.
* The run stage should be kept to as few moving parts as possible, since problems that prevent an app from running can cause it to break in the middle of the night when no developers are on hand.
- - - -
## Processes

> Execute the app as one or more stateless process  

* The app is executed in the execution environment as one or more proceses
* In the simplest case, the code is a stand alone script,. 
* On the other end of the spectrum, a production deploy of a sophisticated app may use many process types, instantiated into zero or more running processes
* Twelve-factor processes are stateless, and share nothing
* Any data that needs to persist must be stored in a stateful backing service, typically a database.
* The memory space or filesystem of the process can be used as brief, single -transaciton cache. (Eg, downloading a large file, opening it, and storing the results of the operation in the database.)
* 12 factor app assumes that anything cached in memory or on disk will be available on a future request or job - with many processes of each type running, chances are high that a future request will be served by a different process.
* We assume that restart will wipe all local states
* 12-factor app prefers to do compiling during the build stages. 
* Sticky sessions are a violation of 12-factor, and should never be used or relied upon.
- - - -
## Port Binding

> Export services via port binding  

* Web apps are sometimes executed inside a web server container (eg, java running inside tomcat)
* 12-factor app is complete self-contained and does not rely on runtime inject of a web server into the execution environment to create a web-facing service. The web app exports HTTP as a service by binding to a port, and listening to requests coming in on that port (eg, facebook.com:8080
* This is typically implemented using dependency declaration to add a web server library to the app such as Jetty for Java. 
	* This happens entirely in the user space (Within the apps code)
* HTTP is not the only service that can be exported by port binding. Nearly any kind of server software can be run via a process binding to a port and awaiting incoming requests. (Eg, Redis)
* Note also that the port-binding approach means that one app can become the backing service for another app, by providing the URL to the backing app as a resource handle in the config for the consuming app
- - - -
## Concurrency

> Scale out via the process model  

* Any computer program, once run, is represented by one or more processes.
* Web apps have taken a variety of process-execution forms. (Eg, JVM provides one massive uber process that reserves a large block of system resources on startup, with concurrency managed internally via threads.)
* Running process(es) are only minimally visible to the developers of the app
* 12factor apps treat processes as a first class citizen
* Processes in the 12factor app take strong cues from [the unix process model for running service daemons.](https://adam.herokuapp.com/past/2011/5/9/applying_the_unix_process_model_to_web_apps/)
* This model states the developer can architect their app to handle diverse workloads by assigning each type of work to a process type
	* Eg, HTTP requests may be handle by a web process, while long running background tasks handled by a worker process
* This does not exclude individual processes from handling their own internal multiplexing, via threads inside the runtime VM, or the async/evented model around itools such as Node.js
* An individual VM can only grow so large (vertical scale), so the application must also be able to span multiple processes running on multiple physical machines.
* The process model truly shines when it comes time to scale out.
	* The share-nothing, horizontally partition able nature of twelve-factor app processes means that adding more concurrency is a simple and reliable operation.
	* The array of process types and number of processes of each time is known as **process formation**
* Twelve factor app processes should never demonise or write PID files. 
* Instead, rely on the operating systems process manager( such as systemd), to manage output streams, respond to crashed processes, and handle user-imitation restarts and shutdowns 
- - - -
## Disposability

> Maximise robustness with fast startup and graceful shutdown  

* 12factor apps processes are disposable, meaning that can be started and stopped at a moments notice. 
* This facilitates fast elastic scaling, rapid deployment of code or config changes and robustness of production deploys. 
* Processes should strive to minimise startup time. Ideally, a process takes a few seconds from the time the launch command is executed until the process is up and ready to receive requests or jobds.
* Short startup time provides more agility for the release process and scaling up.
	* It also aids robustness, because the process manager can more easily move process to new physical machines when warranted. 
* Process shutdown gracefully when they receive a SIGTERM signal from the process manager.
* For a web process, a graceful shutdown is achieved by ceasing to listen
* For a worker process, graceful shutdown is achieved by returning the current job to the work queue. 
* Implicit in doing this is that all jobs are reentrant which is typically is achieved by wrapping the results in a transaction, or making the operation idempotent.
* Processes should be roust against sudden death, in the case of a failure in the underlying hardware. 
* A recommended approach is use of a robust queueing backend, such as Beanstalkd, that returns jobs to the queue when clients are disconnected time out. 
* Either way, a 12 factor app is architected to handle unexpected, non-graceful terminations. 
* Crash-only design takes this concept toits logical conclusion


- - - -
## Dev/Prod Parity

> Keep development, staging and production as similar as possible.  

* Historically theree have been substantial gaps between development (A developer making live edits to a local deploy of the app) and production (A running deploy of the app accessed by end users) 
* These gaps manifest in three areas:
	* Time gap: A developer may work on code that takes days, weeks or even months to go into production
	* The personnel gap: Developers write codes, ops engineers deploy it.
	* The tools gap: Developers may be using a stack like NGINX, SQLite and OSX, while production deploy uses Apache, MySQL and Linux.
* The 12-factor app is designed for continuous deployment by keeping the gap between development and production small.
* Looking at the three gaps described above:
	* Make the time gap small: a developer may write code and have it deployed hours or even just minutes later
	* Make the personnel gap small: Developers who rote code are closely involved in deploying it and watching its behaviour in production
	* Make the tools gap small: keep development and production as similar as possible
* Summarisation:

![](12%20factor%20App/Screen%20Shot%202018-01-27%20at%2012.37.31.png)

* Backing services such as the apps database, queuing system or cache, is one area where dev/prod party is important. 
* Many languages offer libraries which simplify access to the backing service, including slaters to different types of services
* Examples:

![](12%20factor%20App/Screen%20Shot%202018-01-27%20at%2012.37.35.png)

* Developers sometimes find a great appeal in using a lightweight  backing service in their local environments, while a more serious and robust backing service in their local environments, while a more serious and robust backing service will be used in production.
* The twelve-factor developer resists the urge to use different backing services between development and production.

- - - -

## Logs

> Treat  logs as event streams  

* Logs provide visibility into the behaviour of a running app. 
* In server based environments, they are commonly written to a file on disk ( A logifle), but this only a output format
* Logs are the stream of aggregated, time-ordered events collected from the output streams of all running processes and backing services
* Logs in their raw form are typically a text format with one event per line. (Though backtraces from exceptions may span multiple lines.)
* Logs have no fixed beginning or end, but flow continuously as long as the app is operating
* A twelve-factor app never concerns itself with routing or storage of its output stream
* It should not attempt to write or manage log files
* Instead, each running process writes its event stream, unbuffered, to stdout. 
* During local development, the developer will view this stream in the foreground of their terminal to observe the apps behaiour
* In staging or production deploys, each process’ stream will be captured by the execution environment, collated together with all other streams from the app, and routed to one more final destinations for viewing and long-term archival.
* These archival destinations are not visible to or configurable by the app, instead are completely managed by the execution environment. 
* Open source log routers (such as Logplex and Fluentd) are available for this purpose
* The event stream for an application can be routed to a file, or watched via realtime tail in a terminal.
* Most significantly, the stream can be sent to a log indexing and analysis system such as Splunk, or a general purpose data warehousing system such as Hadoop/Hive
* These systems allow for great power and flexibility for introspecting an app behaviour over time, including:
	* Finding specific events in the past
	* Large-scale graphing of trends (such as requests per minute)
	* Active alerting according to user-defined heuristic (such as an alert when the quantity of errors per minute exceeds a certain threshold) 

- - - -

## Run Admin/management tasks as one-off processes

* The process formation is the array of processes that are used to do the apps regular business (such as handling web requests) as it runs.
* Separately, developers will often wish to do one-off administrative or maintenance tasks in the app, such as:
	* Running database migrations
	* Running a console to run arbitrary code or inspect the apps models against the live database. (Most languages provide a REPL by running the interpreter without any arguments)
	* Running one-time scripts committed into the apps repo
* One-off admin processes should be run in an identical envinroment as the regular long-running processes of the app.
* They run against a release, using the same codebase and config as any process run against the release. 
* Admin code must ship with the application code to avoid synchronisation issues
* The same dependency isolation techniques should be used on all process types.
	* Eg,  A python program using Virtualenv should use the vendor bin/python for running both the Tornado web server and any manage.py admin processes.
* Twelve factor strongly favours languages which provide a REPL shell out the box, and which make it easy to run one-off scripts.
* In a local deploy, developers invoke one-off admin processes by a direct shell command inside the apps checkout directory. 
* In a production deploy, developers can use ssh or other remote command execution mechanism provided by that deploys execution environment to run such a process.

