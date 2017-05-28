# Selenium Testing Tools Cookbook - Unmesh Gundecha

---------------------

## Locating Elements

* FindElement method returns a webelement object based on a specific search criteria
* FindElements returns all elements that meet a certain criteria
* The ways you can find elements are:
	* By.id
	* By.name
	* By.class
	* By.tagname
	* By.linkText
	* By.partialLinkText
	* By.CssSelector
	* By.xpath

## Working With Selenium API
* Once you have found an element, selenium provides many methods to interact and manipulate elements
* To get the text from an element, use `.getText()`
* To get a elements attribute, use `.getAttribute("x")` on the element
* To get the CSS value, use `.getCssValue("x")`
* To do actions on a element, use the Actions class

Eg

```
Actions builder = new Actions(driver);
builder.click(element)
builder.keyDown(Keys.CONTROL)
.build().perform

//Note, you must use build().perform() at the end to do the series of actions
```

 * To double click, use `.doubleClick(element)` from the actions class
 * To drag and drop, Use `dragAndDrop(source,target)` in the actions builder class

### Executing Javascript Code
 
 * To execute javascript code, use a Javascript executor

 Example
 
 ```
 
 JavascriptExector js = (JavascriptExecutor) driver;
 
 String title = (String) js.executeScript ("return document.title");
 
 ```
 
### Taking Screenshots
 
 * Selenium provides the TakeScreenshot interface

 ### Maximizing the Browser Window
 
 * Use `driver.manage().window().maximize();`

TODO AUTOMATING DROPDOWNS
 
## Controlling the Test Flow


### Implicit Waits

* You can use implicit waits to wait a specific amount of time.
* This is useful if a element is not in the DOM when you get to that partof the test

Example

```
driver.manage().timeouts().implicitluWait(10, TimeUnit.SECONDS); 
```

### Synchronizing a test with an explicit wait

* Explicit waits wait until a condition is met
* Selenium provides the ExpectedCondition class for this.
* Some of the methods provided are:
	* `elementToBeClickable(x)`
	* `elementToBeSelected(x)`
	* `presenceOfElementLocated(x)`
	* `textTobePresentInElement(x,y)`
	* `titleContains(x)`
* Explicit waits work by checking the object every 500ms to see whether the operation can be before
* You also need to specify when after a certain period of polling, selenium should stop

Example

```
WebDriverWait wait = new WebDriverWait(driver, 10);
wait.until(ExpectedConditions.titleContains("selenium"));
```

### Synchronizing a test with custom-expected conditions

* Can use the ExpectedConditions class on our explicit waits to check for our own custom conditions

Example
```
WebElement message = (new WebDriverWait(driver, 5)). until( new ExpectedCOndition<WebElement>(){
@Override
public WebElement apply (WebDriver d) {
return d.findElement(By.id("page4"));
}});
```

#### Waiting for Elements Attribute Value To Update

```

(new WebDriverWait(driver, 10)).until(new ExpectedCondition<Boolean>()   {       public Boolean apply(WebDriver d) {           return d.findElement(By.id("userName")).   getAttribute("readonly").contains("true"); 	 }});
 	 
```

#### Waiting for an Elements Visibility

```
 (new WebDriverWait(driver, 10)).until(new ExpectedCondition<Boolean>()   {       public Boolean apply(WebDriver d) {           return d.findElement(By.id("page4")).isDisplayed();}});

```

#### Waiting for Dom Events

```
(new WebDriverWait(driver, 10)).until(new ExpectedCondition<Boolean>()   {       public Boolean apply(WebDriver d) {           JavascriptExecutor js = (JavascriptExecutor) d;           return (Boolean)js.executeScript("return jQuery.active == 0");}});

```

### Checking Elements Presence


* Use `isElementPresent(x)`

### Checking Elements Status

* Use one of the following:
	* `isEnabled()`
	* `isSelected()`
	* `isDisplayed()`

### Identifying and Handling Pop windows By Name

* You can switch between windows using `webdriver.switchTo().window(Windowtitle)`
* The window title should be the windows Name Attribute value

### Identifying and Handlign Pop windows By Title

