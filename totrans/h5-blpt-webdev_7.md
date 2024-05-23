# Chapter 7. Automate Deployment With the Build Script

We are ready to deploy our site! But before we do that, we should ensure we minimize all our scripts and optimize the images, so that these pages load as quickly as possible anywhere in the world. We can automate these tasks by executing a script on the command line. Let us look at the options we have.

# The build script

Once you are done with your project, you would like to generate files that strip comments and are optimized for loading quickly. There are software build systems that are typically used in software projects with similar goals. HTML5 Boilerplate's build scripts provide tasks scoped to what a typical web development project would need.

The script should be used only after you have confirmed your project is ready for deployment and it has been well tested. The build script merely automates the process of removing comments, optimizing files, and making sure the files are production ready.

There are currently two kinds of build scripts that are actively maintained by HTML5 Boilerplate contributors; these are explored in the following section.

## Ant build script

The Ant build script is a set of files that work on top of the Apache Ant build system (`ant.apache.org/`) that has been available since the early days of HTML5 Boilerplate. It offers a variety of options, described as follows:

*   Publishes files to test, development, and production environments
*   Checks syntax and code quality of your script files with **JSHint** or **JSLint**, or your stylesheets with **CSSLint**
*   Concatenates and minifies all your JavaScript files into a single file and updates the HTML pages with reference to this new file
*   Cleans up and tidies HTML markup by removing comments, whitespaces, and compressing inline styles and scripts
*   Concatenates and minifies all your stylesheets and updates the HTML pages with reference to the new file instead of multiple CSS files
*   Compiles style preprocessor files such as Less or Sass into the resulting CSS stylesheets and updates references in HTML pages
*   Optimizes PNG and JPEG images within the `img` folder using OptiPNG from `optipng.sourceforge.net/` and JPEGTran from `jpegclub.org/jpegtran/` respectively
*   Builds documentation from your scripts using JSDoc3 from `github.com/jsdoc3/jsdoc`

## Node build script

A new build script that builds on top of Node, found at `nodejs.org/`, is under active development. While it is not out for production use yet, it offers a lot of tasks that are similar to the Ant build script with some new features described as follows:

*   Concatenates and minifies all your JavaScript files into a single file and updates the HTML pages with reference to this new file
*   Concatenates and minifies all your stylesheets and update the HTML pages with reference to the new file instead of multiple CSS files
*   Cleans up and tidy HTML markup by removing comments, whitespaces, and compressing inline styles and scripts
*   Optimizes PNG and JPEG images within the `img` folder using OptiPNG and JPEGTran respectively

Watch the project files for changes, and automatically run the build script and reload open pages in browsers when they do.

## Which build script to use?

Depending on what platforms you are comfortable with, you can choose one over the other. Both the build scripts are stable enough to use to deploy your production files, so your choice is down to what you are most comfortable using.

If you already have Ant installed, the Ant build script might be an obvious choice. If you find yourself using Node frequently or using it in your projects, then the Node build script could be a good start. In this chapter, we will look at using both, so you can become comfortable with either of them.

# Using the Ant build script

First, confirm you have Ant installed on your system by entering the following in your command-line tool:

[PRE0]

If you do not have Ant, install it first before proceeding to the next step.

### Note

Ant is installed by default on Macs, while it is available as a package to install on most Linux platforms. For Windows, installing Ant is slightly more complicated. You need to install the Java SDK from [www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html) and then download `WinAntcode.google.com/p/winant/` and point the installer to `Program Files/Java/jre6/bin/`.

