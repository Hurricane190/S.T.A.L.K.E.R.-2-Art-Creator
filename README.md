# S2 Art Creator 2.3.1

Create your own **Idle Screen**, **Loading Screen**, **Poster**, **main-menu video** and
**shader-loading music** mods for **S.T.A.L.K.E.R. 2: Heart of Chornobyl** - and change
the **text of the main menu** - no manual file editing, no converting, no renaming. Pick
the pictures, texts and soundtrack in the game you want to replace, press one button,
and copy the finished folder into your mods directory.

The window has three top-level tabs:

* **Image Edits** - everything that swaps a picture (idle screen, loading screens,
  posters, main-menu film).
* **Text Edits** - everything that swaps text inside the game (main-menu button
  labels).
* **Music** - replaces the looping track the game plays while it compiles shaders.
  You can preview the vanilla soundtrack and your own audio in the app.

The app also shows you, for every replaceable image and the soundtrack, **which mod is
currently winning in game** - useful when several mods touch the same posters.

A plain-text guide with install, use and uninstall steps is in `README_FIRST.txt`.

---

## Requirements

* Windows 10 or 11, 64-bit.
* **Nothing else** - no Python, no editor, no extra tools. Everything the app needs
  (including the texture encoder and the container packer) is inside this folder.
* S.T.A.L.K.E.R. 2: Heart of Chornobyl must be installed for the mods to have an effect
  and for the *in game* column to work.
* **RAD Video Tools** (free, from RAD Game Tools) is only needed if you want to convert
  your own movie file (`.mp4`, `.mov`, ...) into the Bink 2 format the game uses. The
  app never installs or bundles it - it only uses a copy you already have.
* The **Music** tab uses two bundled command-line audio tools (`wav2wem`, GPLv2, and
  `vgmstream`, ISC). Their licences and source links are in
  `tools\THIRD_PARTY_NOTICES.txt`.

---

## Installing the app

1. Extract the ZIP wherever you like, for example `D:\Games\S2ArtCreator`.
2. Double-click **`S2ArtCreator.exe`**.

That is it. The app never writes into the game folder and never changes your installed
mods - it only reads them to show you what is active.

> Tip: right-click `S2ArtCreator.exe` -> *Send to* -> *Desktop (create shortcut)* to get
> a desktop icon.

---

## Creating your first mod (7 steps)

### 1. Choose what to replace
Pick a top-level tab and then a section:

| tab | section | what you can replace |
|---|---|---|
| **Image Edits** | **Idle Screens** | 1 image - the screen shown while the game compiles shaders / starts up |
| **Image Edits** | **Loading Screens** | 41 images - the 21 zone loading screens and the 20 loading-art variants |
| **Image Edits** | **Posters** | 99 individual posters - 16 poster sets of 6 posters each, plus 3 single posters |
| **Image Edits** | **Main Menu Videos** | 6 videos - the 2 base-game campfire films and the 4 *Cost of Hope* DLC films |
| **Text Edits** | **Menu Text** | the 8 main-menu labels (Continue, New game, Load, Options, Mod browser, Credits, Quit, window title) |
| **Music** | **Shader Loading** | the looping track the game plays while it compiles shaders; the short logos stream is silenced automatically (preview the vanilla track and your own audio in the app) |

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

### 3. Main menu videos (Image Edits)

The main menu loops a **Bink 2** movie. Six films are supported:

| film | file in the game | used by |
|---|---|---|
| Theme 1 | `SII_BONFIRE_MENU_V1_4K_60fps.bk2` | base game |
| Theme 2 | `SII_BONFIRE_MENU_V2_4K_60fps.bk2` | base game |
| DLC theme 1-4 | `Seq_MainMenu_01..04_*.bk2` | *Cost of Hope* DLC |

> With the *Cost of Hope* DLC installed the menu normally plays the **DLC** film, so
> replace the matching DLC row - not the base-game row. The menu theme is switched
> with **TAB** in game.

* Click **Select video...** on the row you want to change. `.mp4`, `.mov`, `.wmv`,
  `.avi`, `.mkv`, `.webm` and ready-made `.bk2` files are accepted.
* The app shows a **preview still** of the film (extracted with RAD Video Tools) and
  the game's own information (resolution, frame rate, length).
* **Encode settings** per row: resolution (3840x2160 to match the game, 2560x1440,
  1920x1080, 32:9 5120x1440, or keep the source), quality, frame rate and
  *remove audio*.
* A `.bk2` file you already have is copied as-is - no conversion, no quality loss.

**RAD Video Tools**

