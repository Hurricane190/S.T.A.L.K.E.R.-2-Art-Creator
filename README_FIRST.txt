S2 ART CREATOR 2.2 - READ ME FIRST
===================================


WHAT THIS APP IS
----------------
S2 Art Creator makes mods for S.T.A.L.K.E.R. 2: Heart of Chornobyl.

You can replace:
- the idle screen (the screen shown while shaders compile)
- the loading screens
- posters in the world
- the main menu videos
- the main menu text and title logo
- the music played while shaders compile

The app also shows which installed mod currently wins for each image and for
the music.


WHAT YOU NEED
-------------
- Windows 10 or Windows 11, 64 bit.
- S.T.A.L.K.E.R. 2: Heart of Chornobyl installed.
- Nothing else. Python is not needed. The app and its tools are in this folder.
- RAD Video Tools is only needed if you want to make your own menu video from
  an MP4, MOV, MKV or similar file. The app does not include RAD Video Tools.


HOW TO INSTALL THE APP
----------------------
1. Extract the whole ZIP to a folder, for example D:\Games\S2ArtCreator.
   Keep all files and folders together:
   S2ArtCreator.exe, _internal, resources and tools.
2. Double-click S2ArtCreator.exe.
3. If the app does not find the game, click "Game folder..." and select the
   folder that directly contains the "Stalker2" folder.


HOW TO UPDATE THE APP
---------------------
1. Close the old app.
2. Extract the new ZIP into a new folder, or replace the old app folder.
3. Your settings are kept in %LOCALAPPDATA%\S2ArtCreator.


HOW TO CREATE A MOD
-------------------
1. Choose a tab at the top: Image Edits, Text Edits or Music.
2. Choose a section.
3. Select your replacement file, or edit the text.
4. Press the FINISH button at the bottom right.
5. Give the mod a name and choose where to save it.
6. Wait for the "MOD READY" message.


HOW TO INSTALL A MOD IN THE GAME
--------------------------------
1. Close the game.
2. Copy the whole mod folder into:
   ...\S.T.A.L.K.E.R. 2 Heart of Chornobyl\Stalker2\Content\Paks\~mods
   Create the "~mods" folder if it does not exist.
3. Start the game.


HOW TO UNINSTALL A MOD
----------------------
1. Close the game.
2. Delete the mod folder from the "~mods" folder.
3. Start the game. The original game content is back.


MUSIC TAB NOTES
---------------
- The Music tab replaces the looping track played while the game compiles
  shaders.
- You can preview the vanilla track and your own audio before building.
- The game loops the track, so any length works.
- Shader compilation only runs on the first launch or after a graphics driver
  update. If your shaders are already compiled, clear the game shader cache
  to hear the new track.


VIDEO MOD NOTES
---------------
- A menu video mod contains install.bat and uninstall.bat, because the game
  reads menu videos as normal files.
- Close the game, run install.bat, then start the game.
- Run uninstall.bat to restore the original video.
- RAD Video Tools is required to convert your own video. It is not included.
- The menu theme is switched with TAB in game. With the Cost of Hope DLC
  installed, the menu normally plays the DLC video, so replace the matching
  DLC video.


WHERE SETTINGS AND CACHE ARE
----------------------------
- Settings: %LOCALAPPDATA%\S2ArtCreator\settings.json
- Preview cache: %LOCALAPPDATA%\S2ArtCreator\cache\music
- You can delete the cache folder at any time. It is created again when needed.


TROUBLESHOOTING
---------------
- "Tool not found" or "application folder looks incomplete":
  Extract the ZIP again and keep _internal and tools next to the EXE.

- "The folder already exists":
  Choose another mod name or another save folder.

- The game does not see the mod:
  Make sure the game was closed while you copied the mod, and that the whole
  mod folder is inside ~mods.

- A mod shows "INACTIVE" in the app:
  That mod was built with the wrong internal package root and the game ignores
  it. Use a mod built by this app.

- Menu video does not change:
  The menu theme is switched with TAB in game. With the Cost of Hope DLC
  installed, the menu normally plays the DLC video, so replace the matching
  DLC video.

- Menu text does not change:
  Menu text mods are made for one language. Build one for the language you
  play in.


HOW TO UNINSTALL THE APP
------------------------
1. Close the app.
2. Delete the folder you extracted.
3. Optional: delete %LOCALAPPDATA%\S2ArtCreator to remove settings and cached
   previews.

The app does not install anything into Windows and does not change the game by
itself.


VERSION
-------
2.2


PROJECT PAGE
------------
https://github.com/Hurricane190/S.T.A.L.K.E.R.-2-Art-Creator


THIRD-PARTY TOOLS
-----------------
The app includes separate command-line tools:
- retoc, repak, texconv, oo2core_9_win64.dll
- wav2wem (GPLv2)
- vgmstream (ISC)

See tools\THIRD_PARTY_NOTICES.txt and the licence files in the tools folder.
