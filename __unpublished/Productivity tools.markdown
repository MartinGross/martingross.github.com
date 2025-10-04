# Productivity tools, I couldn't work without

## for Windows

### [Chocolatey](https://chocolatey.org/)
Tired of installing software on windows little by little?
The package manager for Windows
kind of like apt-get, but for Windows


### [Launchy](http://www.launchy.net/)
It is tiring to start programs with the mouse from the Start Menu. This little utility indexes the programs in your start menu and can launch your documents, project files, folders, and bookmarks with just a few keystrokes!

### [AutoHotKey](http://www.autohotkey.com/)
A really powerful Hotkey and Scripting Automation tool. It can save you a lot of typing. As an very simple example, expand abbreviations as you type them. Typing "brg" can automatically produce "Best regards, Martin".
Think of it as a Windows Automation Tool 

### [ResophNotes](http://www.resoph.com/ResophNotes/Welcome.html)
Simple and fast notes on Windows, searchable and can sync with [SimpleNote](http://simplenote.com/)

### [Dropbox](http://www.dropbox.com/)
Sync files between multiple computers, tablets and smart phone.

### [Sublime Text 2 or 3](http://www.sublimetext.com/)
One of the best editors for programming and viewing files.
	* https://github.com/timonwong/OmniMarkupPreviewer
		* <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>O</kbd>: Preview Markup in Browser.
		* <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>X</kbd>: Export Markup as HTML.
		* <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>C</kbd>: Copy Markup as HTML.

#### Package Manager for Sublime
[Package Control](http://wbond.net/sublime_packages/package_control)

#### Better looking theme for Sublime
[Phoenix Theme](https://github.com/netatoo/phoenix-theme)

[Material Theme](https://equinusocio.github.io/material-theme/)
I would recommend to install the Roboto Mono font from Google. Or mononoki (https://github.com/madmalik/mononoki/blob/master/export/mononoki.zip).

#### Markdown editing
https://sublimetext-markdown.github.io/MarkdownEditing/

If you are using Sublime Text 2, you have to disable the native MarkDown package manually. To do that, add Markdown to your ignored_packages list in ST user settings:

	"ignored_packages":
	[
		..., "MarkDown"
	],


If you would like to use the color scheme of Material Theme for Markdown, you'll need to change Markdown.sublime-settings file.

Change the line with the "color_scheme" from

	"color_scheme": "Packages/MarkdownEditing/MarkdownEditor.tmTheme",

to

	// disabled to avoid conflict with material theme 
	// "color_scheme": "Packages/MarkdownEditing/MarkdownEditor.tmTheme",  

The file is write protected. So you need to extract it from the ZIP file *MarkdownEditing.sublime-package*, edit it and put it back there.

#### Reformat XML & JSON
Plugin for Sublime Text editor for reindenting XML and JSON files

Key:

	Ctrl+K, Ctrl+F

[indentxml](https://github.com/alek-sys/sublimetext_indentxml)

Or [using xmllint](http://www.bergspot.com/blog/2012/05/formatting-xml-in-sublime-text-2-xmllint/)

### [Outlook Google Calendar Sync](https://outlookgooglecalendarsync.codeplex.com/)
https://outlookgooglecalendarsync.codeplex.com/
Does what it says: Synchronize Outlook with Google Calendar

### [Intellij IDEA](http://www.jetbrains.com/idea/)
IMHO, the best IDE for Java programming. Support for other languages like Ruby and HTML/Javascipt is also awesome.

### [Ditto](http://ditto-cp.sourceforge.net/):
Multiple copy and pastes
Clip board Manager

### [Total Commander](http://www.ghisler.com/)
A very powerful file manager for Windows. Too many features to list here but consider it as _the_ "swiss army knife" for file handling.

### [Greenshot](http://getgreenshot.org/)
Awesome screenshot tool for Windows. And it's open source.

### [Keepass]

### Process Explorer

### Cygwin

### Improve usability

[Meslo Font](https://github.com/andreberg/Meslo-Font)
Activate [ClearType] on Windows 

## Security

### Axcrypt

### TrueCrypt

### Uru, Ruby version manager
https://bitbucket.org/jonforums/uru

### Slack

### Shoes
GUI for Ruby
Nice for creating utilities

## Mac OS X

### iTerm2
Terminal deluxe

Install vim colors
	https://github.com/altercation/vim-colors-solarized

Install iTerm colors
	https://github.com/altercation/solarized/tree/master/iterm2-colors-solarized

Set bash to use colors
	$ vi ~/.bash_profile
	export CLICOLOR=1

### Homebrew
brew doctor
only runs if you have admin rights

### Quicksilver
Start everything from the keyboard

### rbenv
* Install ruby with rbenv install 2.0.0-p247
Problem with host: https://github.com/sstephenson/ruby-build/issues/405

### FileMerge
Merge files or directories
Part of Xcode tools

### DigitalColor Meter
Get color values from the screen
Included with OSX

### Bildschirmfoto 
Screenshot Program
Included with OSX 

### nvAlt

### fish shell 