* The app looks for `radvideo64.exe` in the usual install folders and in the registry.
  If it is not installed you get a dialog: *"RAD Video Tools is not installed. Would you
  like to download it now?"* - **Yes** opens the official download page
  (<https://www.radgametools.com/bnkdown.htm>), **No** lets you point the app at an
  existing copy.
* RAD Video Tools is **not** included in this app and is not redistributed with it.
  Bink video encoding for **commercial** use requires a licence from RAD/Epic Games.
* Without RAD you can still use pre-encoded `.bk2` files and all the other features.

**How the video package works**

The game plays these films as **loose files** in the game folder - Bink does its own
file I/O, so a movie cannot be shipped inside a mod container, and the *Cost of
Hope* films live in the DLC container, which mods cannot override. The package
therefore contains:

```
S2ACMV001\
    movies\...                your encoded Bink 2 film(s)
    install.bat               backs the original up and copies yours into the game
    uninstall.bat             restores the original film(s)
    readme.txt
```

* **The app never writes to the game folder.** You decide when to run
  `install.bat`; it stores the original file in `original_backup` first, and
  `uninstall.bat` puts it back.
* If the game is not in the usual place, run
  `install.bat "D:\SteamLibrary\steamapps\common\S.T.A.L.K.E.R. 2 Heart of Chornobyl"`.
* The menu theme is switched with **TAB** in game. If the film you replaced belongs
  to a theme you are not currently seeing, switch themes and it will show up.
* With the *Cost of Hope* DLC installed the menu normally shows the DLC film, so
  replace the matching DLC row (the *Cost of Hope* rows) rather than the base rows.

### 4. Menu text (Text Edits)

The main-menu buttons are localised strings inside
`Stalker2/Content/Localization/Game/<language>/Game.locres`. The app reads the
language you play in (or pick another one), shows the game's original text next to
an editable field, and writes a mod that contains only the changed strings.

* **The game font, size, colour and position stay exactly the same** - only the
  letters change. The font is never replaced.
* Texts must be a single line; keep them short or they will not fit the button.
* **Preview menu...** shows your texts in the game's own Oswald font before you build.
* The mod only contains the language you edited; other languages are untouched.
* The big *STALKER 2 / HEART OF CHORNOBYL* mark cannot be replaced by a mod: it
  needs a hard cook. The app therefore does not offer a title-logo replacement.

### Music (Music tab)

**Shader Loading** replaces the looping Wwise soundtrack the game plays while it
compiles shaders on the idle screen. The event also contains the short
logos/warnings track; when you pick a shader-loading track the app automatically
replaces that stream with silence, so your song starts once when the loop begins
(no double start, no overlap). The game's loading-state mix/filter on that loop is
part of the game and is not removed.

* The left card is the **vanilla soundtrack**: waveform, length and a **Play vanilla**
  / **Stop** button.
* Click **Select audio...** on the right, choose a file (`.wav`, `.mp3`, `.ogg`,
  `.flac`, `.m4a`, `.aac`, `.wma`, `.opus`, `.aiff` all work) and press
  **Play custom** to hear it. The app encodes it to a Wwise Vorbis `.wem` for the game.
* The blue **Music volume** (0-150%) and **Fade in/out** (0-10 s) controls apply to
  the replaced audio. The fade prevents an abrupt start and stop when the game wraps
  the loop. Both values are baked into the replacement file, so they need no
  game-side hooks.
* The **IN GAME** line tells you which installed mod currently wins for this event.
* Only the soundtrack media changes. The game keeps its own Wwise event, bank, loop
  and every other sound.
* **Rebuild old music mods.** Music mods created before 29 October 2026 could make the
  game abort at startup with `Serial size mismatch` for `SFX_UI_IdleScreen`, or hang
  when the track started; delete that mod folder from `~mods` and build it again with
  the current version. Mods that played as static/noise used the wrong Vorbis codebook
  UID and must also be rebuilt.
* Shader compilation only runs on the first launch or after a graphics driver update.
  The game loops the track, so any length works. To test a replacement on an existing
  install, clear the game's shader cache first.

### 5. Build the mod
Press the **FINISH** button (bottom right) of the section you are in:

* **Idle / Loading / Posters** - press **FINISH - CREATE MOD**, give the mod a name
  (the folder name is also used for the priority, so a plain name like `MyArt` is fine,
  see *Which mod wins* below), choose a folder to save it in (your Desktop is fine) and
  wait for **MOD READY**. It usually takes less than a minute.
* **Main Menu Videos** - press **FINISH - CREATE VIDEO MOD** and choose a folder. The
  app encodes the film(s) first (a 4K clip takes a few minutes) and then creates a
  folder named `S2ACMV001`, `S2ACMV002`, ... Keep that name!
* **Menu Text** - press **FINISH - CREATE MENU MOD**, give it a name and choose a
  folder. The folder contains the localisation mod.
* **Music** - press **FINISH - CREATE MUSIC MOD**, give it a name and choose a folder.
  The folder contains the three files `<Name>_P.utoc`, `<Name>_P.ucas`,
  `<Name>_P.pak` and a readme. The container name gives it normal `_P` priority.

The finished **picture** folder contains three files:

```
MyArt_P.utoc     the mod itself
MyArt_P.ucas     the textures
MyArt_P.pak      a small stub the game expects next to them
```

The finished **video / text** folder contains a `.pak` with the patched menu assets
and, for videos, your `.bk2` file(s).

### 6. Install the mod
1. **Close the game.**
2. Copy the whole mod folder into the game's mods directory:

```
<Steam library>\steamapps\common\S.T.A.L.K.E.R. 2 Heart of Chornobyl\Stalker2\Content\Paks\~mods\
```

   (for example `C:\Program Files (x86)\Steam\steamapps\common\S.T.A.L.K.E.R. 2 Heart of
   Chornobyl\Stalker2\Content\Paks\~mods\` - create `~mods` if it does not exist yet;
   the game also accepts the mod folder inside a subfolder of `~mods`)

### 7. Play
Start the game - your images and texts are in.

### Removing the mod again
Close the game, delete the mod folder from `~mods`, and the original game images,
videos and texts are back. Nothing else is left behind: the mods only *add* files,
they never replace game files.

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

* The window scales to your display: on high-DPI monitors the controls and previews render
  at native resolution (sharp, not blurry), and on very wide monitors - including 32:9
  ultrawide - the image list is kept at a readable width and centred instead of being
  stretched across the whole screen. Resize the window freely; the layout follows.
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
tools\                the texture encoder, container packer and audio tools
README.md             this file
appicon.ico           the icon
```

**Version 2.3.1.**

