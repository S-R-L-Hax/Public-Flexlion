## Official website: https://flexlion.github.io/
### Flexlion is Splatoon 3 mod menu delivered you from the developers(well, there’s only 1) of Reinkify for Splatoon 2.
# IF THE GAME/MENU STOPS WORKING, try the following:
1. Make sure you are using the latest game update and menu update.
2. If the game is crashing on boot, delete flexlion3 folder on your sd card, reextract the latest rar and open the game again.
3. It also might be possible that if a game update recently released, Flexlion hasn’t been updated yet, usually a Flexlion update releases in a few hours after the new game update.

# TO INSTALL FLEXLION
First you need to hack your switch(find a tutorial elsewhere). Then, simply extract the Flexlion rar onto the root of your sd card (or the virtual sd card folder if you are using an emulator). (For dummies, extract means take out the contents from inside the zip (in this case, atmosphere and flexlion3 folders) and put them onto the sd)

# Menu Controls:
- L - Open Menu/Section/Toggle Module
- L Stick - Close Menu/Section
- Up/Down Dpad - Select Section/Module when in the menu
- Right/Left Dpad - Open a module’s extra settings

# BEFORE USING:
USE FLEXLION ONLINE AT YOUR OWN RISK. I AM NOT OBLIGED TO REPLACE YOUR SWITCH IF YOU GET BANNED FOR USING THIS MOD ONLINE AND I DO NOT GUARANTEE YOU WILL NOT GET BANNED! It’s worth noting that as of 5.0.0, there aren’t any parts of the anticheat that are known that could detect Flexlion, and there are no registered cases of bans. This could change in the future as Nintendo has already tried implementing anticheat measures specifically against Flexlion in 4.0.0 update (which were pretty stupid and latest build is not detected by  them). 

Please also note that Flexlion does not disable anticheat measures for detecting code patches, param edits and other things, it only sidesteps them. If you try to use any detectable code patches or param edits together with Flexlion, you’ll still get detected by the anticheat .

## FEATURES THAT ARE NOT SAFE ONLINE(May get you BANNED):
- Anything with [UNSAFE] in the name or anywhere 
- Loading pchtxt/ips patches
- VideoModule

## Loading a pchtxt into the menu [DO NOT USE THIS FEATURE ON SYSNAND, USING THIS WILL GET YOU BANNED ONLINE]:
You can load a pchtxt and toggle ips patches live inside Flexlion. To do this, place your pchtxt as /flexlion3/patches.pchtxt on your sd card. Note that some patches, such as splatfest mode from coxxs' public patches, require a game reboot, but most of them should work fine without that. DO NOT USE IPS PATCHES ON SYSNAND OR YOU WILL GET BANNED ONLINE.

