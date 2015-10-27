Planet
==============
2015-10-27


This document is a work in progress.



This document is a non official documentation about planets.
It's non official because nobody owns the universe, and therefore nobody has the power to create an official documentation about planets.


I will try to have the approach of the php developer: pragmatic and straight to the point.





So what's a planet?
----------------------

A planet is a php package.

By extension, an universe is an ensemble of somehow related packages.
By extension, the multi-verse is the ensemble of all known universes.
There is nothing bigger than multi-verse.



How do I use a planet?
---------------------------

Download it, download its dependencies, plug all of it into your application, done.



### Download it


Download the git repository.
As for now, it seems that every planet is represented by a git repository, so that should be a no brainer.


### Download its dependencies

It seems that planet authors use the convention of writing their dependencies to other planets in a file 
called package-info.yml.

Look for such a file in the planet you want to use.
If you don't find the package-info.yml file, you can assume that the planet has no dependency.

If there is one, open it and look for the dependencies property.

Note: the file format is [babyYaml](https://github.com/lingtalfi/Dreamer/blob/master/ArrayConfig/BabyYaml/notation.babyYaml.eng.md) so you shouldn't have problem 
to understand it without knowing anything about babyYaml.


The dependencies property is an array containing the dependencies of the planet to other planets.
You might find something like this:


dependencies:
    - git::/lingtalfi/CopyDir:1.0.0
    
    
In this case, the first dash simply indicates that what follows is an array entry.
The git::/ prefix can be interpreted as an alias for https://github.com, basically.
The dependency's url in this case is: **https://github.com/lingtalfi/CopyDir**.

Then the 1.0.0 number at the end, after the colon symbol, indicates the version that the 
planet author used.
On github, if you go to the releases tab (https://github.com/lingtalfi/CopyDir/releases) of the github repository, you will find all available versions.

In this example we want to download the version named 1.0.0 of the lingtalfi/CopyDir github repository. 
As for now on github, you can download a release using the zip version or the tar.gz version.



Repeat the process until all dependencies have been resolved.

Rumors say that a tool is coming, which will resolve dependencies automatically, so you might want 
to check this article again in some future.







### Plug all of it into your application


To plug a planet into your application, you have to be aware of what you are doing.
Planet code doesn't have to be php code, and if it's php code, it doesn't have to be object oriented.
However, if you the planet you want to import is php object oriented code, chances are that the code
uses [BSR-0](https://github.com/lingtalfi/BumbleBee/blob/master/Autoload/convention.bsr0.eng.md) naming convention.




If your planet is BSR-0 compatible, then you simply need to copy the planet files in your application,
in the directory where the autoloader of your application will find them.
 
It could be a directory named planets, or vendor(s), or modules for instance.

If you don't have such a directory yet you need to create one.
There are different methods to do so.

The one that seems to be used the most in the universe is the 
[portable autoloader technique](https://github.com/lingtalfi/TheScientist/blob/master/convention.portableAutoloader.eng.md).
With this technique, you include a [bigbang script](https://github.com/lingtalfi/TheScientist/blob/master/bigbang/bigbang.php)
in your app, and then any planets of the universe you can plug into your app.  


In planets documentation, you'll often see references to the "a" and "az" functions.
Those come from the bigbang script. 
The a function is basically an alias for var_dump, since
planets authors use it a lot (and by that I really mean a lot) for debugging.
 
az does the same job, but also exit at the end, which helps you focusing on the debugging task (for instance
if you are debugging something in the middle of an html page, you might find the az function very useful). 