```
   @Test   public void testWindowPopupUsingTitle() {       //Save the WindowHandle of Parent Browser Window       String parentWindowId = driver.getWindowHandle();       //Clicking Visit Us Button will open Visit Us Page in a new Popup       //Browser Window       WebElement visitButton = driver.findElement(By.id("visitbutton"));       visitButton.click();       //Get Handles of all the open Popup Windows       //Iterate through the set and check if tile of each window matches       //with expected Window Title       Set<String> allWindows = driver.getWindowHandles();       if(!allWindows.isEmpty()) {       86for (String windowId : allWindows) { 
               try {                   if(driver.switchTo().window(windowId).getTitle().  						 equals("Visit Us")) {                       //Close the Visit Us Popup Window                       driver.close();						break; }               }               catch(NoSuchWindowException e) {                   e.printStackTrace();               }			} }       //Move back to the Parent Browser Window       driver.switchTo().window(parentWindowId);       //Verify the driver context is in Parent Browser Window       assertTrue(driver.getTitle().equals("Build my Car -   Configuration"));   }
```

### Identifying and Handling a pop-up window by its content

```
@Test   public void testWindowPopupUsingContents()   {       //Save the WindowHandle of Parent Browser Window       String currentWindowId = driver.getWindowHandle();       //Clicking Chat Button will open Chat Page in a new Popup Browser       //Window       WebElement chatButton = driver.findElement(By.id("chatbutton"));       chatButton.click();       //There is no name or title provided for Chat Page Popup       //We will iterate through all the open Windows and check the       //contents to find       //out if it's Chat Window
    //Find the Close Button on Chat Popup Window and Set<String> allWindows = driver.getWindowHandles();if(!allWindows.isEmpty()) {    for (String windowId : allWindows) {        driver.switchTo().window(windowId);            if(driver.getPageSource().contains("Build my Car -Configuration - Online Chat")) {close the Popupdirectlyid("closebutton"));//by clicking Close Button instead of closing itWebElement closeButton = driver.findElement(By.closeButton.click();                       break;                   } catch(NoSuchWindowException e) {                       e.printStackTrace();                   }} }       }       //Move back to the Parent Browser Window       driver.switchTo().window(currentWindowId);       //Verify the driver context is in Parent Browser Window       assertTrue(driver.getTitle().equals("Build my Car -   Configuration"));   }


```

### Handling Javascript Alerts

* WebDriver provides the Alert class for handling alerts

```
		try {           //Get the Alert           Alert alert = driver.switchTo().alert();           //Get the Text displayed on Alert using getText() method of   Alert class           String textOnAlert = alert.getText();           //Click OK button, by calling accept() method of Alert Class           alert.accept();           //Verify Alert displayed correct message to user           assertEquals("Hello! I am an alert box!",textOnAlert);
            } catch (NoAlertPresentException e) {        e.printStackTrace();}

```

* driver.switchTo.alert() will throw a NoAlertPresentException if the alert is not present

### Handling A Confirmation Box Alter

* These boxes provide the options to press OK or Cancel
* The OK button returns true, and the cancel button return false

Example

```
@Test
public void testConfirmAccept()
{
	WebElement button = driver.findElement(By.id("confirm"));
	button.click()
	
		try{
		
			Alert alert = driver.switchTo().alert();
			alert.accept()
			
			WebElement message = driver.findElement(By.id("demo"));
			assertEquals("Alert message", message.getText();
			
			} catch (NoAlertPresentException e) {
			e.printStackTrade();
			}
		}
	}

```

### Handling A Promt Box Alert

* These are alerts where the user needs to add text to the box
* Has Ok and cancel buttons. 
* Ok returns the input value, cancel returns null

Example

```
@Test
public void testPrompt() {
	WebElement button = driver. findElement(By.id("prompt"));
	//Click to open the alert
	button.click();
	
	try {
		Alert alert = driver.switchTo().alert();
		//Send value into the input box on the alert
		alert.sendKeys("Foo")
		
		WebElement message = driver.findElement(By.id("prompt_demo"));
		assertEquals("Hello!", message.getText());
		
		} catch (NoAlertPResentException e) {
		e.printStackTrade();
		}
	}
	
```

---------
## The Page Object Model

* Test code needs to be treated as production code, and be required to have similar standard and patterns.
* The Page Object model pattern helps in reducing duplication, and making the tests easier to maintain.
* We develop a class that serves as an interface to a web page in the application. This models the web pages properties and behaviours
* Tests should use objects of the page at a high level, where any change in layout or attributes used for the fields in the page should not break the test