## Custom Collision Mods
Flexlion allows importing custom collision in the form of .obj files to override the games bphsh(phive) files. THIS FEATURE IS NOT ONLINE SAFE. To use, you need to make a folder with any name you want in /flexlion3/collision/, where you must put a config.json and other files referenced by it, such as your .obj file(s) that will be used for collision. An example collision mod is provided in the mod's downloads. 
In the config json you must specify "collision", where you can add one or multiple entries for collision overrides. each entry must have the path of the collision you want to override as the key(For example, "Phive/Shape/Dcc/TestField0001.Nin_NX_NVN.bphsh", you can find this path in the Phive Shape config inside the actor pack of the actor collision of which you would like to override, yes that includes map models, they usally start with Fld_) and in the value you specify "obj_path", where you specify the path to the .obj file relative to the folder of your mod (for example, even if your mod root directory would be /flexlion3/collision/testmod/ and the obj file was /flexlion3/collision/testmod/Fld_Hiagari03.obj, you'd write "/Fld_Hiagari03.obj").  
Inside the collision entry, if you would like to specify different collision material properties, you may also add a "materials", where each entry can have an arbitrary material name as the key (you can call it anything, Water00 would work and SkibidiRizz would work too), but that key must match the material name you use in your .obj file (**material name, not mesh name). A material can have "mat_name", which is a material name string(only affects effects/sounds), "mat_flags", which is an array of material flag strings, and "col_disable_flags", which is an array of flags to disable collision for certain objects. You can see the values available for these inside /flexlion3/fxconfig,json. You can also use "fx_preset" (one string) that will load a preset of certain flags/material name, available options are either "Water" or "Fence"(grates/squid falls through).  
Please note that if your collision is abnormally large, it may not work, you shouldnt use things like map display models directly for their collision, you will  need to decrease the quality first. You can convert a kcl file into a .obj and it should work fine(you will need to specify material flags if you want the materials to behave correctly though).  
  
Due to Switch Toolbox issues, even though things are paintable the paint is invisible on any exported bfres10 models (it is visible on the minimap though and you can swim in it). I've made a script that automatically fixes the map model for you (please note that you have to use it every time you export a model from toolbox, since toolbox will break the model every time), the script is available in mod downloads.  
  
*paintable model materials must have blitz_paint_type NOT as default value, usually it's 1 idk if theres any other available values (i recommend to find a material that already has it as 1), you should also set Paintable in user data to True. Unpaintable model materials must have blitz_paint_type as (i also recommend finding a mat thats already like that) and Paintable in user data set to False.  
  
### To use paintability fixer script: 
1. Either build yourself or there is already a built version in BfresLibrary.Test/bin/Release/net6.0/ 
2. Take the bfres.zs file exported from toolbox and decompress it (for example, you can actually open it with winrar), and put the decompressed file in the folder with the .exe
3. In the folder with the .exe, open cmd and write BfresLibrary.Test.exe FileName.bfres 
OR
3. Drag and drop the bfres onto BfresLibrary.Test.exe
4. If all goes well and there are no errors in the command line, you should get a FixedModel.bfres file. 
5. Compress the FixedModel.bfres file back into zstd (you can use toolbox for this, it wont break anything, just open toolbox, on top bar press Tools->compression->zstd->compress) also make sure 
(*if you were previously using paint_workaround patch for your map, you can now disable it since it is no longer needed)

You can also specify a "map_patches" in your config.json (separate entry from "collision", check example collision mod for reference), there you can add a list of map patches entries (key must be internal map name same as in RSDB, for instance "Vss_Hiagari04"), if the paintable area of your map is very big and your game ends up crashing sometime after the match started, specify "extend_col_heap" : true to automatically apply a code patch while the map is loaded that will increase paintmgr heap size and fix the crash.  
If you have a lot of collision mods installed and your game ends up crashing on boot(flexlion parses your .obj files on game boot) because you didnt have enough ram, you can edit "heap_size" in /flexlion3/fxconfig.json to a higher number(default is 20mb).  
  
## Texture/Shader Replacement Mods
You can also create and share texture/shader replacement mods using Flexlion. An example mod (made by NachoL_) is linked as a downloadable file. To install a mod like this you need to put the mod folder inside /flexlion3/mods/ on your sd card (you have to create "mods" folder inside flexlion3 folder on your sd card).  
  
To create a mod like this, youll need to create a mod config. it has to be a file named config.json inside your mod folder. it should be laid out something like any of the config.json in the example mods.  
  
The file directories are relative to the mod directory so all the paths should be the paths as if your mod directory was root. [!] bftex textures are supposed to be in the dimensions(Width and Height) and the same format inside toolbox, in some cases you'll need to use external converters other than toolbox to convert textures to astc first and then import them to toolbox and export as bftex if the texture you're targeting was displayed as astc inside toolbox [!]  

## Shader Mod Creation Guide:

### To create a shader mod you have to do the following:

1. Dump the shader (later you will be able to using some thing Killz is working on maybe itll be in toolbox, as of rn refer to guide later on this page) 
2. Decompile it with decompiler script in downloads 
3. Edit the decompilated shader. If you need to, you can also utilize Flexlion's helper uniform that is avaible on Replacement Shaders. 
4. Make sure you set the correct extension (.frag for fragment and .vert for vertex) and compile it with Flexlion shader compiler 
5. Make a shader mod according to the flexlion mod format (stated above).

### To use Flexlion shader compiler you have to:

1. Install flexlion first 
2. Place the shader source code files into a folder on your sd card (by default it is /flexlion3/compiler/src but you can put them to any folder and choose it in the compiler) 
3. Extract the zip to title id folder of the game you want to run this over (you have to delete any exefs mods you have installed for it if you do). Preferably Splatoon 3 because if it is not, you will have to also take sdk from Splatoon 3's exefs and put it into the exefs folder for the compiler. 
4. Obtain a glslc binary, rename it to subsdk0 and put it into the exefs folder for the compiler. Old glslc may not work, from my experience glslc from latest mario party game works. To get it from mario party for instance, it is one of the subsdks, you can determine which one by either checking in ida or just trying putting different ones for the compiler to use and checking if it works (you have to reboot the application if you want to load the subsdk). 
5. In the application, if needed select input and output directories, then press A. Logs and errors will be output on screen and also saved to flexcompiler.txt on your sd card.  
If you want to dump game shaders from inside flexlion, you can do so by searching them by fragment shader, youll have to use this for now till you can get a model's shaders with toolbox. They will be saved to /flexlion3/shadertest. To use, enable SHADER DEBUG in "Show Debug Info" in Other Section. After enabling it, some text will appear in top left corner. Press X and you should see weird stuff happening, dont panic. This is binary search mode made to find shaders more easily. At first, all shaders are selected. To narrow down the area of the search, press A, which will cut the size of the block of selected shaders by 2. If you see that your shader is no longer affected, press up, which will make you go to the next block of the currently selected size. Once your target shader is affected again, cut the area again. Repeat this till you only have 1 shader selected (will take like 20 seconds once you understand how this works). In top left, the hash of the fragment shader will be displayed. Press A and the shader will be saved to /flexlion3/shadertest with all the other stages it has. Then you can use the decompiler script to transform it into compileable code.  
  
Shader decompiler script will take shader bytecode and control and produce code compileable for nvn with Flexlion shader compiler. you have to provide it ryujinx shadertools, inside the script set SHADERTOOLS_DIR as path to Ryujinx's shadertools (you can just build ryujinx and set it as path to ryujinx's build directory, use this commit)  

