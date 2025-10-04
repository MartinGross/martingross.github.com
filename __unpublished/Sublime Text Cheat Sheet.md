# Sublime Text Cheat Sheet

## Multiple selection

Put cursor on a word, then press `CTRL + D` multiple times to get incremental finds of the word with multiple cursors, then edit

Cursor spanning many rows
Press `CTRL + ALT + down`



## Navigation

Go to sidebar
`CTRL + 0`


## Using MarkDown

Install https://github.com/ttscoff/MarkdownEditing

If you are using Sublime Text 2, you have to disable the native MarkDown package manually. To do that, add Markdown to your ignored_packages list in ST user settings:

    "ignored_packages":
    [
        ..., "MarkDown"
    ],


Github flavored markdown: https://help.github.com/articles/github-flavored-markdown

## View the current encoding of a file
To see the encoding of an opened file, go to

    View -> Show Console

then type on the console the following command:

    view.encoding()

## Sublime Documentation
http://docs.sublimetext.info/en/latest/index.html

## Editing files of installed packages

In ST3, packages are run directly from .sublime-package files rather than needing to be extracted. 

You should be able to override any particular file by creating that folder with a file named the same. For example, if you want to override "Default/Default (OSX).sublime-keymap", you would simply create that file in the packages directory. I personally think this is acceptable, and sometimes better. This will prevent users from "accidentally" modifying some default package (or installed package). Someone wrote the PackageResourceViewer plugin to help view/edit the "sublime-package" files.