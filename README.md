# Jon Connor - Based in Dublin.<br><br>Software Tester - Manual and Automation 
Welcome to my GitHub page!

Here, you’ll find a collection of automation frameworks and various other projects I’ve created. I believe in learning by doing, so whenever I pick up a new skill or concept, I build practical examples to deepen my understanding and share my journey with others.

Feel free to connect with me on <a href="https://www.linkedin.com/in/jonconnordublin/" target="_blank">LinkedIn</a> or drop me an <a href="mailto:jonconnor@live.ie" target="_blank">Email</a> for a chat about any projects or roles you have coming up. I’m always open to discussing new opportunities and ideas!

# Table of Contents

**[Cucumber Frameworks with Java/Selenium](#CucumberFrameworks)**
   * [Shopping](#Shopping)
   * [Donuts](#Donuts)

**[Page Object Model with Java/Selenium/TestNG](#pom)**
  * [POM Donuts](#pomdonuts)

**[Robot Framework with Browser library (playwright)](#Robot_Donuts)**
  * [Robot Donuts](#RobotDonuts)

**[Other Content I have created](#other)**
  * [My Understanding of BDD](#bdd)
  * [Bug Reports](#Bugs)
  * [Grades](#grades)
  * [About Me](#aboutme)

**[Whats Next?](#What)**

__________________________________

# Cucumber Frameworks with Java/Selenium <a name="CucumberFrameworks"></a>
To help practice writing Cucumber features as well as getting more familiar with the Gherkin syntax and how it integrates with Java I created two frameworks that 'test' existing commercial websites

## <a name="Shopping" href="https://github.com/JonConnorATI/ShopMandM" target="_blank">Shopping</a>
This framework 'tests' the clothes shopping website, <a href="https://www.mandmdirect.ie/" target="_blank">M and M direct</a>[^1]
### Features
<ul>
    <li>Login Feature</li>
        <ul>
            <li>Basic test to verify only valid combination of username and password can successfully log in. Uses the Gherkin 'Scenario Outline' and 'Examples' syntax</li>
        </ul>
    <li>Account Page Feature</li>
        <ul>
            <li>Visits each section and makes changes to verify edits can be made</li>
        </ul>
    <li>Change Password Feature</li>
        <ul>
            <li>Changes the password then logs in with the new password and changes it back to the original value</li>
        </ul>
    <li>Find the cheapest Jeans Feature</li>
        <ul>
            <li>Searches for a pair of jeans with given parameters of size and fit, sorts the results by lowest price and confirms the cheapest are first in the list</li>
        </ul>    
    <li>Cart Cache Feature</li>
        <ul>
            <li>User logs in and selects an item to add to cart, then logs out. User logs in again and verifies the cart still has the previously added item</li>
        </ul>
</ul>

### Reports
I was able to link my test executions on my laptop to the cucumber cloud by storing an Environment token from Cucumber in my IDE's output settings.
View the latest run on the cucumber cloud, <a href="https://reports.cucumber.io/reports/18ca5276-2cd9-4b9c-9a25-a6ccedbd5375" target="_blank">here.</a>


I figured out how to create a yaml file for github actions but unfortunately this was sometime after I'd created this repositry. When I tried to schedule a regular execution of the tests using github actions I found that the tests would not work in headless mode, and that this was probably down to security/configuration settings on the website. It wasn't possible for me to schedule regular executions in the cloud. So I created the repository below.
   
## Donuts <a name="Donuts"></a> <a href="https://github.com/JonConnorATI/Donuts" target="_blank">(Link to github repo)</a>
This framework 'tests' the Irish donut bakers, <a href="https://offbeatdonuts.com/" target="_blank">offBeatDonuts</a>[^2]
### Features
<ul>
    <li>Order Now Feature</li>
        <ul>
            <li>This feature has three scenarios. Each scenario adds more items and verifies the items added are included in the shopping cart</li>
                <ul>
                    <li>Economy, just adds the cheapest donuts </li>
                    <li>Hungry, selects 12 different types of donuts</li>
                    <li>Luxury, adds 2 dozen donuts, candles, card with messages and bows</li>
                </ul>
        </ul>        
</ul>

### Reports
I created a yaml file in github actions that is set to kick off the test execution in the cloud. I added a Secret in the repository to store the cucumber token, so the executions via github actions are also published in the Cucumber cloud.
View the latest run <a href="https://reports.cucumber.io/reports/ae8d4eea-eaf4-47c6-bc0d-8a053db4d051" target="_blank">here</a>

_______________


# Page Object Model with Java/Selenium/TestNG <a name="pom"></a>
I decided to convert the Cucumber framework Donuts into a page object model which runs the tests using TestNG, to get familiar with this popular framework method.

## POM Donuts <a name="pomdonuts"></a> <a href="https://github.com/JonConnorATI/donutsPageObjectModel" target="_blank">(Link to github repo)</a>
The Cucumber Donuts framework was converted to work with Page Object/TestNG:
<ul>
  <li>created a java file with the test steps. See <a href="https://github.com/JonConnorATI/donutsPageObjectModel/blob/main/src/test/java/tests/OrderNowDonutsTests.java" target="_blank">here</a></li>
  <li>created a testNG xml file. See <a href="https://github.com/JonConnorATI/donutsPageObjectModel/blob/main/testng.xml" target="_blank">here</a></li>
</ul>

The testng xml file instructs the framework which test files to select and which tests in those files to run.


The framework is not easily understood by somebody unfamiliar with code or no knowledge of the business domain because the non technical layer, Cucumber, is not present. So its important to cretae method names in the tests that are a descriptive as possible eg ```HomePage.acceptCookies();``` 
 so it is easier to understand what the step of code is doing in the website.

 
The advantage of using TestNG Framework vs Cucumber Framework is there is one less layer to create and maintain but the trade off is non-technical members of the team may not be able to follow it.

### Reports
I created a yaml file in github actions that is set to kick off the test execution in the cloud. When the run has completed a surefire zip report can be downloaded from the Artifacts section. When downloaded and unzipped, the following reports are available:
-  emailable-report
-  index
-  suite/test

They all display the same information in slightly different formats.

You can View the latest run <a href="https://github.com/JonConnorATI/donutsPageObjectModel/actions/runs/13041287156" target="_blank">here</a> and access the zip file from the artifacts section.


______________________________

# Robot Framework with Browser Library (playwright) <a name="Robot_Donuts"></a>
After being introduced to Robot Framework by a colleague, I decided to transition the Cucumber framework into a Robot Framework so I could learn more about it.

The <a href="https://robotframework-browser.org/" target="_blank">Browser library</a> is powered by playwright. 

## Robot Donuts <a name="RobotDonuts"></a> <a href="https://github.com/JonConnorATI/RobotDonuts" target="_blank">(Link to github repo)</a>
The Cucumber Donuts framework was converted to work with Robot Framework
### Keyword Driven
Robot framework is Keyword driven, similiar to Cucumber, but not restricted to just using `Given` `When` `Then`. It describes it self as **ATDD** (*Acceptance Test Driven Development*) while Cucumber is **BDD** (*Business Driven Development*)

The test cases are very readable, all the steps are in plain language and map to a `*.resource` file where the code to interact with the application under test is stored. The code and the test steps are seperated.

### Reports
I created a yaml file in github actions that is set to kick off the test execution in the cloud. A report is exported to the instance of the workflow run and can be downloaded from the Artifacts section in the github actions page.
View the latest run <a href="https://github.com/JonConnorATI/RobotDonuts/actions/runs/11809353226" target="_blank">here</a>

__________________________________

# Other content that I have created <a name="other"></a>

## My Understanding of BDD <a name="bdd"></a>

Some web content I created to highlight my skills and what I know about BDD

- <a href="https://jonconnorati.github.io/JonConnorSWTester/bdd.html" target="_blank">BDD</a> which includes:
  - Cucumber
  - Automation

## Bug Reports <a name="Bugs"></a>
A web page I created after an interview because the question threw me for a second and I realised how much I take for granted when creating a bug in Jira, so it is a reminder of the information for a good bug report and why we need it.

- <a href="https://jonconnorati.github.io/JonConnorSWTester/bugreport.html" target="_blank">Bug Reports</a>

## Grades <a name="grades"></a>
Created a simple input/output web page that grades a score using some simple javascript. I created it for the <a href="https://jonconnorati.github.io/JonConnorSWTester/automation.html" target="_blank">Automation</a> section in <a href="https://jonconnorati.github.io/JonConnorSWTester/bdd.html" target="_blank">BDD</a> to video a demo run of a cucumber test.

- <a href ="https://jonconnorati.github.io/JonConnorSWTester/Grades.html" target="_blank">Grades</a>

## About Me <a name="aboutme"></a>

Created this page to highlight my skills and explain a little bit more about myself, includes my CV.

- <a href="https://jonconnorati.github.io/JonConnorSWTester/" target="_blank">About Me</a>

________________________________________________

# Whats next? <a name="What"></a>
 - More to come, I'm currently looking at working with API's and restAssured. Check back soon

______________________________________________________




##### FOOTNOTES
[^1]: I did not have any involvement with the actual testing or development of the M and M website
[^2]: I did not have any involvement with the actual testing or development of the OffBeatDonuts website
<!--
[Bug Reports](#Bugs)
  * [Grades](#grades)
  * [About Me](#aboutme)

     <li>Two Cucumber test frameworks: <a href="https://github.com/JonConnorATI/ShopMandM" target="_blank">Shopping</a>, and <a href="https://github.com/JonConnorATI/Donuts" target="_blank">Donuts</a>. Created the frameworks to 'test' these active commercial websites, <a href="https://www.mandmdirect.ie/" target="_blank">M and M direct</a> and <a href="https://offbeatdonuts.com/" target="_blank">offBeatDonuts</a>, which includes a method to use Chrome, Edge or Firefox browsers. As I've updated the frameworks to use WebDriver Manager, there's no need to download the webdrivers for the browsers. View the latest runs in these cucumber reports <a href="https://reports.cucumber.io/reports/18ca5276-2cd9-4b9c-9a25-a6ccedbd5375" target="_blank">Shopping</a> and .</li>
    <li>I've replicated the Donuts Cucumber framework as a java TestNG framework using the page object model - <a href="https://github.com/JonConnorATI/donutsPageObjectModel" target="_blank">POM Donuts</a>. Again this framework uses WebDriver Manager, so no webdrivers are needed.</li>
    <li>This is a Robot Framework version of the same tests but written using the built in Browser (playwright) library. Check it out, <a href="https://github.com/JonConnorATI/RobotDonuts" target="_blank">Robot Donuts</a>. </li>
    <li>Some web content I created to highlight my skills and what I know about cucumber - <a href="https://jonconnorati.github.io/JonConnorSWTester/" target="_blank">About Me</a> includes <a href="https://jonconnorati.github.io/JonConnorSWTester/bdd.html" target="_blank">BDD/Cucumber/Automation</a></li>
    <li>A web page I created to test a simple input/output rule - <a href ="https://jonconnorati.github.io/JonConnorSWTester/Grades.html" target="_blank">Grades</a> - Takes an input and grades it. Used in the <a href="https://jonconnorati.github.io/JonConnorSWTester/automation.html" target="_blank">Automation</a> section of <a href="https://jonconnorati.github.io/JonConnorSWTester/" target="_blank">About Me</a> to show and explain how cucumber works.</li>
    <li>A web page I created after an interview because the question threw me for a second and I realised how much I take for granted - <a href="https://jonconnorati.github.io/JonConnorSWTester/bugreport.html" target="_blank">Bug Reports</a> - a reminder of the information for a good bug report and why we need it.</li>
    <!--<li>A web page I created - <a href="https://jonconnorati.github.io/Membership-ChristmasCountdown/" target="_blank">Christmas Countdown</a> - a chrsitmas countdown for a friend who loves Christmas.</li>
    <li>More to come, I'm currently looking at working with API's and restAssured. Check back soon</li>
</ul> -->
<!---
JonConnorATI/JonConnorATI is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