### Using the PageFactory class for exposing elements from  a page

* Before exposing elements of the page, you need to:
	* Identify locators that will be needed
	* Define the structure of the page & classes for the objects of the page

#### The example

Following example is implemented a page object test for a BMI Calulator page

1. Define and create all the page objects in a locial grouping
2. Create a new Java Class which has all the elments of the page
3. Define the classes constructor which calles `PageFactory.initEelemnts();` This method should map the elements on the page to the variables in the BmiCalcPage Class
4. Then create a test 

```
public class BmiCalcPage {

	public WebElement heightCMS;
	public WebElement weightKg;
	public WebElement Calculate;
	public WebElement bmi;
	public WebElement bmi_category
	
	public BmiCalcPage(WebDriver driver) {
		PageFactory.initElements(driver, this);
		}
	
```


```
public void BmiCalculatorTests {

@Test
public void BmiCalculatorTests {

@Test
public void testBmiCalculation() {

	WebDriver driver = new ChromeDriver();
	driver.get(...)
	BmiCalcPage bmiCalcPage = new BmiCalcPage(driver);
	
	bmiCalcPage.heightCMS.sendKeys("181");
	bmiCalcPAge.weightKg.sendKeys("80");
	
	bmiCalcPage.Calculate.click()
	
	assertEquals(somestuff)
	
	driver.close()

```

#### FindBy Annotations

* This can be used to find elements 

```
@FindBy(id = "heightCMS")
public WebElement heightField;
```

#### CacheLookUp Attribute

* If you know that the element will not change. You can find the element once then store it in a cache.
* This is good as FindBy finds the element again each time the element is used.

```
@FindBy(id = "heightCMS")
@CacheLookup
public WebElement heightField;
```

### Using the PageFactory Class for exposing an operation on a page


Example

```
       import org.openqa.selenium.WebDriver;       import org.openqa.selenium.chrome.ChromeDriver;       import org.openqa.selenium.WebElement;       import org.openqa.selenium.support.PageFactory;       public class BmiCalcPage {           private WebElement heightCMS;           private WebElement weightKg;           private WebElement Calculate;           private WebElement bmi;           private WebElement bmi_category;           private WebDriver driver;           private String url = "http://dl.dropbox.com/u/55228056/       bmicalculator.html";       //Create new instance and find elements
       public BmiCalcPage() {       driver = new ChromeDriver();       PageFactory.initElements(driver, this);}

//load the page
 public void load() {       this.driver.get(url);   }
   //close the page   public void close() {       this.driver.close();   } public void calculateBmi(String height, String weight) {       heightCMS.sendKeys(height);       weightKg.sendKeys(weight);       Calculate.click();} public String getBmi() {       return bmi.getAttribute("value");}   public String getBmiCategory() {       return bmi_category.getAttribute("value");}
       
       }

```

```
package seleniumcookbook.tests;import org.junit.Test;import static org.junit.Assert.*;import seleniumcookbook.tests.pageobjects.*;public class BmiCalculatorTests {@Test
 public void testBmiCalculation()       {           //Create an instance of Bmi Calculator Page class           //and provide the driver           BmiCalcPage bmiCalcPage = new BmiCalcPage();           //Open the Bmi Calculator Page           bmiCalcPage.load();           //Calculate the Bmi by supplying Height and Weight values           bmiCalcPage.calculateBmi("181", "80");           //Verify Bmi & Bmi Category values           assertEquals("24.4", bmiCalcPage.getBmi());           assertEquals("Normal", bmiCalcPage.getBmiCategory());           //Close the Bmi Calculator Page           bmiCalcPage.close();       }}

```

####Using the LoadableComponent Class

```
package seleniumcookbook.tests.pageobjects;       import org.openqa.selenium.WebDriver;       import org.openqa.selenium.chrome.ChromeDriver;       import org.openqa.selenium.WebElement;       import org.openqa.selenium.support.PageFactory;       import org.openqa.selenium.support.ui.LoadableComponent;       import static org.junit.Assert.*;       public class BmiCalcPage extends LoadableComponent<BmiCalcPage> {  private WebElement heightCMS;private WebElement weightKg;private WebElement Calculate;private WebElement bmi;private WebElement bmi_category;private WebDriver driver;

   private String url = "http://dl.dropbox.com/u/55228056/       bmicalculator.html";           private String title = "BMI Calculator";       public BmiCalcPage() {           driver = new ChromeDriver();           PageFactory.initElements(driver, this);} @Override       protected void load() {           this.driver.get(url);       }       @Override       protected void isLoaded()  {           assertTrue(driver.getTitle().equals(title));       }
       
```

