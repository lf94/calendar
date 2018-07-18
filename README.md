# The *best* calendar reminder solution on the Internet

`calendar` is a standard program included with most UNIX-like operating systems. Try it out! You'll quickly discover this little tool is very useful. The file format is extremely simple too:

```
July 1<tab>Canada Day
Dec 25<tab>Christmas Day
```

As a local solution, this works very well. The issue is, how can we mix in remote calendars too? That's where this wrapper script comes in.

## Adding a remote calendar

To add a remote calendar, users are expected to host their calendars on a webserver (technically anything `curl` can download from!), and invoke: `calendar remote <url> <filename>`.

A real world example of this could be `calendar remove http://calendar.stallman.org/pub richard.pub`, to get Richard Stallman's public calendar data.

The naming scheme has been chosen to reflect some people will have public dates (.pub) and private dates (.priv) they will and will not want to show to people.

## Why?

There are issues I find with Google Calendar, the go-to synchronized calendar solution.

1. Proprietary
2. Complex
3. UI is not good for lots of tasks to read
4. Cannot be self-hosted

## Installation 

All you need to do, is run `./calendar init`. Every invocation after this can be done with just `calendar`.

This will create your `~/.calendar` directory, and install this `calendar` program to `/usr/local/bin/calendar`, hopefully taking precedence over `/usr/bin/calendar`. Note that this program is meant to be a superset of what the standard `calendar` offers, and calling it with standard `calendar` commands will work!

## Synchronization (Download)

In order to synchronize there are two options:

1. You create a cron job that invokes `calendar refresh`.
2. You directly invoke `calendar refresh`.

Most likely, you will want to use `calendar refresh` when someone tells you they have updated their calendar. This command will re-download all calendars.

## Synchronization (Upload)

There are so many ways to upload files (`scp`, `rsync`, etc). I will leave this configuration up to the user.

In the future, there may be a "calendar server" that accepts uploads from curated users. These users could be given ssh keys to setup an auto-uploading scheme.
