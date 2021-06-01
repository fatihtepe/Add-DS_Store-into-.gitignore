# Add-DS_Store-into-.gitignore
.DS_Store Files and Why You Should Know About Them
Are you currently using a MacBook? If so, you should be cautious of .DS_Store files. You could be exposing information about your website or application that you’re not even aware of.

What is a .DS_Store file?

A .DS_Store, short for Desktop Services Store, is an invisible file on the macOS operating system that gets automatically created anytime you look into a folder with ‘Finder.’ This file will then follow the folder everywhere it goes, including when archived, like in ‘ZIP.’

If you’re a developer or system administrator and still transferring files from your computer to your server or don’t take the necessary precautions with your automated deployment process, you could be putting these files on the server where your site or application lives unconsciously.

Why should you know about them?

This file stores custom attributes/metadata of its containing folder and the names of other files around it. Exposing this information could potentially allow hackers to act maliciously and let them see private files.

Back in 2015, a .DS_Store file was exploited and used to gain access to an admin portal of the TCL Corporation, a multinational Chinese electronics company. The entire backend and database of the application were exposed to anyone that accessed the .DS_Store file.

See Bug Report (Translation needed): https://web.archive.org/web/20190105043001/https://bugs.shuimugan.com/bug/view?bug_no=91869

How to prevent this?

The people who want to prevent security breaches through .DS_Store files are developers and system administrators. Finding .DS_Store files in random folders in your server is not fun. You could be leaking information you don’t intend to. If you do find one, simply delete the file with the command  ‘rm .DS_Store’ and it will be resolved.

The easiest way to prevent this problem from happening is to completely turn off the automatic creation of these files. Follow the steps below to do so:

Press command + spacebar and search for Terminal.
Open Terminal. Then copy/paste this command and press enter:
defaults write com.apple.desktopservices DSDontWriteNetworkStores true

To reverse this if ever needed in the future, just change true to false:
defaults write com.apple.desktopservices DSDontWriteNetworkStores false

After running one of these commands, reboot your machine.
You’re set up & secure!
For developers, you can use Git to solve this problem by doing the following:

Place .DS_Store in your .gitignore file. That way, any .DS_Store file will be ignored and not be pushed with the rest of your code.
Do you not know if your site or application is leaking information due to .DS_Store files?

source: https://buildthis.com/ds_store-files-and-why-you-should-know-about-them/
