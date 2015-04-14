+++
draft = false
title = "do you know how to use curl"
date = "2015-04-16"
publishdate = "2015-04-16"
author = "Satish Talim"
authorlink = "http://satishtalim.com"
authorfacebook = "http://www.facebook.com/satishtalim/about"
authorgoogleplus = "https://plus.google.com/+SatishTalim/about"
authorlinkedin = "https://www.linkedin.com/in/satishtalim"
authortwitter = "http://twitter.com/IndianGuru"
categories = ["Satish Talim"]
nocomment = false
socialsharing = true
tags = ["curl", "Command Line", "network tools"]
permalink= "do-you-know-how-to-use-curl"
totop = true
+++

## Downloading and installing cURL

cURL is available on many platforms, including Windows (all variants),
OSX (all versions) and Linux (all distros). cURL is available from the
cURL website at [http://curl.haxx.se/](http://curl.haxx.se/).


To install cURL on Linux, you should first check for cURL binaries in
your distributions package repository. For exact instructions on how to
do this, refer to your distribution's documentation. On Ubuntu and other
Debian variants, you can install cURL by issuing the following command.

    $ sudo apt-get install curl

If cURL is not available in your distribution's package repository or
you're running another operating system, you can find the right cURL
package by following the download wizard located at
[http://curl.haxx.se/dlwiz/](http://curl.haxx.se/dlwiz/). Simply select
the "curl executable" option, input information about your computer and
operating system and it will direct you to the correct file
download. Once downloaded, extract any files in the archive to an easily
accessible file (for example, c:\\cURL on Windows).

cURL is a command-line tool. This means it is run from the command
prompt (in Windows) or terminal (in Linux or OSX) and its results are
displayed in the terminal window. There is no graphical interface. So in
order to use cURL, you first have to open a command-line window.

On Windows, go to Start -\> Run and enter "cmd" (without quotes) into
the dialog and press enter.

On OSX, open the Terminal application. You'll find this in the
Applications/Utilities folder.

On Linux, open a Bash Prompt or Terminal window.  Again, since all
distributions are different, refer to your distributions documentation
for more detailed information.  On Ubuntu, you can open a bash prompt by
going to Applications -\> Accessories -\> Terminal.

Though Windows, OSX and Linux all run different command-line shells (the
program that interprets commands on the terminal and runs executables),
the commands presented here will work on all of them.

First, change the directory to where you extracted the cURL archive. If
you installed cURL using an installer or a package on Linux, cURL will
already be in your path (meaning it can be run even though you're not
currently in the same directory) so this isn't needed. For example, if I
placed cURL in `C:\\cURL` on my Windows computer, I would issue the
following command.

    > cd C:\cURL

You can now issue cURL commands. On Linux or OSX, you may have to
prepend `./` to your commands. For example, instead of `curl http://some/url`,
the command you'd use would be `./curl http://some/url`.

To test cURL, enter the following command.

    curl -I [http://twitter.com/](http://twitter.com/)

You should see HTTP response headers. The first line should be "HTTP/1.1
200 OK." This means you've made a successful request to Twitter using
cURL.

## Using cURL

cURL is a command-line tool. This means it's launched from a command
line with a number of switches and parameters. Switches change how the
cURL command will act, and begin with the - character. For example, the
previous example used the -I switch, which means to display the HTTP
response headers only, and not the HTTP response body. Parameters pass
information to either a switch, or the cURL command itself. In the
previous example, the Twitter URL was a parameter.

Please refer to the following URL for the various options available in
cURL:

<http://curl.haxx.se/docs/manpage.html>
 
