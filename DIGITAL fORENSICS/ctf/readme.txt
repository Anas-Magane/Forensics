


SecurityQuestionsView v1.00
Copyright (c) 2019 - 2020 Nir Sofer
Web site: https://www.nirsoft.net/utils/security_questions_view.html



Description
===========

SecurityQuestionsView is a tool for Windows 10 that allows you to view
the security questions and their answers stored in the Registry by
Windows 10 operating system.
SecurityQuestionsView can decrypt the security questions stored on your
current running system (Requires elevation) and it can also decrypt the
security questions stored on external hard drive.

SecurityQuestionsView displays the security questions of all users on
your system that chose to set their security questions, for every user
there are usually 3 questions.



System Requirements
===================

This tool works on Windows 10, both 32-bit and 64-bit systems. For
extracting the security questions from external drive, you can run this
tool on earlier versions of Windows (Windows 7, Windows Vista).



Start Using SecurityQuestionsView
=================================

SecurityQuestionsView doesn't require any installation process or
additional DLL files. In order to start using it, simply run the
executable file - SecurityQuestionsView.exe
After running SecurityQuestionsView, you have to choose how to load the
security questions - From your local system or from external drive.
If you choose to load the security questions from your local system,
SecurityQuestionsView will ask you to run this tool as Administrator
(Elevation), because only Administrator can access and decrypt the
security questions.
If you choose to load the security questions from external drive, you
have to type the folder where the Registry files are located, for
example: K:\windows\system32\config
The Registry hive needed to extract the security questions is SAM.

After the security questions and their answers are displayed on the main
window of SecurityQuestionsView, you can select the questions (Ctrl+A)
and then export them to comma-delimited/tab-delimited/XML/HTML file by
using the 'Save Selected Items' option (Ctrl+S).



Translating SecurityQuestionsView to other languages
====================================================

In order to translate SecurityQuestionsView to other language, follow the
instructions below:
1. Run SecurityQuestionsView with /savelangfile parameter:
   SecurityQuestionsView.exe /savelangfile
   A file named SecurityQuestionsView_lng.ini will be created in the
   folder of SecurityQuestionsView utility.
2. Open the created language file in Notepad or in any other text
   editor.
3. Translate all string entries to the desired language. Optionally,
   you can also add your name and/or a link to your Web site.
   (TranslatorName and TranslatorURL values) If you add this information,
   it'll be used in the 'About' window.
4. After you finish the translation, Run SecurityQuestionsView, and
   all translated strings will be loaded from the language file.
   If you want to run SecurityQuestionsView without the translation,
   simply rename the language file, or move it to another folder.



License
=======

This utility is released as freeware. You are allowed to freely
distribute this utility via floppy disk, CD-ROM, Internet, or in any
other way, as long as you don't charge anything for this and you don't
sell it or distribute it as a part of commercial product. If you
distribute this utility, you must include all files in the distribution
package, without any modification !



Disclaimer
==========

The software is provided "AS IS" without any warranty, either expressed
or implied, including, but not limited to, the implied warranties of
merchantability and fitness for a particular purpose. The author will not
be liable for any special, incidental, consequential or indirect damages
due to loss of data or any other reason.



Feedback
========

If you have any problem, suggestion, comment, or you found a bug in my
utility, you can send a message to support@nirsoft.net
