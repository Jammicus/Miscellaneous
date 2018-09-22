# The Art of Monitoring



## A Monitoring and Measurement Framework

* In the new monitoring paradigm, events and metrics are at the core of the solution.
* The data your monitor should provide a source of truth for:
	* The state of our environment
	* The performance of our environment.
* Visualising this data allows for the ready expression and interpretation of complex ideas that would otherwise take thousands of words or hours of explanation.


![](The%20Art%20of%20Monitoring/Screenshot%202017-11-29%2016.07.16.png)

* The architecture of your monitoring framework should:
	* Allow you to easily visualise the state of our environment
	* Be event. log, and metrics-centric
	* Focus on “Whitebox”, or push-based monitoring instead of “blackbox” or pull-based monitoring 
	* Provide contextual and useful notifications

### Pull versus Push

* Most monitoring systems are pull/polling based systems, such as Nagios.
	* Nagios generally queries the components being monitored, such as pinging a host.
	* The most hosts and services that get added to your environment, the more checks Nagios host will need to do.
* Wherever possible, avoid pull monitoring. This scales terribly.
* Push-based architecture defines that the hosts, services and applications are emitters, they send data about themselves to the central collector, rather than the collector querying them.
* Emitters:
	* Report when available.
	* Generally are stateless, by sending data as soon as it is generated.
	* They can use transport and mechanisms local and appropriate to themselves, rather than being forced into a choice by your monitoring tools.
	* This results in modular, functionally separated, compartmentalised monitoring solutions with selected best of breed tools rather than monolithic silos.

* Compared to pull-based approaches, which require your monitoring targets to be centrally configured on what and where to monitor. Push based approaches wait until an emitter sends data, and processes it once it arrives (or, does not arrive?)
	* This is vital for very short time based environments, which may not be up for enough time to convert it into the needed configuration for a pull based system.
* Emitters are also more secure -> They just send data to a receiver, rather than listening for network connections from the central “host”.
* Poll-based systems generally emphasise availability - “Is it up?” .
* There are only a few instances where polling is good:
	* For small, atomic actions - such as a Daemon has stopped working. 
* Orienting your focus towards availability, rather than quality and service, treats IT assets as pure capital and operational expenditure. 
	* This makes organisations see them as assets that need need to be managed - As costs which they are happy to limit and cost as they only see the cost and not the value it brings to an organisation. 
* Push-based models also tend to be more focused on measurement. You still have the availability measurement, but this is a side-effector measuring components and services. 
* As collection is distributed and there generally low overheads, you can receive a huge amount of data on various  things are tore it at high precision. 
	* The increased precision of data can then be used to more quickly answer questions about quality of service, performance, and availability.

Thought:  What about Jenkins at work: We know it occasional goes down, but we don’t consider the load that is being put on it,  EG, 100’s of builds a day. The crash rate is minuscule when you think of it in that term, rather than how often it goes now.

### Blackbox and Whitebox

* Ideally you should use Whitebox monitoring rather than blackbox monitoring.
	* Blackbox monitoring probes the outside of a service or application, which a lot of pull based systems use as their basic building block. You query the external characteristics of a service, to see whether it returns the right thing from the right place.
	* Whitebox monitoring focuses on whats inside a service or application. The application is instrumental and returns its the state of the internal components, or the performance of transactions or vents.
		* This is generally done by sending events, logs and metrics to a monitoring tool or exposing this information on a status page of some kind.
