
 
This past Tuesday, I reinstalled WinZip. Today I ran my weekly AdwCleaner scan (version 7.0.2.1), and it identified WinZip Smart Monitor as a PUP. Meanwhile, my MalwareBytes scan finds nothing. When I tried cleaning, using AdwCleaner, I got this message: Caught unhandled unknown exception; terminating.
 
You should be able to just delete that C:\Program Files\WinZip\WinZip Smart Monitor folder but I'd prefer to have more information as to what it installed on this machine. You said you installed WinZip last Tuesday - did you intentionally install the WinZip Smart Monitor? Where did you download WinZip from? If you look in your installed programs list, do you see separate listings for WinZip and for WinZip Smart Monitor?
 
**Download ✒ [https://quetralverti.blogspot.com/?file=2A0PlD](https://quetralverti.blogspot.com/?file=2A0PlD)**


 
Hi, Ried! Yes, I intentionally purchased and downloaded WinZip 22 (Standard Edition) from the WinZip page: -downwz\_wzd1cb?tracking=wz

Looking in my WinZip folder, I do see a separate WinZip Smart Monitor folder. So I'm assuming I should be able to delete that. I have Eraser software, so that might be a better option.
 
"Starting with WinZip 21.5, Smart Monitor is introduced to WinZip. It is being used to provide more granular control over the scheduling of the WinZip Background Tools. If you are not using these tools, you certainly can remove Smart Monitor. It will not hinder any other usage of WinZip."
 
Same thing here, with this difference... I did not install winzip last week, last month... Got the PUP-message for the first time this weekend, after my weekly scan.
Do not know when smart monitor was slipped onto my computer, but I definitely don't ilke it.

thx for the intel, got it removed.
 
This is a response from WinZip Technical Support re: Smart Monitor: "You are getting False positive warning from Malwarebytes for Smatmonitor.
The Smart Monitor handles scheduling the WinZip Background Tools ( ) to run. If you use the tools, you will want to keep Smart Monitor running." So if you don't use the tools you can delete it. But Malware bytes needs to address the false positive issue.
 
This is very interesting. I have Malwarebytes Premium 3.8.3.2965 and WinZip Pro 23.0. Although I am getting the popups to update my WinZip (just got another a minute ago), I have not done so yet. I see this thread began almost 2 years ago and the last post (before now) was a year and a half ago, so I assumed the issue had been resolved. But my Malwarebytes runs a scan every night, and last night's scan is the first time I have gotten a warning about WinZip Smart Monitor. Why it is just coming up now?
 
This thread is about ADWCleaner, not Malwarebytes, detecting Winzip Smart Monitor, so that would likely explain why up until recently Malwarebytes showed no detections on your system. If you perform a scan with ADWCleaner I bet it would likely detect it. It is usually the case that Malwarebytes and ADWCleaner detect different things from one another, though there is occasionally overlap (they use different detection techniques and separate Research teams to create their detection signatures/definitions and use somewhat different criteria for determining what they will and will not detect).
 
If you wish to see if ADWCleaner detects anything you can find it **here**. If you require assistance with checking your system for threats then please follow the instructions in **this topic** and then create a new topic on the malware removal area by **clicking here** and one of our malware removal specialists will assist you with checking and clearing your system of any remaining threats.

I still have winzip 18 and refuse to upgrade any further since I have seen nothing in the upgrades to produce more security. I thought about 7-zip but there were a lot of cautions on the info page so I decided to stick with winzip.
 
My need is to zip and unzip files and folders and sometimes create a password protected zip file and if 7-Zip can do everything that WinZip can do in that regard then I may either keep my copy of WinZip 19 or switch to 7-Zip if someone can give me a reason to do so. Since there is a 7-Zip beta though, I would like to know more about that if someone has any details. Thanks.
 
Windows does almost all the Zipping I need.
If I need to create a zip with a password I use 7-Zip.
7-Zip also creates a self extractor if you use the 7z format and it can open lots of other archive types, even ISO.
Where 7-Zip falls down is use, it is not intuitive for me and I usually have to think carefully about what I want to do.
 
Is this me or everybody is puzzled what is up with downloading 1 photo from Icloud photo, not only the download arrives in form of a .zip file, but also if you happen not to have the winzip trial you have to purchase the \*\*\*\* thing? So bothersome...
 
If you had it installed for some reason, then it would have associated the zip file type to itself which would make it open with the Winzip application and as such may require you to reset the evaluation version. However, Windows 10 has no issues with opening ZIP files on its own you do not need Winzip at all.
 
Thanks Phil, but I am running WIn 10, and had to uninstall and reinstall for Winzip to allow me to use "WINZIP Evaluation version", otherwise it requests to take action via "buy" button. Not sure if I am missing the point.
 
The job neither completes nor fails; it just stops moving forward. It will generate the dbBack.bak file and create the dbBack.zip file in the remote location, but it won't proceed past there. It seems to be behaving like it is waiting on a pop-up confirmation, but I don't see one when I log in to the console or run the zip from the command line.
 
I've tried adding -ybc flag to automatically confirm or skip any prompts, but it didn't seem to do anything. The process still didn't complete. I've even tried to > pipe output of the process, but it won't even write my log file.
 
This is a secured system and infrastructure, but I'm fairly certain I'm not being blocked by a permission. My SQL Server service account that runs the job has access to the folders it needs and it can run the winzip32.exe process. This process ran fine, but we had to upgrade WinZip this past weekend (19.5), and that's when it stopped working properly. We aren't able to roll back to the previous version (10).
 
I think I discovered the problem. It turns out, we are using the GUI version of WinZip and calling the executable from the command line. Even though we can't see the GUI, it's still there. So, the prompt to confirm our compression is still there in the program's workflow, we just can't see it and thus can't confirm it. And the confirm flags don't work with the GUI version.
 
My workaround involved logging in to my SQL server as our service account and running a WinZip operation. When it completed and gave me the Add Complete prompt, I checked Do not display this dialog in the future and clicked OK. This will suppress that prompt when the service account runs its Job.
 
If someone changes the service account, we'll have to do this again, so our ultimate solution will be to install the WinZip Commmand Line Plugin. Hopefully, when that's done, we won't have to worry about this.
 
Anytime I download a .zip file or create a compressed folder, my PC makes it a Winzip file, which is no good because I don't want to pay their fee to get the full version (the version I have was a trial one I obtained when I had this one .zip file that needed it to work).
 
Uninstall WinZip by going into "Programs and Features" (Vista / Windows 7) or "Add/Remove Programs" (XP). Unintalling WinZip should cause Windows to revert to it's native ZIP handling behavior. If the Windows ZIP handler doesn't meet your requirements, you can always install something else.
 
If you need WinZip for some specialist features, but want to use the inbuilt facilities in most case, just (for w8):- go to Control Panel- choose Programs- choose 'Make file types always open in a specific program'- scroll down for ".zip"- select 'change program' in the top right- choose 'windows explorer'
 
Windows 10: remove all winzip or any other zip programs through control panel, programs, etc.right-click on start button, settings, apps, default apps, choose default apps by file type, scroll down to .zip file type, click on it then click on "windows" as thw default app for opening .zip files
 
I then copied over the zip file to the remote server and ran unzip through there but surprisingly the unzipping took forever. My guess is that even though the files are already on the server and getting unzipped locally, that winzip doesn't realize this and is somehow using my local machine as a temp stage before unzipping to the remote directory.
 
The way you did it was that your local machine was doing the actual unzipping, just against data that was remote - what you need to do is run the unzip code on the remote server via something like RDP/VNC/SSH or similar - you need full access to the remote machine via one of these protocols first though ok.
 
GUI-based applications like PKZIP and winzip (and the GUI version of 7z/7zip) let us browse around our directories and create a compressed file that contains lots of different directories and files, complete with [partial or full] paths.
 
I can't believe I learn about this program only now, after using ubuntu for a year, reading omgubuntu.co.uk, webupd8.org etc. :) As you can see it has all one would need.
 It is installed via deb package. For me it installed without errors but I didn't get a Dash shortcut for it. Since the portable version (no installation required) works fine, I won't bother troubleshooting it. Right click > View Image for higher resolutions.
 
I do not consider File Roller a 7zip or WinZip equivalent as it has some serious limitations. For example File Rolle