## Keyboard/Mouse Controls

keyboard/mouse config is located in /flexlion3/FxKbmConfig.json. For format see the file.
You can map the following buttons:  

MouseLeft MouseRight MouseMiddle MouseExtra1 MouseExtra2
A B C D E F G H I J K L M N O P Q R S T V U W X Y Z 1 2 3 4 5 6 7 8 9 0 Escape Backspace Tab Space Minus Plus CapsLock F1 F2 F3 F4 F5 F6 F7 F8 F9 F10 F11 F12 RightArrow LeftArrow DownArrow UpArrow NumPadDivide NumPadMultiply NumPadSubtract NumPadAdd NumPadEnter NumPad1 NumPad2 NumPad3 NumPad4 NumPad5 NumPad6 NumPad7 NumPad8 NumPad9 NumPad0 LeftControl LeftShift LeftAlt RightControl RightShift RightAlt

## Flexlion Save Editor

There is also a save editor, which can be used with flexlion without using any additional applications for dumping/injecting save. PLEASE NOTE THAT EDITING YOUR SAVE CAN GET YOU **BANNED**, MOREOVER SOME THINGS WILL NOT APPLY IF YOU TRY TO USE THE SAVE ONLINE (FOR INSTANCE, WEAPONS/GEAR/GEAR ABILITIES/NAME/MONEY ETC WILL BE RESET IF YOU CONNECT TO THE INTERNET). Plaza post printer is probably safe, but i give no gurantees. To use the save editor with flexlion cloudsave, login with your discord account on https://flexlion.github.io/ , then in the Account Section press get fxtoken.epic and put that into /flexlion3/ folder on your sd card. Then, again on the same website in the Account Section press "Enable CloudSave". Now, when you launch the game your save will be uploaded to the server (or when the game saves while you play). When you want to edit your save, first close the game, then in the save editor, press "Use Flexlion Cloudsave", which will load the cloudsave into the editor, after you're done editing, press "Save to Flexlion Cloudsave". Then, you can boot your game and changes should automatically be applied.
Note by **kirakira**:  
The Flexlion save editor hasn't been working for me lately. Also the discord login is dead. @nvnprogram recenttly merged a lotta PR on the website's github page including some changes to the save editor which adds the 10.X.X weapons and 10 stars, but it still doesn't work for me.