Next, you need to install **ant-contrib** , a utility that makes a lot of functionality available for Ant that HTML5 build script uses. **WinAnt** does this automatically, when you use it to install Ant on Windows. However, for Linux users, you can use **yum** to install it as a package. On Mac, you can install MacPorts ([www.macports.org/install.php](http://www.macports.org/install.php)) and then enter the following in your command-line tool (typically Terminal):

[PRE1]

Finally, ensure that the image optimization tools are installed. For Mac users, you need to make sure you have **jpegt** **ran** ([www.ijg.org/](http://www.ijg.org/)) and **optipng** (`optipng.sourceforge.net/`) installed and on your path. You can install these two files by entering the following in your command-line terminal:

[PRE2]

### Note

The `PATH` is an environmental variable that holds a list of folders that your command-line interface searches through when you enter a command. You can learn about how to add folders to the path from [www.cs.purdue.edu/homes/cs348/unix_path.html](http://www.cs.purdue.edu/homes/cs348/unix_path.html).

If you are on Windows, the Ant build script project contains the required binaries for these image tools for you to install.

## Installing the build script

In Terminal (or your command-line tool), we will navigate to our project folder and install the build script using Git, as shown in the following screenshot:

![Installing the build script](img/8505_07_01.jpg)

We now have to rename the build script folder from `ant-build-script` to `build` before we continue. This is done by using the following command:

[PRE3]

Once that is done, let us navigate to the build script folder by using the following command:

[PRE4]

Now, we shall execute the build script! Go to your command-line tool and enter the following:

[PRE5]

If you set up your build script folder correctly, then you should get the following screen:

![Installing the build script](img/8505_07_02.jpg)

Then, after the tasks are executed, you should get the following output:

![Installing the build script](img/8505_07_03.jpg)

Now, you have a brand new `publish` folder where the optimized files are stored. Let us look at what all have been optimized, by opening the `index.html` page from the `publish` folder, in Chrome browser and using the Chrome Developer Tools' **Network** tab to observe the files that are loaded and their associated sizes.

Please note that you must load the page with the **Network** tab open to log the files being requested.

## Smaller image files

The **Network** tab records all images that are fetched for use on `index.html`. We can see that the images that are fetched for the `index.html` page in the **publish** folder are noticeably smaller in size.

In the following screenshot, the bottom section of the screenshot shows the list of images in the **publish** folder, which are noticeably smaller than the images used in our original project (listed in the top section of the screenshot):

![Smaller image files](img/8505_07_04.jpg)

## Smaller CSS file

We note that before we used the build script, our CSS file was called `main.css` and was approximately 21 KB, but after using the build script, the file has been renamed and is now almost half the original size, as shown in the following screenshot:

![Smaller CSS file](img/8505_07_05.jpg)

## Smaller and fewer JS files

After executing the build script, you will notice that `main.js` and `plugin.js` have been combined into one. Not only have they been combined together, but they have also been minified, leading to a smaller file size of the final script file.

The `index.html` page from the `publish` folder generated via the build script invokes only four JavaScript files as shown in the bottom section of the following screenshot, compared to five JavaScript files originally placed in the folder (top section):

![Smaller and fewer JS files](img/8505_07_06.jpg)

## No comments in files

The HTML, CSS, and JS files in the `publish` folder have no comments that HTML5 Boilerplate files contain.

## Build options

The Ant build script has a few tasks that are not executed by default, but are available to you if you need them. The following sections explain what these tasks allow you to do.

### Minifying markup

By default, the Ant build script does not remove whitespaces from the `index.html` page when optimizing; if you want to also remove whitespaces in the HTML file and minify it, you can execute the following:

[PRE6]

### Preventing image optimization

When executing the build script, you will notice that the script takes the longest time to optimize images. If you are executing the build script to merely test the final production-ready files, then you would not have to optimize images. In this case, you should execute the following command:

[PRE7]

### Using CSSLint

CSS Lint (`csslint.net`) is an open source CSS code-quality tool that performs a static analysis of your code and flags style rules that are invalid or may be the cause of problems. To use CSS Lint on your project's CSS files, just enter the following:

[PRE8]

Typically, you will observe a bunch of warnings. CSS Lint has a lot of options you can set. To do this, open the `project.properties` file within the `config` folder in build. Uncomment this line by removing the `#`, by using the following command:

[PRE9]

Enter all the options you want to use with CSS Lint after the `=` sign and save. The various options that you can use are mentioned at `github.com/stubbornella/csslint/tree/master/src/rules`.

### Using JSHint

JSHint (`jshint.com`) is a community-driven tool to detect errors and potential problems with your JavaScript code and enforce your team's coding conventions. To execute JSHint on your JavaScript files, go to your project and execute the following:

[PRE10]

Once executed, we see a bunch of errors being listed for our `main.js`. The corrected file is included within the code for this chapter. Once corrected, you will also notice a whole slew of errors being thrown for the code in `plugin.js`. This is because we used the minified code of the smooth-scroll plugin. Let us replace it with the unminified code from the project repository at `github.com/kswedberg/jquery-smooth-scroll/blob/master/jquery.smooth-scroll.js`.

Now, we get a bunch of errors all telling us we need to use the stricter comparison operator. Let us turn this off for our current project. We can do this by opening the `project.properties` file within the `config` folder under our `build` folder and uncomment the following line that allows you to use your own options for JSHint:

[PRE11]

Change it to the following snippet:

[PRE12]

### Note

More options are listed on the JSHint website at `jshint.com`.

Our errors have disappeared!

### Setting up the SHA filenames

The concatenated and minified CSS and JS filenames are set to uniquely generated strings, which ensures a cached local copy of these files never get loaded when a new production build is deployed to the server. By default, the number of characters used in the filename is `7`. You can set it to a smaller or larger number by changing the following line in `project.properties` within the `config` folder inside the `build` folder:

[PRE13]

Uncomment the previous line and then alter the number `7` to the number of characters you prefer, using the following syntax:

[PRE14]

## Using with Drupal or WordPress

Minor changes need to be made to make sure that these Ant build scripts work as intended for Drupal. Do note that there is not much help in minifying the HTML pages as a significant portion of the markup will be generated by Drupal or WordPress.

### Updating build.xml

There is a minor change you need to make to `build.xml` to make it work with the file structure of Drupal or WordPress.

Look for `<echo message="Minifying any unconcatenatedcss files..."/>` within the file. Just after that line of code, change the following:

[PRE15]

To the following:

[PRE16]

### Setting up the project configuration properties

In the `project.properties` file within the `config` folder of the `build` folder, add the following code:

[PRE17]

### Setting the JS file delineator

WordPress or Drupal themes require you to split your markup into separate files (for example, `footer.php` for WordPress or `footer.tpl.php` for Drupal). You need to know in which of these files the following code is located:

[PRE18]

Use that filename (for example, `footer.php`) to set the `file.root.page` property in the `project.properties` file by using the following code:

[PRE19]

A sample Drupal and WordPress theme that contains the modified build script are provided in the code for this chapter.

# Using the Node build script

The Node build script is different from the Ant build script in the following two ways:

*   It installs universally and does not need to be copied from one project to the other.
*   All projects should be initialized with the Node build script. It is significantly more troublesome to add it on to a project that is already underway.

The Node build script requires Node, so verify you have Node installed by entering the following command:

[PRE20]

If you do not have Node already, you can install it from `nodejs.org/` (or by using **package manager** from [github.com/joyent/node/wiki/Installing-Node.js-via-package-manager](http://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager).

## Grunt

**Grunt** (`gruntjs.com/`) is a Node-based command-line build tool on which this Node build script is based. The Node build script provides HTML5 Boilerplate optimized tasks that plug into Grunt.

This requires using a `package.json` file along with a `grunt.js` file within your project folder, which can be set up when you initialize your project.

## Installing Node build script

In your command-line tool, first install the Node build script package, by entering the following command:

[PRE21]

The Node build script can also be used as a part of a bigger build setup. If you are inclined to using it differently, take a look at all the possible ways of doing so here at `github.com/h5bp/node-build-script/wiki/install`.

Once installed, you can create your HTML5 Boilerplate project folder by initializing it.

### Initializing your project

You can choose from various options to set up a project folder for yourself. Let us use this to set up a temporary project, to learn how to use this script to start your HTML5 Boilerplate project.

Create a folder where your HTML5 Boilerplate project should be. Navigate to it within your command-line tool and enter the following command:

[PRE22]

This will start setting up a whole set of command-line interactions for you to choose from. It is mostly used to set up information for package management that will be used by Grunt.

Once you have done that, you have three options to choose from for setting up the files you want to start with; these options are as follows:

*   `[D]efault`: Standard set of files for HTML5 Boilerplate.
*   `[C]ustom`: Get all the standard files with the option of choosing to rename `js/`, `css/`, or `img/` folders. You would typically want to do this if your files are going to be used as templates for other systems such as Drupal or WordPress.
*   `[S]illy`: Prompts to rename every folder/file in HTML5 Boilerplate. You are least likely to use this option, unless you are a semantic perfectionist.

After you choose the type of installation you want to do, there are also more questions that are asked. Note that if you press *Enter*, the default value as indicated within parenthesis will be set.

This will then download the latest version of HTML5 Boilerplate from the Github repository for you to start as your base.

### Using the Node build script with an existing project

It is not impossible to use the script with an existing project, but it's just a bit more tedious. There is work underway in the project to make this happen at `github.com/h5bp/node-build-script/issues/55`, but until then, the following is how we can use it with our Sun and Sand website:

1.  First, create a temporary folder, and execute the Node build script to initialize an empty project from the command line as described in the earlier section.
2.  Then, copy only `package.json` and `grunt.js` into your project folder.

You can see the code in the `nimbu.in/h5bp-book/chapter-7-node-init/` folder to see this in action.

## Using the Node build script to build your project

Navigate to the Sun and Sand project folder (that you initialized it in the previous section) in your command-line tool and enter the following command:

[PRE23]

This will combine the files and the results are published in the `publish` folder just like the Ant build script. You can also use these other build options like the Ant build script.

### Text

If you would like to leave out compressing images when building your project, then use the following command:

[PRE24]

### Minify

If you would like to additionally minify HTML files, then use the following command:

[PRE25]

The results are similar to what you would find with Ant build script; the following screenshot shows the result of the minification process:

![Minify](img/8505_07_07.jpg)

There are some additional options available that you don't get with Ant build script.

### Server

This will open a local server instance you can immediately preview your website on. This is useful when you want to test the pages where protocol-relative URLs are used to link to files. To do this, simply navigate to your project folder in the command-line tool and enter the following command:

[PRE26]

You will see the server being started for both the `publish` folder and the `intermediate` folder, as shown in the following screenshot:

![Server](img/8505_07_08.jpg)

Then, open `http://localhost:3001` to view the published site.

### Connect

Using this command, you can see your page reload on browsers it is open in as soon as you have made changes to any asset within the project. This saves you from refreshing the page manually to see the change. To do this, just navigate to your project folder in the command-line tool and enter the following command:

[PRE27]

## Using with Drupal or WordPress

It is fairly trivial to initialize an HTML5 Boilerplate project with Node build script and then convert it into a template you are building for Drupal or WordPress. First, make sure you choose the `Custom` option when executing `h5bp init`. Then, when setting the folders, set `inc` as the folder where your stylesheet will be, and `images` as the name of the folder that would contain your template images. When you are prompted again, enter in the same values and the project framework will be generated for you. Make sure you replace `index.html` with your template files.

Once you have done this, open the `grunt.js` file in your project folder and confirm that the stylesheet's folder is set to the parent folder by using the following code:

[PRE28]

Make sure that only JavaScript files and stylesheets get prefixed with the SHA filenames, by editing or removing images from being renamed. This is done by using the following code:

[PRE29]

The script also needs to know the new location of the `images` folder. We can do this by setting the source and destination folders for images, as shown in the following code snippet:

[PRE30]

# Next steps

Once we are satisfied with our production files in the `publish` folder, then we can move it to our hosting provider to replace the files that make our website.

Ideally, you would be using a Version Control System to do this, so you can quickly roll back an update in the unlikely event of this update making some page unavailable.

If you are only creating a template for Drupal or WordPress, then it may help to move this to within the WordPress folder on the server that is under a Version Control System.

Alternatively, you can compress your project and then copy the files to the server where they can be decompressed and used. The Node build script provides an option to do this. Go to your project folder in your command-line tool and enter the following command:

[PRE31]

Use the name that best describes your project instead of `<project-name>`. Then, copy the `<project-name>.tgz` to your server and expand it into the folder you would want the files in.

# Summary

In this chapter, we learned how to use two kinds of build scripts that are available from the HTML5 Boilerplate team. We also looked at how we can use them both with Drupal or WordPress templates. We also looked at what we can do once the files have been built.

In the next chapter, we will look at some advanced tasks you can take on, now that you know how to create and deploy projects using HTML5 Boilerplate.