```
import org.junit.Test;       import static org.junit.Assert.*;       import seleniumcookbook.tests.pageobjects.*;       public class BmiCalculatorTests { 154@Testpublic void testBmiCalculation(){    //Create an instance of Bmi Calculator Page class    //and provide the driver    BmiCalcPage bmiCalcPage = new BmiCalcPage();    //Open the Bmi Calculator Page bmiCalcPage.get();    //Calculate the Bmi by supplying Height and Weight values    bmiCalcPage.calculateBmi("181", "80");
    
    //Verify Bmi & Bmi Category values               assertEquals("24.4", bmiCalcPage.getBmi());               assertEquals("Normal", bmiCalcPage.getBmiCategory());               //Close the Bmi Calculator Page               bmiCalcPage.close();           }}
```

#### Implemented Nested Page Object Intances

1. Create a borwse rclass - This wil rpovide static and shared WebDriver instance for all pages
2. Create HomePage class. This will allow naviagtion on the home page
3. Create search class. This provides all pageObjectModel objects for searching
4. Create SearchResult class, which is nested in the search class. This represents result page
5. create a suitable test

```
  import org.openqa.selenium.WebDriver;       import org.openqa.selenium.chrome.*;       public class Browser {            private static WebDriver driver = new ChromeDriver();            public static WebDriver driver() {                return driver;}            public static void open(String url) {                driver.get(url);}            public static void close() {               driver.close();} }
```

```
   import org.openqa.selenium.support.PageFactory;   import org.openqa.selenium.support.ui.LoadableComponent;   import static org.junit.Assert.*;   public class HomePage extends LoadableComponent<HomePage> {       static String url = "http://demo.magentocommerce.com/";       private static String title = "Home page - Magento Commerce   Demo Store";       public HomePage() {           PageFactory.initElements(Browser.driver(), this);}       @Override       public void load() {           Browser.open(url);       }       @Override       public void isLoaded() {           assertTrue(Browser.driver().getTitle().equals(title));       }       public void close() {           Browser.close();}       public Search Search() {           Search search = new Search();           return search;} }
```

```
import org.openqa.selenium.support.FindBy;       import org.openqa.selenium.support.PageFactory;       public class Search {           private WebElement search;           @FindBy(css = "button.button")           private WebElement searchButton;           public Search() {               PageFactory.initElements(Browser.driver(), this);}           public SearchResults searchInStore(String query) {               search.sendKeys(query);               searchButton.click();               return new SearchResults(query);} }
```

```
package demo.magentocommerce.pages;       import java.util.ArrayList;       import java.util.List;       import org.openqa.selenium.By;       import org.openqa.selenium.WebElement;       import org.openqa.selenium.support.PageFactory;       import org.openqa.selenium.support.ui.LoadableComponent;       import static org.junit.Assert.assertTrue;       public class SearchResults extends LoadableComponent<SearchResul       ts> { 158private String query;public SearchResults(String query){    PageFactory.initElements(Browser.driver(),this);
    }@Overridepublic void isLoaded() {           assertTrue(Browser.driver().getTitle().equals("Search   results for: '" + this.query                   + "' - Magento1 Commerce Demo Store"));}       @Override       protected void load() {           // TODO Auto-generated method stub       }       public List<String> getProducts() {           List<String> products = new ArrayList<String>();           List<WebElement> productList = Browser.driver().   findElements(By.cssSelector("ul.products-grid > li"));           for(WebElement item : productList)               products.add(item.findElement(By.cssSelector("h2 >   a")).getText());           return products;       }       public void close() {           Browser.close();}       public Search Search() {              Search search = new Search();              return search;} }
    
 ```
 
 ```
 import org.junit.Test;import static org.junit.Assert.*;import demo.magentocommerce.pages.*;
public class SearchTest {           @Test           public void testProductSearch()           {               //Create an instance of Home page               HomePage homePage = new HomePage();               //Navigate to the Home page               homePage.get();               //Search for 'sony', the searchInStore method will return               //SearchResults class               SearchResults searchResult = homePage.Search().       searchInStore("sony");               //Verify there are 2 products available with this search               assertEquals(2, searchResult.getProducts().size());               assertTrue(searchResult.getProducts().contains("Sony       Ericsson W810i"));               //Close the Search result page               searchResult.close();           }}


```

