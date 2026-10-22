# S2 Art Creator 1.0

Create your own **Idle Screen**, **Loading Screen** and **Poster** mods for
**S.T.A.L.K.E.R. 2: Heart of Chornobyl** - no manual file editing, no converting, no
renaming. Pick the images in the game you want to replace, choose your own picture for
each, press one button, and copy the finished folder into your mods directory.

The app also shows you, for every replaceable image, **which mod is currently winning in
game** - useful when several mods touch the same posters.

---

## Requirements

* Windows 10 or 11, 64-bit.
* **Nothing else** - no Python, no editor, no extra tools. Everything the app needs
  (including the texture encoder and the container packer) is inside this folder.
* S.T.A.L.K.E.R. 2: Heart of Chornobyl must be installed for the mods to have an effect
  and for the *in game* column to work.

---

## Installing the app

1. Extract the ZIP wherever you like, for example `D:\Games\S2ArtCreator`.
2. Double-click **`S2ArtCreator.exe`**.

That is it. The app never writes into the game folder and never changes your installed
mods - it only reads them to show you what is active.

> Tip: right-click `S2ArtCreator.exe` -> *Send to* -> *Desktop (create shortcut)* to get
> a desktop icon.

---

## Creating your first mod (5 steps)

### 1. Choose what to replace
At the top of the window pick a category:

| category | what you can replace |
|---|---|
| **Idle Screens** | 1 image - the screen shown while the game compiles shaders / starts up |
| **Loading Screens** | 41 images - the 21 zone loading screens and the 20 loading-art variants |
| **Posters** | 99 individual posters - 16 poster sets of 6 posters each, plus 3 single posters |

### 2. Choose your picture
Every row shows the game's original picture on the left. Click **Select file...** on the
row you want to change and pick your own image (`.png`, `.jpg`, `.jpeg`, `.webp`, `.bmp`,
`.tif` all work).

* Your picture is **centre-cropped** to the game's resolution automatically, so the
  composition stays where you want it. Larger pictures look better.
* **Posters work one by one.** A poster set of six is shown as six separate rows; you can
  replace just one poster of a set. The other five keep the original game artwork, and the
  poster set stays complete and correct in game.
* Rows you do not touch keep the original game image.

### 3. Build the mod
Press **FINISH - CREATE MOD** (bottom right):

* give the mod a name - the folder name is also used for the priority, so a plain name
  like `MyArt` is fine (see *Which mod wins* below),
* choose a folder to save it in (your Desktop is fine) - the app creates a folder named
  after the mod,
* wait for the green **MOD READY**. It usually takes less than a minute.

The finished folder contains three files:

```
MyArt_P.utoc     the mod itself
MyArt_P.ucas     the textures
MyArt_P.pak      a small stub the game expects next to them
```

### 4. Install the mod
1. **Close the game.**
2. Copy the whole `MyArt` folder into the game's mods directory:

```
<Steam library>\steamapps\common\S.T.A.L.K.E.R. 2 Heart of Chornobyl\Stalker2\Content\Paks\~mods\
```

   (for example `C:\Program Files (x86)\Steam\steamapps\common\S.T.A.L.K.E.R. 2 Heart of
   Chornobyl\Stalker2\Content\Paks\~mods\` - create `~mods` if it does not exist yet;
   the game also accepts the mod folder inside a subfolder of `~mods`)

### 5. Play
Start the game - your images are in.

### Removing the mod again
Close the game, delete the `MyArt` folder from `~mods`, and the original game images are
back. Nothing else is left behind: the mod only *adds* files, it never replaces game
files.

---

## Which mod wins?

If several mods replace the same image, the game decides by the priority encoded in the
container file name:

| file name | priority |
|---|---:|
| `MyArt` (no `_P`) | 3 |
| `MyArt_P` | 103 |
| `MyArt_20_P` | 103 + 100 x 20 = 2103 |

Higher priority wins: `MyArt_20_P` beats `MyArt_P`, which beats `MyArt`. Only when two
containers have the **same** priority does the order they are mounted in decide - the
folder whose name comes first alphabetically is mounted last and therefore wins.

The app's **IN GAME** column shows exactly that: the replacement the game really uses.
**Details...** explains the decision and lists every container that touches the image.
Two more states you may see:

* **Vanilla** - no installed mod replaces this image.
* **INACTIVE** - a mod does contain this image, but the game ignores it. That happens when
  the mod's textures were not cooked with the game's own package root (`/Game/`), which
  older or third-party mods sometimes get wrong. The app tells you the expected root so
  you can fix or avoid such a mod.
* **Unknown** - the winner cannot be determined safely (for example two containers with the
  same priority and the same path). The app refuses to guess instead of showing the wrong
  picture.

---

## Notes

* The app writes **only** into the folder you pick when saving a mod. It never modifies
  game files, and it only *reads* the installed mods (previews are decoded in a temporary
  folder that is deleted afterwards).
* Your settings (the remembered game folder) are stored in
  `%LOCALAPPDATA%\S2ArtCreator\settings.json`. If the game is not found automatically,
  click **Game folder...** and select the folder that directly contains `Stalker2`.
* Every image is encoded in the exact format and resolution the game expects, and the
  finished container is verified before you get it.
* When you replace only some posters of a set, the untouched posters are rebuilt from the
  bundled full-resolution vanilla artwork, so the set stays complete in game.
* Only the three supported categories are exposed. Murals, photo walls, scheme boards and
  mosaics are deliberately not part of this app.

## Troubleshooting

| message | what to do |
|---|---|
| *Tool not found* / *The application folder looks incomplete* | the folder was extracted incompletely - extract the ZIP again, keeping `tools\` and `_internal\` next to the exe |
| *The folder already exists* | pick another mod name or another destination when saving |
| The game is not found | click **Game folder...** and select the folder containing `Stalker2` |
| The **IN GAME** column stays *Vanilla* | the mod is not in `~mods`, or the game was running while you copied it, or the container is marked *INACTIVE* (see **Details...**) |
| Nothing changes in game | make sure the whole mod folder (all three files) is in `~mods` and that the game was closed while you copied it |

---

## What is in this folder

```
S2ArtCreator.exe      the application
_internal\            the bundled Windows runtime (no Python needed on your PC)
resources\            the game's pristine texture templates and preview images
tools\                the texture encoder and container packer used while building
README.md             this file
appicon.ico           the icon
```

**Version 1.0.**
