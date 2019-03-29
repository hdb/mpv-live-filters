# mpv-live-filters


A lua script for mpv that lets you add, remove, toggle and set shortcuts for ffmpeg video filters during mpv playback. Designed to easily test ffmpeg's command line filters without having to start and stop `ffplay` commands or use a bloated NLE.

This script is based on James Ross-Gowan's [mpv-repl](https://github.com/rossy/mpv-repl) and Olivier Perret's [mpv-scripts](https://github.com/occivink/mpv-scripts), tuned specifically for streamlined use of filters. 

<p align="middle">
    <img src="assets/example.gif" width="50%" /> 
</p>

## Setup 

Place lua file in mpv's scripts directory. In Linux this will be `/home/user/.config/mpv/scripts/` mpv loads all scripts in this directory when it starts. 

Alternatively, specify the path to this script from the command line with `mpv video.mkv --script /path/to/live-filters.lua`. 


## Usage

Default key-bindings:

- `` ` ``           activate REPL for filter inputs (changes key-bindings)
- `ctrl+z`          undo last filter
- `ctrl+shift+z`    re-do filter
- `ctrl+x`          toggle filters on/off
- `ctrl+shift+x`    clear all filters

REPL mode key-bindings:

- `esc`             exit REPL input mode
- `tab`             autocomplete from list of ffmpeg filters
- `enter`           add vf filter
- `alt+enter`       set vf filter (removes current filters)

With the REPL active, type the vf filter options with any parameters. Multiple filters can be entered either all at once or with separate commands in sequence. 

Example:

    > tblend=c0_mode=difference,eq=contrast=2    

is equivalent to

    > tblend=c0_mode=difference
    > eq=contrast=2

is equivalent to 

    mpv video.mp4 -vf tblend=c0_mode=difference,eq=contrast=2


See source for details on default text-entry key-bindings for REPL -- they should be straightforward (i.e., `home` to beginning of line, `up` to go to last entered text, etc.). 

In REPL mode, most key-bindings that use alt/ctrl/super modifier keys continue to work (e.g., `ctrl+z` for undo filter), but key-bindings that do not are disabled so that it is possible to enter text.

## Shortcuts

mpv-live-filters supports shortcuts for commands. Simply copy the shortcut and the command into [live-filters.lua](https://github.com/hdbhdb/mpv-live-filters/blob/1d4f571ec68ab2a9d8667cbcedcdb8145f68baf0/live-filters.lua#L112-L121). 

## License

MIT