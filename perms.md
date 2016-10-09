Permissions Overview
====================
Have you ever felt confused or even overwhelmed when trying to set Nadeko's permissions? In this guide we will be explaining how to use the 
permission commands correctly and even cover a few common questions! Every command we discuss here can be found in the [Commands List](http://nadekobot.readthedocs.io/en/latest/Commands%20List/#permissions).

Why do we use the Permissions Commands?
----------------------------------------
Permissions are very handy at setting who can use what commands in a server. By default, the NSFW module is blocked, but nothing else is. If something is a bot owner only command, it can only be ran by the bot owner, the person who is running the bot, or has their id in [`credentials.json`](http://nadekobot.readthedocs.io/en/latest/JSON%20Explanations/ "Setting up your credentials"). 

The administration module still requires that you have the correct permissions on discord to be able to use these commands, so for users to be able to use commands like `.kick` and `.prune`, they need kick and mange messages permissions respectively.

With the permissions system it possible to restrict who can skip the current song, pick NadekoFlowers or use the NSFW module.

First Time Setup
-----------------
To change permissions you **must** meet the following requirement:

**Have the role specified by `;permrole` (By default, this is Nadeko)**

If you have an existing role called "Nadeko" but can't assign it to yourself, create a new role called "Nadeko" and assign that to yourself.

If you would like to set a different role, such as "Admins", to be the role required to edit permissions, do `;permrole Admins` (you must have the current permission role to be able to do this).

Basics & Hierarchy
-------------------
The [Commands List](http://nadekobot.readthedocs.io/en/latest/Commands%20List/#permissions) is a great resource which lists **all** the available commands, however we'll go over a few commands here.

Firstly, let's explain how the permissions system works - It's simple once you figure out how each command works!
The permissions system works as a chain, everytime a command is used, the permissions chain is checked. Starting from the top of the chain, the command is compared to a rule, if it isn't either allowed or disallowed by that rule it proceeds to check the next rule all the way till it reaches the bottom rule, which allows all commands.

To view this permissions chain, do `;listperms`, with the top of the chain being rule number 1, shown at the top of the message.

If you want to remove a permission from the chain of permissions, do `;removeperm X` to remove rule number X and similarly, do `;moveperm X Y` to move rule number X to number Y (moving, not swapping!).

As an example, if you wanted to enable NSFW for a certain role, say "Lewd", you could do `;rolemdl NSFW enable Lewd`.
This adds the rule to the top of the permissions chain so even if the default `;sm NSFW disabled` rule exists, the "Lewd" role will be able to use the NSFW module.

If you want the bot to notify users why they can't use a command or module, use `;verbose true` and Nadeko will tell you what rule is preventing the command.

Commonly Asked Questions
-------------------------

###How do I create a music DJ?
To allow users to only see the current song and have a DJ role for queuing follow these five steps: 

	1.	`;sm Music disable`
1. Disables music commands for everybody
	2.	`;sc !!nowplaying enable`
2.	Enables the "nowplaying" command for everyone
	3.	`;sc !!getlink enable`
3.	Enables the "getlink" command for everyone
	4.	`;sc !!listqueue enable`
4.	Enables the "listqueue" command for everyone
	5.	`;rm Music enable DJ`
5. Enables all the music commands only for the DJ role


###How do I create a NSFW channel?
Say you want to only enable NSFW commands in the #NSFW channel, just do the following two steps.

	1.	`;sm NSFW disable`
1. Disables the NSFW module from being used
	2.	`;cm NSFW enable #NSFW`
2. Enables the NSFW module for use in the #NSFW channel

_-- Thanks to @applemac for providing the template for this guide _