* With the white box approach, it provides an idea of the actual running state of your service of application. You get a much richer, more contextual set of information about the state of your application than blackbox monitoring. (
	* Think of blackbox as black and white, working or not working, and white box as colour, load statistics, ping times, number of queries in the last x minutes ect….

### Event, Log, and Metric-centered 

* The push and whitebox-centric architecture is going to be centred around collecting event and metric data, and using this data to monitor our environment and detect when things go wrong:
	* Events - these are generally used to notify about changes and occurrences in the environment
	* Logs - A subset of events. Helpful for letting us know whats happening, but most often useful for fault diagnosis and investigation
	* Metrics - The most important aspect

### More About Metrics

* Traditional metrics were focused on fault detection: Whether a specific system event or state has occurred. 
	* When we receive a notification about these specific system events, we usually go look at whatever metrics we’re collection, to find out what exactly has happened, and why.
	* Metrics are seen as a by-product of or a supplement to our fault detection
	* However, this is not ideal.
* We are taking a new approach, focusing on anomaly detection and pattern analysis. 
	* This will give you the potential to identify faults and issues before they occur on before the specific system event that indicates an outage is generated

### What is a metric? 

* Metrics are measures of properties in pieces of software or hardware.
* To make a metric useful, you keep track of its state by recording data points of observations over time.
	* The combination of these data point observations are called a “time series”
	* Classic example of this is website visits.  You’d periodically collect the following information:
		* Number of hits
		* Times of observations
		* Source of hits
		* Which server it hit on		
* Observations are generated collected at a fixed time interval. Which could range from one second to 5 minutes to 60 minutes and so on.
	* This is called the granularity or resolution (how often the data is collected)
* Choosing the right granularity at which to record a metric is critical. 
	* If you choose a granularity that is too course (Does not collect the data often enough) you can miss important events. 
	* If you choose a granularity that is too fine, you’ll gather loads of irrelevant data.
* Metrics are generally chronologically ordered list of observations, with the oldest at the front, and the newest at the end.
* A 2D plot will have the time on the x, and a metric on the Y, such as CPU usage. They may even have a mathematical function applied to it.

### Types of Metrics

#### Gauges

* Gauges are numbers that are expected to change over time. 
* Gauges are essentially a snapshot of a specific measurement. 
	* Classically, gauges are used for the following metrics:
		* CPU
		* Memory
		* Disk usage

#### Counters

* Counters are numbers that increase over time, and never decrease.
* They can however be reset to 0 and are then increased again after a specified time period or after an event,
	* Classically, counters are used for:
		* System uptime
		* Number of bytes sent and received by a device
		* Number of logins in a month.
* Counters are useful as they allow you to calculate the rates of change.
	* For each observed value is a moment in time T, you can subtract the value at T from the value at T+1 to get the range between two values. 

#### Timers

* Timers track how long something took.
* Typically used for monitoring inside an application
	* Classically used for:
		* Testing how long a method takes
		
#### Metric Summaries

* Often single values of a metric are not of use. You need to visualise a metric by applying a mathematical transformation to it.
* Some common math functions that you might want to apply:
	* Count or n - Number of observations in a specific time interval
	* Sum = Adding values from all observations in a specific time interval
	* Average = The Mean of all values in a specific time interval
	* Median =  The middle value. Where 50% of our values are above, and 50% are below it.
	* Percentiles - Measuring the values below which a given percentage of observations in a group of observations fall.
	* Standard Deviation = Standard deviation from the mean in the distribution of our metrics.  Measure the variation, or change in a data set. 
		* A standard deviation of 0 means the distribution is equal to the mean of the data. 
		* Higher deviations mean the data is spread out over a range of values. 
	* Rates of change - Represents the degree of change between data in a time series. 
	* Frequency distribution and histograms - This is a frequency distribution of data set. You group the data - called “binning” - and present the groups in a such a way that their relative sizes are visualised. This is most often shown as a histogram. 

### Metric Aggregation

* You’ll often want to show aggregated views of metrics from multiple sources, such as disk space of all your application servers 
* Typically this is done by aggregating(joining) the data from multiple sources into a single plot (Eg, all the hard drive info from virtual machines into one graph)
* You’ll want both single and aggregated metrics
	* Single to drill down into specific issues
		* Aggregated to see the high-level state  of the health of your environment.

### Contextual and useful notifications


* When building a notification system, you need to answer the following:
	* Who to tell about a problem
	* How to tell them
	* How often to tell them
	* When to stop telling them, do something else, or escalate to someone else.
	* And most importantly, What to tell whoever is receiving the notification
* When designing the notification itself, think:
	* How to make the notification actionable, clear and articulate. 
	* How to add context to the notification - how to send notifications that contain additional information about the component we’re notifying on
	* Aligning our notifications with the business needs of the service being monitoring so we only notify on whats useful to the business.
	* Remember that notifications are read by humans, not computers, and design them accordingly

### Visualisation

* Metrics and their visualisations are often tricky to interpret. 
* Humans tend towards apophenia - the perception of meaningful patterns within random data - when viewing visualisations.
	* This can lead to sudden leaps from correlation to causation
* The ideal visualisation will clearly show the data, with emphasis on highlighting substance over visuals.
* The following broad rules should be followed (Taken from Edward Truftes: The Visual Display of Quantitative Information):
	* Clearly show the data
	* Induce the viewer to think about the substance, not the visuals
	* Avoid distorting the data
	* Make large data sets coherent
	* Allow changing perspectives of granularity, without impacting comprehension.

### Why is this Architecture? What’s wrong with Traditional Monitoring?

* When you describe “Traditional Monitoring”, especially in reactive environments, what we’re usually talking about is fault detection.
	* Its best thought of as watching an object to know it working, by polling it for its state.
	* Historically these are boolean checks, whether its replying to your requests or not, or whether a value falls in a  specific range - These are known as check selection
	* These checks can  can be:
		* Experience or learning based - based on what you’ve read online, you run checks against these
		* Reactive - A check or checks in response to an indecent or outage that has occurred in the past.
* These however, **carry a wide set of issues**

#### Static Configuration

* Checks in traditional monitoring generally have static configuration. 
	* These need to update as the system grows, evolves or changes. These do not adapt well to change!
* Checks often require you to duplicate the configuration on both a server and the object being monitored
	* A slack of single source of truth (Or shared code) leads to increased risk of inconsistency and difficulty in managing checks. 
	* Also means the monitoring server needs to know about resources being monitored before they can be monitored. (Very bad for dynamic/changing landscapes”
* Many faults are from configurations that have not adapted, or ins static configuration, has not been updated. 
	* Changes get missed, or notifications are given on the wrong thing

#### Inflexible Logic and Thresholds

* Checks are often designed using inflexible boolean logic or arbitrary static in time thresholds. 
	* They rely on a specific result or range being matched. 
	* They dont consider the dynamic aspects of a system. 
	* Breaches or matches which are important or have have been triggered by exceptional events  may never be triggered. 
* Arbitrary static thresholds are always wrong.
	* They set up a point-in-time boundary
	* During that period, everything beneath that boundary is judged normal and everything above is abnormal. 
	* This is inflexible, and artificial 
	* One systems abnormality may be another normal operation -> Leading to notifications wired to arbitrary thresholds will frequent fire off false positives.
* Boolean checks suffer similar issues to arbitrary thresholds..
	* Usually they are singletons, and often can’t take advantage of trends or prior event history. Is this a really a failure? is this a critical failure?

#### Object-centric

* The checks tend to be object centric, usually centric to single hosts or services.
* They make you define a check on an object or objects.
	* This is bad, as the objects are generally part of a much larger, often more complex system.
	* Single objects in these cases frequently lack any context and limit your ability to understand what the checks output means to the broad system.
		* Byproduct of this is that is hard to determine the criticality of the objects failure.
	
#### An interlude into pets and cattle

* Traditional monitoring environments are often marked by thousands of checks. 
* This is bad as its extremely hard to scale, manage or massively duplicate and more often than not the majority of these checks are not useful in doing fault diagnosis.
* Another key factor is fault resolution is changing.
* Hosts can be thought of as pets or cattle. 
	* Some have names and are loving raise and looked after. If something goes wrong you fix them immediately and ensure they stay is good condition. These are known as pets
	* Sone are mass produced. They are basically identical to each other. If something goes wrong with one of them, all of them re put down and replaced. These are cattle.
* Modern environments treat hosts as cattle. 
	* They should be configured automatically and rebuild automatically when something goes wrong. 
* For our cattle environments, we do not need hundreds of checks on individual components because the default fix for the majority of programs is to rebuild the host or scale the service

#### What will we do Differently?

* Rather than infrastructure-centric checks, such as pinging a host. We’re going to configure our hosts, services and applications to emit events and metrics.
* There are two main benefits of events and metrics:
	* If a metric is measuring, an event is reporting, or a log is spooling, then the service is available. If it stops measuring or reporting then its likely the service is not available. 
		* Available = where a host, service or application is operable and functioning in line with expectations. 
* This will work by the use of the event router in your monitoring framework. 
	* Its responsibility will be to track our events and metric. 
	* It can also do a lot of other interesting things such as sending them to visualisation tools, or using them and their values to notify us of performance issues.

Example: Configuring a web server to emit metrics showing the current load

We configure the event router to detect:
	If the metrics stop being reported (We assume that something has gone wrong)
	If the value of a metric matched some criteria we’ve deployed. (Gives us long term metrics to work with and analyse)

#### Smarter Threshold Input

* We will still use thresholds, but the data we feed into those thresholds is considerably more sophisticated. 
* In our new monitoring framework, we will:
	* Collect frequent and high-resolution data
	* Look at windows of data not static points in time
	* Calculate smarter input data.
* Using the above methodology we’re more likely to identify if a state is an actual issue instead of an anomalous spike or transitory state

##### Averages

* The de facto metric analysis method.
* These assume there is a normal event or that your data is a normal distribution (Assumed all participants are the same, such as each VM has the same memory and cpu speed, ect)
* However, as seen in the following image, the average give you distorted view:
![](The%20Art%20of%20Monitoring/Screenshot%202017-11-30%2015.18.00.png)

##### Median

* The median is the dead center of our values: Exactly 50% of the values are below, and 50% of the values are above it. 
	* If theres a odd number, the median is the value in the middle.
* You still get problems, such as with the mean.  That when data is spread out between very high and small values, you distorts your view of the data. 
	* This would be okay if a data was on a bell-curve - However, real life data is not generally like that.

![](The%20Art%20of%20Monitoring/Screenshot%202017-11-30%2015.26.17.png)

##### Standard Deviation

* The standard deviation measures the variation, or spread, in a data set. (Distance from the mean)
	* If the Standard Deviation is 0, it means that the data is generally close to the mean.
	* Higher standard deviations mean that the data is more distributed and further from the mean.
* Again, this works best when the data is a normal distraction, eg, close to the mean. 
* In a normal distraction theres a simple way of articulating the distribution: the empirical rule:
	* Within the rule, one standard deviation or 1 to -1 will represent 68.27% of all transactions on either side of the mean. 
	* Two standard deviations, or 2 to  -2 would be 95.45% 
	* And three standard deviations will represent 99.73% of all transactions
* The issue with this is without normal distraction of data, the resulting stand deviation can be misleading (Image a catastrophic event that is miles away from the standard deviation)

![](The%20Art%20of%20Monitoring/Screenshot%202017-11-30%2015.35.30.png)

##### Percentiles. 

* Percentiles measure the value below which a given percentage of observations in a group of observations fall
	* Essentially, they look at the distribution of values across your data data set.
* Percentiles make a lot of sense because they make the distribution easy to grasp and identify outliers.
	* For example, if 99.97% of your website viewers access the website within 10 milliseconds, the 1% , or the 1 percentile, can be looked at to address their problem.  (Empirical rule will miss this)
![](The%20Art%20of%20Monitoring/Screenshot%202017-11-30%2015.41.23.png)
	* Above, the 75th percentile is 5.5 seconds (p7). This indicates that 75% completed in 5.5seconds, and the resulting 25% were slower.
	* We can also see that the 99th percentile, shows 10.74, this means 99% of users had a request times of less than 10.74, and 1% had more than 10.74
	* This approach gives us a real picture of how our application is performing.
	* If we’re comfortable with 99% of users getting 10.74 second response times or better and 1% being slower than we dont need to consider further tuning

Example Data set:
![](The%20Art%20of%20Monitoring/Screenshot%202017-11-30%2015.44.37.png)

* Above, the 75th percentile is 10 seconds and the 99th is 12 seconds.
* The 99th percentile provides a clear picture of the broader distribution of our transactions. 
* This shows us that not all of our users are enjoying the experience, where as the mean would say that our users are getting into the website easily. 

However, you should graph several combinations of metrics to get a clear picture of the data
* As an example, for measuring the latency its best to display:
	* The 50th percentile (Or median)
	* The 95th and 99th percentiles
	* The max value

## Collecting Data For Our Monitoring Framework

* In our framework we’re going to focus on agent-based collection of data.
* We’re going to prefer the running of local agents on hosts, and focus on the instrumentation of applications and services
*  Where ever possible, each host or service will be self-contained and responsible for emitting its own monitoring data. Locally we’ll configure collection and the destination of our data.
* We’re also going to try and avoid remote checks of hosts and services (With a few exceptions we will see later)
* Our data collection will include the following:
	* Resource information, like consumption of CPU or memory
	* Performance information, like latency and application throughput
	* Business and user-experience metrics, like volumes or the amounts of transactions or numbers of failed logins
	* Log data from hosts, services and applications. 
* Much of the data and observations we collect directly as metrics, and in some cases, we’ll also convert observations in the form of events into metrics

### Overhead and the Observer Effect

* You need to consider that collecting the data can also impact the values of being collected.
	* Methods used to collect data will consume some of the resources we’re monitoring. 
	* This can cause excessive overheads and actually influence the state of the machine you are monitoring, or trigger notifications and outages. (This is also known as the observer effect)
	* You MUST keep this in mind, and design your code to use the least amount of resources as possible.

- - - -

## Managing Events and Metrics With Riemann

* The ideal design for our event router is:

![](The%20Art%20of%20Monitoring/Screenshot%202017-11-30%2016.17.57.png)

* With the following design, we want the routing engine to:
	* Receive our events and metrics
	* Maintain sufficient state to allow us to do event matching; provide context for notifications and for checks based on trending
	* Munge events including extracting metrics from events
	* Categorise and route data to be stored, graphed, altered on, or sent to any other potential destinations
* To do this, we’re using a tool called Riemann
	* Event based tool for monitoring distributed systems. 
	* Works in a push model, receiving events rather than polling them. 
	* All our machines will send their events into Riemann, and riemann will make the necessary decisions about those events. 

### Introducing Riemann

* Written in Clojure and runs on top of the JVM
* Has the majority of features we want in a system. (Eg push based)
* Open source.

#### Riemann Architecture and Implementation 

* In the book, we’ll:
	* Install Riemann servers in the Production A and Production B environments
	* Install Graphite and Grafana servers in the production A and Production B environments
	* Configure the downstream Riemann, Graphite, and Grafana servers in our Mission Control Environment 

![](The%20Art%20of%20Monitoring/Screenshot%202017-11-30%2016.30.15.png)

#### Installing Riemann

* The book is going to host it on the following hosts:
	* Ubuntu 14.04 host in production A with a hostname of `riemanna.example.com` and an IP address of 10.0.0.110
	* A Red Hat Enterprise Linux (RHEL) 7.0 Host in production B with a hostname of `riemannb.example.com` and an IP address of 10.0.0.120
	* A Ubuntu 14.04 host in Mission Control with a hostname of `riemannmc.example.com` and an IP address of 10.0.0.100.

I’M NOT GOING TO COVER THE REST OF THIS, READ THE BOOK IF YOU WANT TO DO IT

Note: I would suggest Prometheus over Riemann.


## Introducing Graphite and Grafana

* The design for a metrics storage and visualisation solution is as follows:

![](The%20Art%20of%20Monitoring/Screenshot%202017-12-01%2012.22.20.png)

* With this design, we want our graph storage and visualisation to be able to:
	* Receive and process our metric data efficiently
	* Scale as we grow our environment
	* Provide scalable, efficient storage of metrics data
	* Provide a mechanism to elegantly degrade the granularity of metric data, storing at a high granularity for recent metrics and degrading for older metrics
* To provide the storage and visualisation capabilities we’re going to install and configure a tool called [Graphite](https://graphiteapp.org/) 

### Introducing Graphite

* Graphine is an engine that stores time-series data and then can render graphs from that data using API.
* Written in Python
* Simple and fast - But not necessarily the most modern. 
	* Relies on flat files, for example, rather than more modern database-style implementations.
* To get metrics into graphite, you need to configure Prometheus/Rienmann to send metrics to it.
* We will use a dashboard called https://grafana.com/ to see the results 

### Graphite Components - Carbon (The Daemon)

* Carbon is a collection of event-driven daemons that listen on network ports
* Two major daemons we’ll be using in the book: `carbon-cache` and `carbon-relay`
* `carbon-cache` daemon listens, receives and writes time-series data to storage. 
* `carbon-relay` daemon listens, receives, and forwards time-series dat to `carbon-cache` servers.
* Both the deamons allow us to scale and cluster Carbon across individual and multiple hosts 
	* For example - Having a host behind a load balancer running multiple `carbon-relay` daemons that receives events and then forwards them to another host running multiple `carbon-cache` daemons that ingest and process our data
* For now, we’ll run everything on a single host, and learn about how to scale Carbon later in the book
* Carbon daemons expect a stream of time-series data, which consist of:
	* A metric
	* A timestamp
	* A value
* Metrics can be anything that comes in the form of a measurable output, such as: systems metrics, applications metrics, business metrics.
* After Carbon receives metrics, it periodically flushes them to  a storage database called Whisper

### Graphite Components - Whisper (The Daemon)

* Whisper is a lightweight, flat-file database format for storing time-series data.
* Not a daemon or service, its a database file format.
* Carbon writes metric data to the disk in the whisper format. 
* Each unique metric type is stored in a fixed size file with a `.wisp` suffix:

![](The%20Art%20of%20Monitoring/Screenshot%202017-12-01%2012.50.29.png)
 
* The size of each database file is determined by the number of data points stored.
* The data is written to the disk  by using the usual bottleneck for scaling Graphite servers

### Graphite Components - Graphite Web, Graphite-API and Grafana.

* Graphite web is a Django-based web UI that can query the Carbon daemon and read Whisper data to return metrics data
* Can be used to compose graphs directly, or it can provide a RESTful API that can be used by third-party tools to extract metrics to compose graphs.
* The API can return data or rendered output like .png images
* Its not a good idea to use Graphite web - Its problematic to install and configure, along with its interface being somewhat dated and hard to use.
* Instead, we’ll use Grafana,.
* Grafana is a open source metrics dashboard that supports Graphite, InfluxDB, and OpenTSDB. 
* When using Graphite, Grafana runs not op of the Graphite Web API. 
* Rather than installing the full graphite web component, we’re going to install an API integration and them the Grafana dashboard onto of that API

### Graphite Architecture.

* The overall architecture is:
	* Carbon receives the incoming metrics  and writes it  into the Whisper format on the disk
	* The graphite API makes those metrics written by carbon available to grafana.


INSTALLATION OF GRAFANA AND GRAPHITE FOLLOWS THIS, THERE IS WAY OT MUCH TO COVER, READ THE BOOK IF YOU NEED IT

----





