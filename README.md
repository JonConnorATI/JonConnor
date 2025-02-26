# Based in Dublin.<br><br>Software Tester - Manual and Automation 
Welcome to my GitHub page!

Here, you’ll find a collection of automation frameworks and various other projects I’ve created. I believe in learning by doing, so whenever I pick up a new skill or concept, I build practical examples to deepen my understanding and share my journey with others.

Feel free to connect with me on <a href="https://www.linkedin.com/in/jonconnordublin/" target="_blank">LinkedIn</a> or drop me an <a href="mailto:jonconnor@live.ie" target="_blank">Email</a> for a chat about any projects or roles you have coming up. I’m always open to discussing new opportunities and ideas!

# Table of Contents

**[1. Cucumber Frameworks with Java/Selenium](#CucumberFrameworks)**
   
   * [<b>Shopping Framework</b>](#Shopping)
     * [Features](#Features)
       * [LogIn](#LogIn)
       * [Account Page](#AccountPage)
       * [Change Password](#ChangePassword)
       * [Find Cheapest Jeans](#FindJeans)
       * [Cart Cache](#Cart)
     * [Reports](#Reports)
  
   * [<b>Donuts Framework</b>](#Donuts)
     * [Feature](#Dfeatures)
       * [Order Now Scenarios](#OrderNow)
         * [Economy](#Donuts_Economy)
         * [Hungry](#Donuts_Hungry)
         * [Luxury](#Donuts_Luxury)
     * [Reports](#Donuts_reports)
       
       
**[2. Page Object Model with Java/Selenium/TestNG](#pom)**

  * [<b>POM Donuts<b>](#pomdonuts)
     * [Test NG](#TestNG)
     * [Test Suite](#TestSuite)
         * [Economy](#PomDonuts_Economy)
         * [Hungry](#PomDonuts_Hungry)
         * [Luxury](#PomDonuts_Luxury)
     * [Reports](#PomDonuts_reports)
   
**[3. Robot Framework with Browser library (playwright)](#Robot_Donuts)**

  * [Robot Donuts](#RobotDonuts)
    * [Keyword Driven](#keyword-driven)
    * [Test Cases](#RobotTestCases)
      * [Economy](#Robot_Economy)
      * [Hungry](#Robot_Hungry)
      * [Luxury](#Robot_Luxury)
    * [Reports](#Robot_reports) 

**[4. Other Content I have created](#other)**

  * [My Understanding of BDD](#bdd)
  * [Bug Reports](#Bugs)
  * [Grades](#grades)
  * [About Me](#aboutme)

**[5. Whats Next?](#What)**

______________________________________________________________________________________

# 1. Cucumber Frameworks with Java/Selenium <a name="CucumberFrameworks"></a>
To help practice writing Cucumber features as well as getting more familiar with the Gherkin syntax and how it integrates with Java I created two frameworks that 'test' existing commercial websites

## Shopping<a name="Shopping"></a> <a href="https://github.com/JonConnorATI/ShopMandM" target="_blank">(Link to github repo)</a>
This framework 'tests' the clothes shopping website, <a href="https://www.mandmdirect.ie/" target="_blank">M and M direct</a>[^1]
### Features <a id="Features"></a>

- Login Feature <a id="LogIn"></a>
  - Basic test to verify only valid combination of username and password can successfully log in. Uses the Gherkin 'Scenario Outline' and 'Examples' syntax.

![Log in cucumber feature file](/assets/images/loginfeature.png)
    
- Account Page Feature <a id="AccountPage"></a>
  - Visits each section and makes changes to verify edits can be made.

 ![Log in cucumber feature file](/assets/images/accpagefeature.png)

- Change Password Feature <a id="ChangePassword"></a>
  - Changes the password then logs in with the new password and changes it back to the original value.

![Change password feature](/assets/images/changepasswordfeature.png)

- Find the Cheapest Jeans Feature <a id="FindJeans"></a>
  - Searches for a pair of jeans with given parameters of size and fit, sorts the results by lowest price and confirms the cheapest are first in the list.

![Cheapest Jeans Feature](/assets/images/cheapestjeansfeature.png)

- Cart Cache Feature <a id="Cart"></a>
  - User logs in and selects an item to add to cart, then logs out. User logs in again and verifies the cart still has the previously added item.

![Cart Cache Feature](/assets/images/cartcachefeature.png)

### Reports <a id="Reports"></a>
I was able to link my test executions on my laptop to the cucumber cloud by storing an Environment token from Cucumber in my IDE's output settings.
View the latest run on the cucumber cloud, <a href="https://reports.cucumber.io/reports/23233055-651b-4f2a-9e2d-882235290cbc" target="_blank">here.</a>

I figured out how to create a yaml file for github actions but unfortunately this was sometime after I'd created this repositry. When I tried to schedule a regular execution of the tests using github actions I found that the tests would not work in headless mode, and that this was probably down to security/configuration settings on the website. It wasn't possible for me to schedule regular executions in the cloud. So I created the repository below.
   
## Donuts <a name="Donuts"></a> <a href="https://github.com/JonConnorATI/Donuts" target="_blank">(Link to github repo)</a>
This framework 'tests' the Irish donut bakers, <a href="https://offbeatdonuts.com/" target="_blank">offBeatDonuts</a>[^2]
### Features <a id="Dfeatures"></a>

- Order Now Feature <a id="OrderNow"></a>

![order now feature](/assets/images/ordernowfeature.png)

  - This feature has three scenarios. Each scenario adds more items and verifies the items added are included in the shopping cart

    - Economy Just add the cheapest donuts <a id="Donuts_Economy"></a>

    ![Economy Donuts feature](/assets/images/economydonutsfeature.png)

      - Hungry, selects 12 different types of donuts <a id="Donuts_Hungry"></a>

    ![Hungry Donuts feature](/assets/images/hungrydonutsfeature.png)

      - Luxury, adds 2 dozen donuts, candles, card with messages and bows <a id="Donuts_Luxury"></a>
    
    ![Luxury Donuts feature](/assets/images/luxurydonutsfeature.png)


### Reports <a id="Donuts_reports"></a>
I created a yaml file in github actions that is set to kick off the test execution in the cloud. I added a Secret in the repository to store the cucumber token, so the executions via github actions are also published in the Cucumber cloud.
View the latest run <a href="https://reports.cucumber.io/reports/ae8d4eea-eaf4-47c6-bc0d-8a053db4d051" target="_blank">here</a>

_______________


# 2. Page Object Model with Java/Selenium/TestNG <a name="pom"></a>
I decided to convert the Cucumber framework Donuts into a page object model which runs the tests using TestNG, to get familiar with this popular framework method.

## POM Donuts <a name="pomdonuts"></a> <a href="https://github.com/JonConnorATI/donutsPageObjectModel" target="_blank">(Link to github repo)</a>
The Cucumber Donuts framework was converted to work with Page Object/TestNG:

- Test NG <a id="TestNG"></a>
  - A testNG xml file was created.
  
    ![Test NG XML FILE](/assets/images/POMtestNGxml.png)
    
- Test Suite <a id="TestSuite"></a>
  - A java file with the test cases and Test steps.
    
    ![Order Now Donut Tests](/assets/images/pom_test_suite.png)
    
    - Economy <a id="PomDonuts_Economy"></a> Test Case
    
      ![Economy Test Steps](/assets/images/pom_Economy.png)
      
    - Hungry <a id="PomDonuts_Hungry"></a> Test Case
    
      ![Hungry Test Steps](/assets/images/pomHungry.png)
      
    - Luxury <a id="PomDonuts_Luxury"></a> Test Case
    
      ![Luxury Test Steps](/assets/images/pomLuxury.png)


    

The testng xml file instructs the framework which test files to select and which test cases in those files to run.

The framework is not easily understood by somebody unfamiliar with code or no knowledge of the business domain because the non technical layer, Cucumber, is not present. So its important to cretae method names in the tests that are a descriptive as possible eg ```HomePage.acceptCookies();``` 
 so it is easier to understand what the step of code is doing in the website.

 
The advantage of using TestNG Framework vs Cucumber Framework is there is one less layer to create and maintain but the trade off is non-technical members of the team may not be able to follow it.

### Reports <a id="PomDonuts_reports"></a>
I created a yaml file in github actions that is set to kick off the test execution in the cloud. When the run has completed a surefire zip report can be downloaded from the Artifacts section. When downloaded and unzipped, the following reports are available:
-  emailable-report
    
      ![email report](/assets/images/report2.png)
   
-  index-report
    
      ![Index report](/assets/images/report1.png)
   
-  suite/test-report
    
      ![suite/test report](/assets/images/report3.png)
   
They all display the same information in slightly different formats.

You can View the latest run <a href="https://github.com/JonConnorATI/donutsPageObjectModel/actions/runs/13041287156" target="_blank">here</a> and access the zip file from the artifacts section.


______________________________

# 3. Robot Framework with Browser Library (playwright) <a name="Robot_Donuts"></a>
After being introduced to Robot Framework by a colleague, I decided to transition the Cucumber framework into a Robot Framework so I could learn more about it.

The <a href="https://robotframework-browser.org/" target="_blank">Browser library</a> is powered by playwright. 

## Robot Donuts <a name="RobotDonuts"></a> <a href="https://github.com/JonConnorATI/RobotDonuts" target="_blank">(Link to github repo)</a>
The Cucumber Donuts framework was converted to work with Robot Framework
### Keyword Driven <a id="keyword_driven"></a>
Robot framework is Keyword driven, similiar to Cucumber, but not restricted to just using `Given` `When` `Then`. It describes it self as **ATDD** (*Acceptance Test Driven Development*) while Cucumber is **BDD** (*Business Driven Development*)

## Test Cases <a id="RobotTestCases"></a>

* Economy Test Case<a id="Robot_Economy"></a>

  ![Economy Test Case](/assets/images/robotEconomy.png)

* Hungry Test Case <a id="Robot_Hungry"></a>

  ![Hungry Test Case](/assets/images/robotHungry.png)

* Luxury Test Case <a id="Robot_Luxury"></a>

  ![Luxury Test Case](/assets/images/robotLuxury.png)

The test cases are very readable, all the steps are in plain language and map to a `*.resource` file where the code to interact with the application under test is stored. The code and the test steps are seperated.

### Reports <a id="Robot_reports"></a>
I created a yaml file in github actions that is set to kick off the test execution in the cloud. A report is exported to the instance of the workflow run and can be downloaded from the Artifacts section in the github actions page.

View the latest github actions run <a href="https://github.com/JonConnorATI/RobotDonuts/actions/runs/11809353226" target="_blank">here</a>

The reports are excellent and have lots of useful detail. Please take a look at the reports generated for a run in Chrome and Firefox

* <a href="https://raw.githack.com/JonConnorATI/JonConnor/Jon_Edits/assets/Reports/chrome/offBeatTest-log.html" target="_blank">Chrome</a>

* <a href="https://raw.githack.com/JonConnorATI/JonConnor/Jon_Edits/assets/Reports/firefox/offBeatTest-log.html" target="_blank">Firefox</a>

You can expand and collapse the sections in the Test Execution log and discover the layers of code mapped to each keyword.

For example the ```add some candles``` keyword in the ```Customer is Hungry``` Test Case, is made up of sub keywords ```Wait For Element To Be Visible``` and ```Click```

![Report Snippet](/assets/images/reportRobot.png)

__________________________________

# 4. Other content that I have created <a name="other"></a>

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

# 5. Whats next? <a name="What"></a>
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
