# fzf-player
CLI music player wrapper with fuzzy search

### Control Interface
![][1]

### Create Playlist
![][2]

## Usage

```sh
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
```

***NOTE***: `.fdignore` file in Music folder is used to exclude directories and
files during `fd` search.

## Audio Format Support

It finally depends on the back end player. From the front-end's perspective,
this wrapper currently respect `wav`, `ape`, `flac`, `m4a`, `mp3`, `ogg`

***NOTE***
To review all the file types, via file extension, under your music library:

```sh
fd -t file | awk -F "/" '{n=split($NF, a, "."); print a[n]}' | sort | uniq
```

## Requirements

- a music player support CLI, e.g. mplayer
- [fzf][3], A command-line fuzzy finder
- [fd][4], A simple, fast and user-friendly alternative to 'find'

### Mplayer Support

#### Enable single track repeat

Add key bindings in `~/.mplayer/input.conf`:
```ini
# l: inf, 1, 2, 3...; L: ..., 3, 2, 1, inf, off
l loop 1
L loop -1
```

[1]: <Resources/screenshot.png> "screenshot"
[2]: <Resources/demo.gif> "demo"
[3]: <https://github.com/junegunn/fzf> "fzf"
[4]: <https://github.com/sharkdp/fd> "fd"


[//]: # (vim: tw=78:ts=8:sts=4:sw=4:noet:ft=markdown:norl:)
