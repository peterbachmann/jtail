jtail
=====

A Java version of the UNIX tail command using NIO.2

Basically, all old Java versions of tail that I could find had a design pattern of the following:

open file
while (true)
{
    try
    {
        read file
        write file to output
        thread.sleep(1 second)
    } catch (InterruptedException) {}
}
close file

Since time immemorial, the UNIX tail command, if it is available, makes use of 'inotify' to receive
messages from the kernel regarding changes to the files it watches.

With Java SE 7, this possibility is open to us as well, by means of the WatchService.

Just thought I'd see how good this works.

Usage
-----

java -classpath jtail.jar;jopt-simple-4.5.jar com.tools.jtail.Jtail --help

java -classpath jtail.jar;jopt-simple-4.5.jar com.tools.jtail.Jtail -version

java -classpath jtail.jar;jopt-simple-4.5.jar com.tools.jtail.Jtail ipsum.txt

java -classpath jtail.jar;jopt-simple-4.5.jar -Djava.util.logging.config.file=logging.properties com.tools.jtail.Jtail ipsum.txt

For more information
--------------------

WatchService Javadoc:
http://docs.oracle.com/javase/7/docs/api/java/nio/file/WatchService.html

My blog:
https://randomthoughtsonjavaprogramming.blogspot.com/

My github homepage:
http://maartenl.github.io/

