Macrosploit - Multi Platform Social Engineering / Penetration Testing Macro Payload
===========

Microsoft Word Macros have been used successfully as social engineering payloads for penetration testers for years. This method does not actually use any exploits, it uses the intended functionality of a macro for unintended purposes. If you can trick a user into enabling Macros then code execution on the users system is possible. Macrosploit introduces a new method for the built in Applescript of OS X operating systems and the built in Powershell of Windows to create one office document that will work on both platforms. Future plans include a macro for LibreOffice in Linux. 
Tested and working on the following:

Windows 7 Pro x64 - Microsoft Office Professional Plus 2010

OS X 10.9.5 - Microsoft Word for Mac 2011 14.2.0

Features:

Automatically runs on document open when Macros are enabled

OS X Persistent Reverse Shell using Bash and Plist persistence

Bypasses built in OS X GateKeeper Security!!!

What it does:

On Mac it will create a reverse shell connection to the listener that you must specify
It uses the plist method of persistance so that a new reverse shell is attempted ever 120 seconds (WARNING: You must manually remove the com.apple.video2.plist file or unload plist to remove this persistance). The Macro attempts to run with root privileges, if successful it sets up a reverse shell with root privileges, it will also set up a user reverse shell in case the root privileges can not be obtained. 

On Windows it will execute powershell payload of your choice this could be a reverse shell, Meterpreter, or Beacon if you have access to Cobalt Strike (www.advancedpentest.com).

How to use it:

For the Mac payload just change the reverse shell listener to your listener IP address, change the port (currently 4444) to your listener port. E.g. nc -lvp 1234 (or use the generic/shell_reverse_tcp in Metasploit). For the Windows payload change to the powershell command of your choice.

I have found that an effective way of packaging the Macro is in a word document named Vacation Photos. 
This could be Vacation_Photos_CEO-Name-Here.doc or really anything. 
The idea is to make the name of the file interesting enough that someone would want to open it bad. 
Bad enough to go against thier better judgement and allow macros just to load the photos. 
Unfortunately for the user that opens the document there is a present inside but it does not include any vacation photos :)

The text in the document can simply be something like this:

Windows Users - Photos cannot be viewed unless editing is enabled and content is enabled. Please make sure to select the ”Enable Editing” and “Enable Content” buttons above to view this document.

Mac Users – Please reopen this document and select “Enable Macros” to view photos.

Future Plans

Create a script (SET like) to automate creation of Macro using selection of payloads, automate starting listener.

Test on Libre Office / Open Office for Linux reverse shell so that one payload can work on Windows, OSX, Linux and Unix.