## Music Changer

Cstm Music in Other section. This is wip version so default values and/or configs may be subject to change. Example music mod format is shown on gamebanana page.   

Currently, the way it works is you can place a folder of audio (wav, mp3, flac) files to /flexlion3/music/playlist/, and it will be a playlist. You can also have custom Last1min(Now Or Never), StartDemo, Result_Win and Result_Lose audio, check example music mod for more info.  

By default, all audio files will loop from start to end (unless youre not in Gamemode mode, then it will ignore loop and start playing next song) and use -10.64db volume. You can have json configs that will set an audio's Volume, Pitch, Loop Start and End Points.  (but you do not have to have a json config). If your audio file is CoolAudio.extension, name for json is CoolAudio.json. Audio folders can also have a default.json, which would contain the default values that can be overridden by individual audio configs (for example if both configs have an entry "Volume", the one from the individual audio config will be used, however if only one of them has some entry, that entry will also be used, otherwise default preset value is used).  

### Example config:
{  
  "VolumeDB": 13.5,  
  "Pitch": 0.85,  
  "Loop Start": "00:48:05",  
  "Loop End": "01:20"  
}  

Volume: for volume you can have either "Volume" (float value, for example 0.0 meaning 0%, 1.0 meaning 100%, 0.5 meaning 50% etc., not capped at 1.0, for example  

{  
  "Volume": 0.8  
})  
or "VolumeDB" (float value of volume in decibells, for example -10.64, which is the default value if no Volume is set by the config.)  
If neither volume is present in config or config isnt present, default value of "VolumeDB": -10.64 is used.  
Pitch: float value that defines audio pitch, should be self explanatory  
Loop Start/End - Loop timestamps, you can use either format Minutes:Seconds:Centiseconds (Centiseconds must be exactly 2 digits long, for example 01, and are 1/100th of a second), Minutes:Seconds:Milliseconds(Milliseconds must be exactly 3 digits long, for example 001, and are 1/1000th of a second) or Minutes:Seconds. If Start is not present, 0 is used, if End is not present, audio length is used.  

### Example config

{  
    "Loop Start": "00:48:05"  
}  

Volume = -10.64db = 0.086 (default)  
Pitch = 1.0 (default)  
Loop Start = 00:48:05  
Loop End = End Of Song  

## VideoModule
Module that renders an arbitrary video as ink on the floor at LobbyVersus  
**[DO NOT USE VideoModule ONLINE, I do not gurantee your game will be stable if you use this, as at the very least it uses a lot of ram if you enable it at least once]**  

To run it, you need to first get and place multimedia nso of sufficiently close sdk version in your exefs folder (you can get it as subsdk0 from animal crossing. Make sure you rename it to subsdk8(or any subsdk1-9) before putting it in /exefs/subsdk123456789 the reason you can't use subsdk0 is because Flexlion uses it. you can also ask @nvnprogram on discord for the file).  
You can place your videos into /flexlion3/video/, supported formats are webm(vp8, vp9), and mp4(may randomly not work? """newer""" mp4 files may not load for some reason, if that happens try webm instead). The video is played in LobbyVersus. To enter lobby offline, you can use Coxxs patches ([here](https://github.com/Coxxs/public-pchtxt)) (do NOT use online, they are 100% not online safe)
### Important Note by **kirakira**:  Splatoon 10.X.X updated the whole SDK as well (also broke all hooks) so it might not work using ACNH's subsdk0, so use Splatoon 9.3.0, I've personally tested VideoModule on 9.3.0 and it works fine. Go to the releases page for 9.3.0 flexlion. **DO NOT PESTER ME FOR SPLATOON 930 GAME ROM; THATS PIRACY AND I WILL JUST BLOCK YOU**  

# Join the official discord server [here](https://discord.gg/ZPBKbpKYMM) to see the progress.
