# MENDING MORROWIND

[Back to main page](https://github.com/Sigourn/morrowind-improved/blob/master/readme.md)

## INDEX

- [Modding tips](https://github.com/Sigourn/morrowind-improved/blob/master/mendingmw.md#modding-tips)
- [Morrowind Code Patch](https://github.com/Sigourn/morrowind-improved/blob/master/mendingmw.md#morrowind-code-patch)
- [Uncompressed vanilla textures](https://github.com/Sigourn/morrowind-improved/blob/master/mendingmw.md#uncompressed-vanilla-textures)
- [Bug fixes and optimization](https://github.com/Sigourn/morrowind-improved/blob/master/mendingmw.md#bug-fixes-and-optimization)
- [Minor bug fixes](https://github.com/Sigourn/morrowind-improved/blob/master/mendingmw.md#minor-bug-fixes)
- [MWSE bug fixes](https://github.com/Sigourn/morrowind-improved/blob/master/mendingmw.md#mwse-bug-fixes)
- [Expansion Delay](https://github.com/Sigourn/morrowind-improved/blob/master/mendingmw.md#expansion-delay)
- [Intelligent Textures](https://github.com/Sigourn/morrowind-improved/blob/master/mendingmw.md#intelligent-textures)
- [Finishing touches](https://github.com/Sigourn/morrowind-improved/blob/master/mendingmw.md#finishing-touches)
    - [Adjusting your load order](https://github.com/Sigourn/morrowind-improved/blob/master/mendingmw.md#adjusting-your-load-order)
    - [Automated conflict resolution](https://github.com/Sigourn/morrowind-improved/blob/master/mendingmw.md#automated-conflict-resolution)
    - [Synchronizing mod masters](https://github.com/Sigourn/morrowind-improved/blob/master/mendingmw.md#synchronizing-mod-masters)
    - [Running Distant Land](https://github.com/Sigourn/morrowind-improved/blob/master/mendingmw.md#running-distant-land)
    - [In-game configuration](https://github.com/Sigourn/morrowind-improved/blob/master/mendingmw.md#in-game-configuration)

## MODDING TIPS

A crash course to Morrowind and Bethesda modding in general is:

- Don't uninstall mods mid-playthrough, and if you do, keep a pre-uninstallation savefile as a backup in case things go wrong.
- Read the description of every mod you install. Descriptions usually list requirements, compatibility issues, and known issues in a mod. This not only prevents future issues (or assures you they are "normal" or "expected"), but it also helps you decide beforehand whether a mod is worth the trouble.
- File structure matters when installing a mod. The file structure is how files are organized for the game to read these files and use them. Incorrect file structure accounts for a good deal of mods that don’t work properly. For instance, .esm and .esp files always need to be inside **Morrowind\Data Files**, or else the game simply won't register them. When a mod listed here has packaging issues, I will tell you how to fix them. Bear in mind that some mods do keep optional plugins in a separate folder, but these are the exception and descriptions usually make mentions of them.
- Some mods come with BSA files. These contain data files for the mod. The most popular mod which includes BSA files is the Tamriel Rebuilt project, which is not part of this guide. BSA files need to be registered in your Morrowind.ini file for the game to properly load the assets; failing to due so results in a well known problem of [yellow exclamation triangles](https://external-preview.redd.it/dl-I4l_Pzm5autet-87p1hnU1btUavtiu1mtwGzWBko.png?width=960&crop=smart&auto=webp&s=3d180a6476cad80c332c12be08252511a0044c5c). This particular guide, however, features no mods with BSA files. Broadly speaking, mods with BSA files tend to add lots of new assets into the game (meshes and textures), and this guide is focused with mostly vanilla graphics in mind.

When installing mods manually, by extracting the contents of a mod and dropping them inside your Data Files folder, there is a chance you will be overwriting one mod's files with another mod's. This is where mod managers come in: they make modding easy by providing you with lots of tools to aid you in modding your game.

**Mod Organizer 2** lets you hide specific files from your installed mods, including anything from meshes to textures, but also plugins. This is a especially useful feature when you deactivate certain plugins from a mod but don't want to see them cluttering up your load order, or you want to certain files not to overwrite another mod's.

- To hide a plugin, right click on your installed mod and select **Information...**.
- Select the **Filetree** tab.
- Right click on the plugins, folders, or files you want to hide, and select **Hide**.
- Mod Organizer 2 will hide the files, and these will no longer affect your game.

Separators allow you to neatly separate installed mods in Mod Organizer 2 for ease of viewing. I recommend creating a separator for the following sections before installing these mods.

- Right click on the empty space on the mod order window, and click **Create Separator**.
- Name it **MENDING MORROWIND** and click **OK**.

One more quirk about Mod Organizer 2 is the **Overwrite** folder and how it ties together with the tools we installed in the **Setup** section. The **Overwrite** folder is the destiny folder for the output of many of these tools. For instance, Distant Land generation will place its contents here, inside the **distantland** folder. Files in the **Overwrite** folder will overwrite all your installed assets and plugins, should they have the same names.

Now that we have installed all tools, our Mod Manager, and MGE XE, we can finally get onto patching Morrowind itself.

## MORROWIND CODE PATCH

The Morrowind Code Patch patches bugs in the Morrowind program (Morrowind.exe), which cannot otherwise be fixed by editing scripts or data files. It is a must-have utility for anyone who plays with vanilla Morrowind. Unlike mods, the Morrowind Code Patch requires specific install instructions, and can't be installed through Mod Organizer 2.

[**Morrowind Code Patch**](https://www.nexusmods.com/morrowind/mods/19510?tab=files)

- Extract the contents of the file to your Morrowind root directory, so that Morrowind Code Patch.exe and the mcpatch folder are in the same folder as Morrowind.exe.
- Now download the **MCP beta** update file from [**Morrowind Code Patch Update**](https://www.nexusmods.com/morrowind/mods/26348/?tab=files).
- Extract the contents of the file to your Morrowind root directory, and overwrite when prompted. This will update the Morrowind Code Patch to version 2.5b4.
- Right click on Morrowind Code Patch.exe and select **Run as Administrator**.
- The amount of options available can be overwhelming. My recommendation is to install or skip patches as per [this handy Google Sheets document](https://docs.google.com/spreadsheets/d/1r6fv59to4-KgHJgCm-GDNnwSmD3LdDmamSDEs5jKFdM/edit?usp=sharing).
- Once you finish installing the Morrowind Code Patch a **Morrowind.Original.exe** will appear in your Morrowind folder.

The Morrowind Code Patch **Rain/snow collision** patch requires a few .ini edits to work properly.

- Launch Mod Organizer 2.
- Click on the **Tools** icon, which resembles a jigsaw puzzle, and click **INI Editor**.
- On the morrowind.ini that just opened, adjust the following values. Use CTRL+F to input the bolded names and find them easily.
  - **[Weather Rain]**
  - Rain Diameter=600 -> Change this to **Rain Diameter=1200**
  - Max Raindrops=450 -> Change this to **Max Raindrops=1500**
  - **[Weather Thunderstorm]**
  - Rain Diameter=600 -> Change this to **Rain Diameter=1200**
  - Max Raindrops=650 -> Change this to **Max Raindrops=3000**
  - **[Weather Snow]**
  - Snow Diameter=800 -> Change this to **Snow Diameter=1600**
  - Max Snowflakes=750 -> Change this to **Max Snowflakes=1500**
- Click **Save** and close the window.

## UNCOMPRESSED VANILLA TEXTURES

These textures must be installed before any other mod that replaces them, such as bug fixing mods.

- [**Morrowind Uncompressed Vanilla Textures**](https://www.nexusmods.com/morrowind/mods/45551) by Bethesda Softworks: replaces most vanilla textures with textures shipped in the GOG release of Morrowind that have less compression artifacts and which the game doesn't use by default.
  - MO2 will tell you there's no game data on top level. Right click on **Data Files**, click **Set data directory**. Click **OK**.

## BUG FIXES AND OPTIMIZATION

These are the major bugfixing and optimization mods for Morrowind. No player should play Morrowind without these.

- [**Patch for Purists**](https://www.nexusmods.com/morrowind/mods/45096) by half11: the "official" unofficial fan patch for Morrowind, simply put the best out there.
- [**Correct UV Rocks**](http://mw.modhistory.com/download-56-12003) by Nich: fixes UV mapping on rocks and stones.
  - MO2 will tell you there's no game data on top level. Right click on **Data Files** and click **Set data directory**. Click **OK**.
- [**Morrowind Optimization Patch**](https://www.nexusmods.com/morrowind/mods/45384?) by Remiros and Greatness7: greatly improves performance and fixes some mesh errors.
  - MO2 will install the mod as a BAIN package. Tick the following options and click **OK**:
    - **00 Core**
    - **01 Fixed Vanilla Textures**
    - **02 Lake Fjalding Anti-Suck**
    - **03 MGE XE Addon**
  - Hide/delete **meshes\f\furn_web00.nif** and **meshes\f\furn_web10.nif**. These meshes are buggy and cause visual problems when seen from a distance.
- [**Project Atlas**](https://www.nexusmods.com/morrowind/mods/45399) by the Project Atlas Team: optimizes the most performance heavy areas of vanilla Morrowind through texture atlases. 
  - MO2 will install this mod as a BAIN package. Tick **00 Core** and click **OK**.
  - Hide/delete **meshes\x\ex_imp_plat_01.nif**. This mesh is buggy and can cause problems when traveling from Raven Rock to Fort Frostmoth using the boat.

## MINOR BUG FIXES

These are minor bug fixes that most players won't notice. Feel free to skip them.

- [**No More Stage Diving - Desele's Dancing Girls**](https://www.nexusmods.com/morrowind/mods/47738) by Pherim: keeps the girls in Desele's House of Earthly Delights from dancing off the stage by making them not greet the player as he approaches them. 
  - Only install the **No More Stage Diving** main file.
  - Hide/deactive **NoMoreStageDiving_TalkativeGirls.esp**.

## MWSE BUG FIXES

These are bug fixes and quality of life improvements that require MWSE to work appropiately.

- [**Expeditious Exit**](https://www.nexusmods.com/morrowind/mods/45634) by NullCascade: forces the game to instantly close on exit.
- [**Immersive Run Fix**](https://www.nexusmods.com/morrowind/mods/45947) by Petethegoat: normalizes the player's movement speed, ensuring they run at a consistent speed even during diagonal movement. 
- [**Quest Skill Reward Fix**](https://www.nexusmods.com/morrowind/mods/48269) by Merzasphor: makes the game treat skill increases from quests as if there were raised via normal means, solving numerous problems with how the game treats these skill increases.
- [**Skill Increase GMST Fix**](https://www.nexusmods.com/morrowind/mods/48029) by Merzasphor: fixes several engine bugs related to GMSTs used when raising skills via NPC training and skill books.

## EXPANSION DELAY

This is an essential mod for anyone who thinks Bethesda's expansions deserved a better implementation.

- [**Expansion Delay**](https://www.nexusmods.com/morrowind/mods/47588?) by half11: modifies how the Tribunal and Bloodmoon expansions are implemented into the game.

## INTELLIGENT TEXTURES

This is the most faithful to vanilla and comprehensive texture pack out there. Thankfully, the textures included in Intelligent Textures already contain the texture fixes present in the above mods.

- [**Intelligent Textures**](https://www.nexusmods.com/morrowind/mods/47469) by Remiros: replaces almost all textures in the vanilla game and its expansions with high resolution AI upscales.
  - MO2 will install this mod as a BAIN package. Tick **00 Core** and **01 Atlas Textures** and click **OK**.
  - Also install the **Wood Fix** update file.
  - Also install [**this hotfix**](https://www.mediafire.com/file/impju2r934eqkkt/Intelligent_Textures_Ashlander_Hotfix_v2.zip/file), which will fix a bug with one of the ashlander hairstyles.

> If you see white textures in Velothi buildings (such as the Temples) after installing **01 Atlas Textures**, [**install this downscaled patch**](https://www.mediafire.com/file/6kvf9k2lehy8yhb/Intelligent_Textures_v2.1_-_Downscaled_Velothi_Atlas_Patch.zip/file) on top of Intelligent Textures. White textures can happen with less than ideal GPUs since the Atlas textures are already bigger than most textures in Morrowind, and the Intelligent Textures patch exacerbates their dimension far beyond the norm.

## FINISHING TOUCHES

### ADJUSTING YOUR LOAD ORDER

Before running the automated conflict resolution tools, we need to confirm your installed mods and plugins are in the right order.

You can download a package containing these in .txt form from here: [Mending Morrowind June 18th](https://download1502.mediafire.com/aez3glgpaz9g/hoe97mn1vwvsu5o/Mending+Morrowind+-+Load+order.zip)

> The **loadorder.txt** is formatted so that Mod Organizer 2 is able to read it, and adjust your load order accordingly. For Mod Organizer 2 to recognize **loadorder.txt**, you need to place it inside **\Mod Organizer 2\profiles\Morrowind Improved\loadorder.txt**, overwriting when prompted. Note that this will overwrite your personal **loadorder.txt**: if you aren't okay with this, simply adjust your load order manually. Your mod installation order, however, will need to be adjusted manually in any case.

### AUTOMATED CONFLICT RESOLUTION

TES3Merge lets us merge the objects in our active plugins in order to reduce conflicts, generating a **Merged Objects.esp** file which we will have to place at the end of our load order. This is very useful when, for example, you have a mod that modifies the stats on the Glass Armor while another modifies how it looks like: TES3Merge will merge both changes into a single plugin.

- Run TES3Merge in MO2. Once it's finished, press any key to exit.
- **Merged Objects.esp** will now be present at the end of your load order.

TESTool lets us merge the leveled lists in our active plugins in order to reduce conflicts, generating a **Merged_Leveled_Lists.esp** file which we will have to place at the end of our load order. This is very useful when, for example, you have a mod that adds certain weapons for sale to vendor leveled lists, and another mod also does the same.

- Run TESTool in MO2.
- A window will pop up, asking you if you want to use your Morrowind root folder instead of registry settings. Click **Yes**.
- Select **Merge Leveled Lists for active plugins** and click **Execute**.
- Close the program. **Merged_Leveled_Lists.esp** will now be present at the end of your load order.

### SYNCHRONIZING MOD MASTERS

Wrye Mash lets us synchronize the masters of mods we have installed. This will prevent certain error messages from popping up when launching the game.

- Run WryeMash in MO2.
- In the **Mods** tab, you will see a list with all your plugins, both active and inactive. Plugins that do not need to have their masters synchronized have a **green box** next to them. Those that do need to have their masters synchronized will have a box of a different color.
- Click on the faulty plugin, and a panel to the right will display the plugin's masters. Right click on either of them, and an **Update Masters** window will appear. Click **Yes**. 
- Once the window has closed, click on the **Save** button further below the same panel.

### RUNNING DISTANT LAND

MGE XE's Distant Land setup should be re-run. If you followed the steps [in this section](https://github.com/Sigourn/morrowind-improved/blob/master/setup.md#distant-land-tab) earlier, the process will be much easier.

- Run MGE XE in MO2.
- In the **Distant Land** tab, click **Distant land generator wizard**.
- Click **Select all**, and then **Continue**.
- Click **Run above steps using saved / default settings**.
- Once the statics have been created, simply click **Finish**.

### IN-GAME CONFIGURATION

- Under the **Options** menu, go to the **Video** tab.
  - The **Gamma Correction** slider lets you increase/decrease the brightness of your game. I like to play Morrowind with the slider roughly 40-45% of the way from left to right, making the game look less washed out.
  - Turn the **Real-time Shadows** slider all the way to the left, disabling them. These shadows look pretty bad, and can be quite glitchy.

Congratulations, your Morrowind installation is ready!

[Back to main page](https://github.com/Sigourn/morrowind-improved/blob/master/readme.md)
