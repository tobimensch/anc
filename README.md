anc is a shell script to make changing between frequently used directories
as easy and as natural as possible.

> Note: The current version was developed with and for bash. Nevertheless it might work out of the box on other modern shells, but is unlikely to work on a pure POSIX shell. This may get fixed in future versions. Patches, bug reports and help welcome.

Installation:
 1. Download anc.
 2. Put this line into ~/.bashrc 
    ```alias anc=". full/path/to/anc"```

> Note: Anchors are directories between which the user wants to jump back and forth.
anc saves the list of anchors in ~/.anc_list. The current default anchor is saved in ~/.anc .

Examples:
```
    # make the current directory the default anchor:
    $ anc s

    # go to /etc and then back to the default anchor:
    $ cd /etc; anc

    # go back to /etc :
    $ anc b

    # add another anchor :
    $ anc a /home/user/test

    # view the list of anchors (the default one has the asterisk):
    $ anc l
    (0) /path/to/first/anchor *
    (1) /home/user/test

    # jump to the anchor we added:
    $ anc j1
```

anc -h
```
Usage: anc [OPTIONS]

Changes directory to one of the previously set anchors.
Jumps to current default anchor with no options given.

First the user has to set one or more anchor directories
to jump between. See options (and --examples) below.

Note that for all short options like -s, -v and -b,
you can alternatively type s, v and b without the dash.

Likewise for long options like --clear or --version
you can type clear or version.

Options:
  -s DIR         Set DIR as default anchor. [default: current directory]
  -a DIR         Adds DIR to anchor list, but doesn't
                 set DIR as default anchor. [default: current directory]
  -r DIR         Removes DIR from anchor list. [default: current directory]
  -v             View current default anchor.
  -g TEXT        Compares anchor paths with text and jumps
                 to first match.
  -j NUM         Jump to anchor NUM in anchor list.
  -1             Jump to last anchor in anchor list.
  -b             Go back to previous directory.
  -l, --list     Print list of set anchors.
  --clear        Clear anchor list.
  --install      Install anc in bashrc.
  --config-help  Print configuration help.
  --examples     Print examples.
  -h, --help     Print this help message.
  --version      Print version information.
```

anc is licensed under the MIT license.