## Extending Selenium


###Creating an Extension Class for Web Tables

* Currently there is no build in support for web tables or table elements 

Example

* Create a consutrcotr and create setter and getters
```
import org.openqa.selenium.WebElement;       import org.openqa.selenium.By;       import java.util.List;       public class WebTable {         private WebElement _webTable;         public WebTable(WebElement webTable)         {           set_webTable(webTable);         }         public WebElement get_webTable() {           return _webTable;}         public void set_webTable(WebElement _webTable) {           this._webTable = _webTable;} }```

* Add methods to get the rows and collumns of a table

```
  public int getRowCount() {         List<WebElement> tableRows = _webTable.findElements(By.   tagName("tr"));         return tableRows.size();}   public int getColumnCount() {       List<WebElement> tableRows = _webTable.findElements(By.       tagName("tr"));       WebElement headerRow = tableRows.get(0);       List<WebElement> tableCols = headerRow.findElements(By.       tagName("td"));       return tableCols.size();}
```
* Add a method to retrieve data from a specific cell

```
public WebElement getCellEditor(int rowIdx, int colIdx, int   editorIdx) throws NoSuchElementException {try {       List<WebElement> tableRows = _webTable.findElements(By.       tagName("tr"));       WebElement currentRow = tableRows.get(rowIdx-1);       List<WebElement> tableCols = currentRow.findElements(By.       tagName("td"));       WebElement cell = tableCols.get(colIdx-1);       WebElement cellEditor = cell.findElements(By.       tagName("input")).get(editorIdx);       return cellEditor;     } catch (NoSuchElementException e) {       throw new NoSuchElementException("Failed to get cell editor");} }
```

* Create method to retrieve the cell editor element. 

```
 public WebElement getCellEditor(int rowIdx, int colIdx, int   editorIdx) { 2. Now add methods to retrieve rows and columns from a table, as shown in following code:List<WebElement> tableRows = _webTable.findElements(By.tagName("tr"));WebElement currentRow = tableRows.get(rowIdx-1);

   List<WebElement> tableCols = currentRow.findElements(By.         tagName("td"));         WebElement cell = tableCols.get(colIdx-1);         WebElement cellEditor = cell.findElements(By.tagName("input")).       get(0);         return cellEditor;}

```

* create a test to test it out

```
import org.openqa.selenium.WebDriver;       import org.openqa.selenium.firefox.FirefoxDriver;       import org.openqa.selenium.WebElement;       import org.openqa.selenium.By;       import static org.junit.Assert.*;       import org.junit.After;       import org.junit.Before;       import org.junit.Test;       public class WebTableTests {         private WebDriver driver;         private StringBuffer verificationErrors = new StringBuffer();         @Before         public void setUp() {           // Create a new instance of the Firefox driver           driver = new FirefoxDriver();           driver.get("http://dl.dropbox.com/u/55228056/Locators.html");}         @Test         public void testWebTableTests() {try {             //Get the table element as WebTable instance using CSS             //Selector             WebTable table = new WebTable(driver.findElement(By.             cssSelector("div.cart-info table")));             //Verify that it has three rows             assertEquals(3,table.getRowCount());             //Verify that it has six columns             assertEquals(5,table.getColumnCount());
                 //Verify that specified value exists in second cell of    //third row    assertEquals("iPhone",table.getCellData(3,1));    //Get in cell editor and enter some value    WebElement cellEdit = table.getCellEditor(3,3,0);    cellEdit.clear();    cellEdit.sendKeys("2");  } catch (Error e) {    //Capture and append Exceptions/Errors    verificationErrors.append(e.toString());} }@Afterpublic void tearDown() {  //Close the browser  driver.quit();  String verificationErrorString = verificationErrors.  toString();  if (!"".equals(verificationErrorString)) {    fail(verificationErrorString);  } } }
```

