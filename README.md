Custom Event Provider
=====================

This repository contains an example manifest for creating a custom event provider for the windows event log. This provider was inspired by the Stack Overflow question [How to store an object in the Windows Event Log?](http://stackoverflow.com/questions/43587652/how-to-store-an-object-in-the-windows-event-log)

Most of the content for this manifest came from an article by [Daniel Gordon](http://blog.dlgordon.com/2012/06/writing-to-event-log-in-net-right-way.html) In fact, the steps come directly from his article. I made modifications to his manifest file to represent the details of the Stack Overflow question.

How to Install
==============

1.	Open a git bash prompt and cd to `c` <br/><br/> ![](img/1.PNG) <br/> <br/>
2.	Clone the repository and cd to cloned directory location. <br/><br/> ![](img/2.PNG) <br/> <br/>
3.	Open a Visual Studio Command Prompt and cd to C:\CustomProvider <br/><br/> ![](img/3.PNG) <br/> <br/>
4.	Compile the manifest: `mc -css Namespace CustomProvider.man` <br/><br/> ![](img/4.PNG) <br/> <br/>
5.	Create the resource file: `rc CustomProvider.rc` <br/><br/> ![](img/5.PNG) <br/> <br/>
6.	Compile the source: `csc /target:library /unsafe /win32res:CustomProvider.res CustomProvider.cs` <br/><br/> ![](img/6.PNG) <br/>
7.	Register the provider. `wevtutil im CustomProvider.man` <br/><br/> ![](img/7.PNG) <br/><br/>
8.	You'll now see the custom provider in the Windows Event Viewer <br/><br/> ![](img/8.PNG) <br/> <br/>
9.	To write to the log, open a Windows Powershell prompt and execute `New-WinEvent -ProviderName CustomProvider -Id 10000 -Payload @("MyValue1")` then refresh the event log and you'll see the event. <br/><br/> ![](img/9.PNG) <br/> <br/>
10.	Congratulations, you've created a custom provider thanks to this repository and Daniel Gordon

How to Uninstall
================

1.	3. Open a Visual Studio Command Prompt and cd to C:\CustomProvider <br/><br/> ![](img/3.PNG) <br/> <br/>
2.	7. Unregister the provider. `wevtutil um CustomProvider.man` <br/><br/> ![](img/10.PNG) <br/><br/>
3.	Open new event viewer window and provider will be removed. <br/><br/> ![](img/11.PNG) <br/><br/>
