---
title: Launch Sublime Text 3 from the command line
date: 2016-07-25 17:15:10
tags: [mac,sublime]
---


在命令行当前文件夹快速打开sublime text

<!-- more -->

Sublime Text 3 ships with a CLI called subl. By default you can't use this command line utility unless you do some fiddling.
#### A word about the load $PATH

First up, check your own $PATH by running: echo $PATH. This is what mine returns:  

```
/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin  
```

As you can see the /usr/local/bin path is included by default on OS X.  
#### Installation

```
ln -s "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl" /usr/local/bin/sublime  
```

Yes, I name the symlink **sublime** instead of **subl** because I believe you should always be explicit. You should never have to type the full word anyway. Typing sub + Tab should auto-complete the full name of the symlink.  
#### Testing

Open a Terminal window and run:  
    **sublime** ~/Documents  

open the entire current directory  
    **sublime** .  
#### Conclusion

Now you don't need to get out of Terminal to simply open a file or a folder, you didn't have to add an "alias" or yet another bin directory to your .bash_profile which the official instructions given by the Sublime team seems to recommend.  

Have fun, Sublime is a great editor. Check out the most recent beta release of Sublime Text 3.  

原文链接:[http://olivierlacan.com/posts/launch-sublime-text-3-from-the-command-line/](http://olivierlacan.com/posts/launch-sublime-text-3-from-the-command-line/)