### Setting Attribute Values

```   import org.openqa.selenium.JavascriptExecutor;   import org.openqa.selenium.WebElement;   import org.openqa.selenium.internal.WrapsDriver;   public class WebElementExtender {      public static void setAttribute(WebElement element, String      attributeName, String value)      {          WrapsDriver wrappedElement = (WrapsDriver) element;          JavascriptExecutor driver = (JavascriptExecutor)          wrappedElement.getWrappedDriver();          driver.executeScript("arguments[0].setAttribute(arguments[1],          arguments[2])", element, attributeName, value);} }

```

### Highlighting Elements

```
import org.openqa.selenium.JavascriptExecutor;   import org.openqa.selenium.WebElement;   import org.openqa.selenium.internal.WrapsDriver;   public class WebElementExtender {      public static void highlightElement(WebElement element) {         for (int i = 0; i < 5; i++) {           WrapsDriver wrappedElement = (WrapsDriver) element;           JavascriptExecutor driver = (JavascriptExecutor)           wrappedElement.getWrappedDriver();           driver.executeScript("arguments[0].setAttribute('style',           arguments[1]);",                     element, "color: green; border: 2px solid yellow;");           driver.executeScript("arguments[0].setAttribute('style',           arguments[1]);",
           element, "");
           }
           }
           }

```

* Using the JSExecutor, we can set the style to a different color (This will help us greatly when debugging)

### Capturing Screenshots of element sin the Selenium WebDriver

* TakeScreenshot interface captures screenshots of the entire page.

```
ublic static File captureElementBitmap(WebElement element) throws   Exception {
   
   WrapsDriver= wrapsDriver = (WrapsDriver) element;
   
   //Get the entire Screenshot from the driver of passed WebElement     File screen = ((TakesScreenshot)  wrapsDriver.getWrappedDriver()).     getScreenshotAs(OutputType.FILE);     //Create an instance of Buffered Image from captured screenshot     BufferedImage img = ImageIO.read(screen);     // Get the Width and Height of the WebElement using     int width = element.getSize().getWidth();     int height = element.getSize().getHeight();     //Create a rectangle using Width and Height     Rectangle rect = new Rectangle(width, height);     //Get the Location of WebElement in a Point.     //This will provide X & Y co-ordinates of the WebElement     Point p = element.getLocation();     //Create image by for element using its location and size.     //This will give image data specific to the WebElement     BufferedImage dest = img.getSubimage(p.getX(), p.getY(), rect.width,     rect.height);     //Write back the image data for element in File object     ImageIO.write(dest, "png", screen);     //Return the File object containing image data     return screen;   }
```

* YOu can then call WebElementExtender.CaptureElementBItmap(Element, filelocation);


### Comparing Elements in Selenum

* Selenium does not have features for comparing images. We have to make this ourself

```
import java.awt.Image;   import java.awt.Toolkit;   import java.awt.image.PixelGrabber;   public class CompareUtil {     public enum Result { Matched, SizeMismatch, PixelMismatch };     static Result CompareImage(String baseFile, String actualFile) {       Result compareResult = Result.PixelMismatch;       Image baseImage = Toolkit.getDefaultToolkit().getImage(baseFile);       Image actualImage = Toolkit.getDefaultToolkit().       getImage(actualFile);       try {           PixelGrabber baseImageGrab = new PixelGrabber(baseImage, 0, 0,           -1, -1, false);           PixelGrabber actualImageGrab = new PixelGrabber(actualImage,           0, 0, -1, -1, false);           int[] baseImageData = null;           int[] actualImageData = null;           if(baseImageGrab.grabPixels()) {             int width = baseImageGrab.getWidth();             int height = baseImageGrab.getHeight();             baseImageData = new int[width * height];             baseImageData = (int[])baseImageGrab.getPixels();}           if(actualImageGrab.grabPixels()) {             int width = actualImageGrab.getWidth();             int height = actualImageGrab.getHeight();             actualImageData = new int[width * height];             actualImageData = (int[])actualImageGrab.getPixels();}           System.out.println(baseImageGrab.getHeight() +  "<>" +           actualImageGrab.getHeight());
           
           System.out.println(baseImageGrab.getWidth() +  "<>" +           actualImageGrab.getWidth());           if ((baseImageGrab.getHeight() != actualImageGrab.getHeight())           || (baseImageGrab.getWidth() != actualImageGrab.getWidth()))             compareResult = Result.SizeMismatch;           else if(java.util.Arrays.equals(baseImageData,           actualImageData))             compareResult = Result.Matched;       } catch (Exception e) {         e.printStackTrace();}       return compareResult;     }}

```

