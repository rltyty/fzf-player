# fzf-player
A simple CLI music player wrapper with fast search

### Screenshot
![][1]

### Demo
![][2]

# Usage

    Usage: fzf-player: [-dgh] [-p playlist] [-l music_library]

    where
        -d              debug mode
        -p playlist     just play the list without search
        -l music_lib    directory where to search music files
        -g              gui mode
        -h              show this help

    When "-p playlist" is given, the utility just play the list.

    Press `<CTRL-q>` to quit the command
    Press `<TAB>`/`<SHIFT-TAB>` for multiple selection.
    Press `<Enter>` to confirm play queue

NOTE: .fdignore file in Music folder is used to exclude directories and
files during `fd` search.

# Audio format support

This finally depends on the backend player. From the frontend's perspective,
the script currently respect `wav`, `ape`, `flac`, `m4a`, `mp3`, `ogg`

NOTE:
It's easy to review all the file types under your music library by:

    fd -t file | awk -F "/" '{n=split($NF, a, "."); print a[n]}' | sort | uniq

# Requirements

- a music player support CLI, e.g. mplayer
- [fzf][3], A command-line fuzzy finder
- [fd][4], A simple, fast and user-friendly alternative to 'find'

NOTE:
`Luit` is used to translate character set and solve the "garbled text"
problem met when visit east Asian BBS. On Debian 11, the default luit(1.1.1)
installed as a part of x11-utils is too old, may cause unexpected issues
like segmentation fault. Build and install from luit 2.0 [source][1]. On
Debian 12, the default luit installed is v2.0, so no need to build from
source.

[1]: <Resources/screenshot.png> "screenshot"
[2]: <Resources/demo.gif> "demo"
[3]: <https://github.com/junegunn/fzf> "fzf"
[4]: <https://github.com/sharkdp/fd> "fd"


[//]: # (vim: tw=78:ts=8:sts=4:sw=4:noet:ft=markdown:norl:)
