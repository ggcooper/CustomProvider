Custom Event Provider
=====================

This repository contains an example manifest for creating a custom event provider for with windows event log. This provider was inspired by the Stack Overflow [How to store an object in the Windows Event Log?](http://stackoverflow.com/questions/43587652/how-to-store-an-object-in-the-windows-event-log)

Most of the content for this manifest came for an article by [Daniel Gordon](http://blog.dlgordon.com/2012/06/writing-to-event-log-in-net-right-way.html) In facts, the steps come directly from his article. I made modifications to his manifest file to represent the details of the Stack Overflow.

How to Install
==============

1.	Clone the repository
2.	Open a Visual Studio Command Prompt
3.	Compile the manifest: `sh
	mc -css Namespace CustomProvider.manifest
	`
4.	Create the resource file: `rc CustomProvider.rc`
5.	Compile the source: `csc /target:library /unsafe /win32res:CustomProvider.res CustomProvider.cs`
