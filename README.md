## binnit -- minimal pastebin clone in golang

That's just it. A minimalist, no-fuss pastebin clone server in
golang. It supports only two operations:

* store a new paste, through a POST request
* retrieve a paste using its unique ID, through a GET request

what else do you need? 

## WTF?

`binnit` serves pastes in the format:

    mypasteserver.org/abcdef1234567890

and stores them in a folder, one file per paste, whose filename is
identical to the paste ID. The unique ID of a paste is obtained from
the SHA256 of the concatenation of title, time, and content. Rendering
is minimal, on purpose, but based on a customisable template.

`binnit` is currently configured through a simple key=value
configuration file, whose name can be specified on the command line
through the option `-c <config_file>`. The configurable options are:

* server\_name  (the FQDN where the service is reachable from outside)
* bind\_addr (the address to listen on)
* bind\_port (the port to bind)
* paste\_dir (the folder where pastes are kept)
* templ\_dir (the folder where HTML files and templates are kept)
* max\_size (the maximum allowed length of a paste, in bytes. Larger
    pastes will be trimmed to that length)
* log_fname (path to the logfile)

## Why another pastebin?

There are hundreds of pastebin-like servers in the wild. But the
overwhelming majority of them is _overbloated_ software, depending on
lots of libraries/frameworks/tools, providing a whole lot of useless
features, and implying a useless amount of complexity. 

A paste server must be able to do two things, 1) create a new paste
and return its ID, and 2) retrieve an existing paste using its
ID. `binnit` does just and only these two things, in the simplest
possible way, without any external dependency. If you need more, then
`binnit` is not for you.

If you want to strip `binnit` down even further, you could consider
removing:

* sanity checks and error management
* logging
* the external configuration file
* code comments

> It seems that perfection is attained not when there is nothing more
> to add, but when there is nothing more to remove (Antoine de Saint
> Exupéry)


## LICENSE

`binnit` can be used, modified, and redistributed under the terms of
the GNU Affero General Public Licence, version 3 of the Licence or, at
your option, any later version. Please see the LICENSE.md file for
details.

