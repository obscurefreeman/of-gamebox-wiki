# Add local content

## File structure

This is the basic file structure of `local content`.

```
.
├─ lua/
|   └─ html/
|   |  └─ includes/
|   |     └─ your_local_game.html.lua
|   |     └─ your_multifile_local_game/
|   |        └─ index.html.lua
|   |        └─ script.js.lua
|   |        └─ style.css.lua
|   └─ ofmg_extensions/
|      └─ your_local_games_info.lua
└─ materials/
   └─ entities/
      └─ ofmg_games/
         └─ your_local_game.png
         └─ your_multifile_local_game.png
```

## Process HTML files

Since the Gmod Workshop doesn't allow `html` files to be uploaded, we can disguise it as a `Lua` file and load it with the HTML Loader.

- If there is only one `html` file, change its suffix to `.html.lua` and place it in the `lua/html/includes/` folder.

- If it has multiple files, you can create a new folder, here take `your_multifile_local_game` as an example, put all the `html`, `js`, `css` files into this folder, and then open the `html` file with `vsc` or notepad (if you don't have `vsc`), and change the paths of `js` and `css`.


### Modify the path of `css`

```html
<link rel="stylesheet" href="your_multifile_local_game/style.css">
```

### Modify the path of `js`

```html
<script src="your_multifile_local_game/script.js"></script>
```

After modifying the files, don’t forget to change the suffix of the `css` file to `css.lua` and the suffix of the `js` file to `js.lua`.

## Fill in extension information

Create a `lua` file in the `ofmg_extensions` folder, and try to name it with a unique name to avoid conflict with other people's extensions. In this file, create a new table for `OFMGCustomExtensions` and give it a name. Likewise, give this table a unique name.

Only **one** HTML file.

```lua
OFMGCustomExtensions["Your Local Game"] = {
    ["Type"] = "Game",--Its type is local game.
    ["Info"] = "your_local_game.html",--Location of the game.
    ["Image"] = "your_local_game",--Name of the image. Please put the 128*128 preview image in the entities/ofmg_games folder.
    ["Compatible"] = true,--Is it compatible with Gmod without CEF installed?
}
```

Contains **multiple** HTML files.

```lua
OFMGCustomExtensions["Your Multi-file Local Game"] = {
    ["Type"] = "Game",---Its type is local game.
    ["Info"] = "your_multifile_local_game/index.html",--Location of the game.
    ["Image"] = "your_multifile_local_game",--Name of the image. Please put the 128*128 preview image in the entities/ofmg_games folder.
    ["Compatible"] = true,--Is it compatible with Gmod without CEF installed?
}
```