* The above class uses PixelGrabber to compare pixels from each image (It puts them in an array and compares them that way
* They are testing firstly for size missmatch, then pixel mismatch

Example test:

```
   import org.openqa.selenium.firefox.FirefoxDriver;   import org.openqa.selenium.*;   import org.apache.commons.io.FileUtils;   import org.junit.*;   import static org.junit.Assert.*;   import java.io.File;   public class BmiCalculatorTest {     public WebDriver driver;     private StringBuffer verificationErrors = new StringBuffer();     @Before     public void setUp() throws Exception {       // Create a new instance of the Firefox driver       driver = new FirefoxDriver();     }     @Test     public void testBmiCalculatorLayout() throws Exception {       String scrFile = "c:\\screenshot.png";       String baseScrFile = "c:\\baseScreenshot.png";       //Open the BMI Calculator Page and get a Screen Shot of Page into       a File       driver.get("http://dl.dropbox.com/u/55228056/bmicalculator.html");
       File screenshotFile = ((TakesScreenshot) driver).getScreenshotAs(OutputType.FILE);
       
       FileUtils.copyFile(screenshotFile, new File(scrFile));       try {         //Verify baseline image with actual image         assertEquals(CompareUtil.Result.Matched,         CompareUtil.CompareImage(baseScrFile,scrFile));       } catch (Error e) {         //Capture and append Exceptions/Errors         verificationErrors.append(e.toString());       }}     @After     public void tearDown() throws Exception {       //Close the browser       driver.quit();       String verificationErrorString = verificationErrors.toString();       if (!"".equals(verificationErrorString)) {         fail(verificationErrorString);       }} }
```

## Testing On MObile Browsers

TODO


## Client-side Performance Testing


### Measuring The Response Time using a timer

* This can be implemented using Date/Time Classes 

Example
```
// Get the Start Time   long startTime = System.currentTimeMillis();   // Open the BMI Calculator Mobile Application   driver.get("http://dl.dropbox.com/u/55228056/bmicalculator.html");   // Wait for the Calculate Button   new WebDriverWait(driver, 10).until(ExpectedConditions.   presenceOfElementLocated(By.id("Calculate")));   // Get the End Time   long endTime = System.currentTimeMillis();   // Measure total time   long totalTime = endTime - startTime;   System.out.println("Total Page Load Time: " + totalTime + "   milliseconds");
```

### Using the BrowserMob proxy for measuring perormance

* Captures performance data from a web application using HTML Archive (HAR) formzt
* Can also manipulate brwoser behaviour and trafic

Steps:

* Launch the browerMob Proxy server
```
ProxyServer server = new ProxyServer(9090);
server.start()
```
* Create an object of SeleniumProxy and DesiredCapabilities

```
Proxy proxy = server.seleniumProxy();

DesiredCapabilties capabilities = new DesiredCapabilities();
capabilities.setCapability(CapabilityType.PROXY, proxy);
```
* Create and launch a browser instance with the proxy

```
WebDriver driver = new FirefoxDriver(capabilities);
```
* Create a new HAR file and navigate to the url

```
server.newHar("bmiCalculator");
```
* Implement the test steps
```
// Open the BMI Calculator Application       driver.get("http://dl.dropbox.com/u/55228056/bmicalculator.html");       WebElement height = driver.findElement(By.name("heightCMS"));       height.sendKeys("181");       WebElement weight = driver.findElement(By.name("weightKg"));
       weight.sendKeys("80");       WebElement calculateButton = driver.findElement(By.       id("Calculate"));       calculateButton.click();       Thread.sleep(5000);
```

* Collect the performance data from the proxy

```
// Get the HAR data       Har har = server.getHar();       // Write the HAR Data in a File       File harFile = new File("C:\\bmiCalculator.har");       har.writeTo(harFile);       // Stop the BrowserMob Proxy Server       server.stop();       // Close the browser       driver.quit();
```

## Testing HTML5 Web Applications



