# libretro-thumbnails

Thumbnails for [RetroArch](http://retroarch.com), split into individual repositories to ease maintenance.

## Install

Check out the repository, with all submodules, into RetroArch's thumbnails directory:

```
cd ~/.config/retroarch
git clone --recursive --depth=1 http://github.com/libretro-thumbnails/libretro-thumbnails.git thumbnails
```

## Update

To bring in the latest thumbnails across all systems, use:

```
git pull --recurse-submodules
git submodule update --remote --recursive
```

Or by using the script which will maintain shallow clones (depth=1) and checkout master:

```
sh update_modules.sh
```

## Usage

- Thumbnails are installed into RetroArch config's `thumbnails` directory
- There are three types of thumbnails:
  - `Named_Snaps` are in game snapshots
  - `Named_Titles` are title screen snapshots
  - `Named_Boxarts` are the boxes or covers for games
- Thumbnails follow the following naming convention:
    ```
    thumbnails/Playlist Name/Named Type/Game Name.png
    ```
- The following characters in playlist titles must be replaced with _ in the corresponding thumbnail filename:
    ```
    &*/:`<>?\|"
    ```
- Images must be `.png` format
- Image resolution guidelines:
  - Images with native width larger than 512px should be scaled down to 512px wide
  - Images with native width of 512px or less should be added as-is
- Substitute promotional material is acceptable when no official boxart is available
- Use [libretro-thumbnails-check](https://github.com/RobLoach/libretro-thumbnails-check) to check for missing thumbnails

## Testing

To check for files with invalid file names, use the following command....

``` bash
find . -name '*[&\*:`<>?\\|"*]*'
```

## Thumbnail Server

The libretro-thumbnail server provides two functions...

### .index Files

The .index files allow RetroArch to list the files available in the given directory. To build the .index files, run the following command...

```
make index
```

## Credits

The art provided has many different sources. Thank you to many of the contributors and sites who have made this possible...

- [Screenshot(s) via MobyGames](https://mobygames.com)
- [Fandom](https://www.fandom.com)
