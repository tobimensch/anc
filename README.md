anc is a shell script to make changing between frequently used directories
as easy and as natural as possible.

> Note: The current version was developed with and for bash. Nevertheless it might work out of the box on other modern shells, but is unlikely to work on a pure POSIX shell. This may get fixed in future versions. Patches, bug reports and help welcome.

Installation:
 1. Download anc.
 2. Put these two lines into ~/.bashrc 
    ```alias anc=". /absolute/path/to/anc"
       anc --init-completion```

> Note: Anchors are directories between which the user wants to jump back and forth.
anc saves the list of anchors in ~/.anc_list. The current default anchor is saved in ~/.anc .

Examples:
```
Examples:
    # make the current directory the default anchor:
    $ anc s

    # go to /etc, then /, then /usr/local and then back to the default anchor:
    $ cd /etc; cd ..; cd usr/local; anc

    # go back to /usr/local :
    $ anc b

    # add another anchor:
    $ anc a $HOME/test

    # view the list of anchors (the default one has the asterisk):
    $ anc l
    (0) /path/to/first/anchor *
    (1) /home/usr/test

    # jump to the anchor we just added:
    # by using its anchor number
    $ anc 1
    # or by jumping to the last anchor in the list
    $ anc -1

    # add multiple anchors:
    $ anc a $HOME/projects/first $HOME/projects/second $HOME/documents/first

    # use text matching to jump to $HOME/projects/first
    $ anc pro fir

    # use text matching to jump to $HOME/documents/first
    $ anc doc fir

    # add anchor and jump to it using an absolute path
    $ anc /etc
    # is the same as
    $ anc a /etc; anc -1

    # add anchor and jump to it using a relative path
    $ anc ./X11 #note that "./" is required for relative paths
    # is the same as
    $ anc a X11; anc -1

    # using wildcards you can add many anchors at once
    $ anc a $HOME/projects/*
    
    # use shell completion to see a list of matching anchors
    # and select the one you want to jump to directly
    $ anc pro[TAB]
```

anc -h
```
Usage: anc [OPTIONS]
       anc ( <NUM> | <TEXT> )
       anc <PATH>

Changes directory to one of the previously set anchors.
Jumps to current default anchor with no options given.

First the user has to set one or more anchor directories
to jump between. See options (and --examples) below.

Note that for all short options like -s, -v and -b,
you can alternatively type s, v and b without the dash.
(-1 is an exception to the rule, because 1 is for jumping
to the second anchor in the list.)

If the first parameter is a number and there are no other
parameters, it is equivalent to:
  anc -j NUM

If the first parameter is text and it doesn't conflict with
any of the options, it is equivalent to:
  anc -g TEXT...

If the first parameter is a number and there are multiple
parameters, it is equivalent to:
  anc -g TEXT TEXT...

If the first parameter is either an existing absolute path
or an existing relative path starting with ./ or ../, anc will
add it to the anchors list and jump to it immediately.

Options:
  -s DIR         Set DIR as default anchor. [default: current directory]
  -a DIR         Adds DIR to anchor list, but doesn't
                 set DIR as default anchor. [default: current directory]
  -r DIR         Removes DIR from anchor list. [default: current directory]
  -v             View current default anchor.
  -g TEXT        Compares anchor paths with text and jumps
                 to first match.
  -j NUM         Jump to anchor NUM in anchor list.
  -i             Interactive anchor jumping.
  -1             Jump to last anchor in anchor list.
  -b             Go back to previous directory.
  -l, --list     Print list of set anchors.
  --clear        Clear anchor list.
  --sort         Sort all anchors by path.
  --install      Install anc in bashrc.
  --config-help  Print configuration help.
  --examples     Print examples.
  -h, --help     Print this help message.
  --version      Print version information.

Project <http://github.com/tobimensch/anc/>.
```

anc is licensed under the MIT license.

