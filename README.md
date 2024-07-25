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
git pull
git submodule update --recursive --remote --init --force
```

If you have [`make`](https://www.gnu.org/software/make/) available, you can run the above by simply running:

```
make
```

Alternatively, the script below will maintain shallow clones (depth=1) and checkout master:

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

The libretro-thumbnail server updates the thumbnails about once every two days on a cronjob. If you don't see updated files, append `?nocaches=CURRENTDATE` to have CloudFlare serve new content.

### .index Files

The .index files allow RetroArch to list the files available in the given directory. To build the .index files, run...

```
make index
make
```

## Image guidelines for contributors:
In order for the thumbnail repository to contain "archival quality" snaps (in-game screenshots) for each game:
  - Snaps should ideally represent characteristic art/sprites, environment, and/or action from the game.
  - Contributors should think of what screenshot a museum curator would pick for a museum exhibit about the game.
  - Contributors should think of what kind of picture the game's designers/artists would pick for the back of the game's box.

### Examples:
  - In a racing game: a good screenshot often will show the vehicle following the road.  Not crashed off the track with the camera aiming away from the upcoming road.
  - In a fighting game: a good snap screenshot will show the character sprites and at least one animation key frame, not a situation when the characters are off-screen or invisible.
  - In a scrolling shooter: some combination of clear player ship + clear background + enemies + some of the bullet style or explosions.
  - In a 3rd person action game: a good snap thumbnail will include some balance between the character and the environmental setting/style.  A less ideal snap thumbnail might be mostly filled by a single wall texture with the camera directly facing a bland wall.
  - 
## Credits

The art provided has many different sources. Thank you to many of the contributors and sites who have made this possible...

- [Screenshot(s) via MobyGames](https://mobygames.com)
- [Fandom](https://www.fandom.com)
