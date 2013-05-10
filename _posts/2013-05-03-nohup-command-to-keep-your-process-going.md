---
layout: post
title: nohup utility to keep your process going
comments: true
---

As part of my job, I had this task that involved handling huge TSV datasets (of 1b records). My specific task was to parse all of the datasets and form a new combined one. 

Despite the fact thar it will take days until completed, this parsing task sound easy to handle. However, the main difficulty I was facing - was that I had to run the process on another server through my own computer with an internet line that was occasionally interrupted.

So after a few failed attempts of running this through my local machine, I started searching for a solution that will allow me to run a script on a remote unix server without having to stay connected (to server) throughout the entire process.

# And there was nohup

nohup is a unix utility that enables you to run a command and keep it running even though session is disconnected or user has logged out.

    $ nohup ./parser.sh &

This simple command saved my computer from working days and nights continuously. This utility, `"no hang up"`, runs a command while staying immune to hangup signals such user logging out etc. 

Besides running the script without interruptions, it also prints the output of the file into `$HOME/nohup.out`. This can be very useful handling errors or even listening the process' progress with `tailing` the log.

	