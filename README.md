# Anatomy of a NotITG Modfile

This is a document to highlight the anatomy of a NotITG modfile and the inner workings of each file, as well as how to set up a basic modfile template that you can build upon to create something unique and tailored to you.

## SM (NITG) Specification

`#NITGVERSION` - The earliest required version of NotITG to play your file specified by `YYYYMMDD` of release. If you use mods/features not present in a prior version, set this tag to minimize reports of a broken modfile on earlier versions of NotITG.  
`#TITLE` - The song's title. Put the name of the song here.  
`#TITLETRANSLIT` - The song's title translated to English.  
`#SUBTITLE` - The song's subtitle. Put any part of the title in parentheses here.  
`#SUBTITLETRANSLIT` - The song's subtitle translated to English.  
`#ARTIST` - The song's artist. Put the creator of the song here.  
`#ARTISTTRANSLIT` - The song's artist translated to English.  
`#GENRE` - The song's music genre. Mostly unused.  
`#CREDIT` - The author of the file. Put yourself here!  
`#MUSIC` - The path to the audio file. OGG is most widely accepted, but MP3 can be used as well.  
`#BANNER` - The path to the file banner. PNG, JPG, or GIF works here.  
`#BACKGROUND` - The path to the file background. Mostly unused.  
`#CDTITLE` - The path to the file jacket (the sleeve of the album). Mostly unused.  
`#SAMPLESTART` - The start of the preview that plays on the song wheel. Set it to a hype moment in the song!  
`#SAMPLELENGTH` - The length of the preview that plays on the song wheel. Try to get it to loop nicely!  
`#SELECTABLE` - The setting that marks your file as one that can be chosen on the song wheel. Mostly unused (you want people to play your file, right?)  
`#OFFSET` - The offset of the audio from the chart's first beat. Milliseconds are imperative for this tag.  
`#BPMS` - The tempo(s) of the song at the specified beat(s). Most likely one entry, but can have several.  
`#STOPS` - The section(s) of a chart that freeze in place for the specified length(s) in seconds. Mostly unused in modfiles, but there are plenty exceptions if you look well enough. Used a lot in gimmick charts.  
`#BGCHANGES` - The changes to the background during gameplay. Can be PNG, JPG, MPEG, GIF, INI, or XML.  
`#BETTERBGCHANGES` - `#BGCHANGES` but better? There's some bug with `#BGCHANGES` that this fixes and I don't remember what.  
`#FGCHANGES` - The changes to the foreground during gameplay. This is what nearly every modern modfile uses to inject the Lua necessary for modfiles to work in the first place.  
`#NOTES` - The section to denote a chart in the SM.

## Modfile Setup

Once you set up your chart for normal play, you have a few steps before you can fully initialize a modfile environment. Here is an example of a very basic modfile template you can customize further on your own.

(If images don't load, you can view the repository for this template here.)

1.	Create a folder called `lua` in your stepfile's root directory.![mug root beer](https://cdn.discordapp.com/attachments/945097632185995334/945097725425365062/unknown.png)
2.	Create a file in `lua` called `default.xml`.![mug root beer](https://cdn.discordapp.com/attachments/945097632185995334/945097988911530014/unknown.png)
3. Open `default.xml` in your code editor and create an `ActorFrame`.![mug root beer](https://cdn.discordapp.com/attachments/945097632185995334/945098620015886366/unknown.png)
4. Add an `OnCommand` to  the `ActorFrame`.![mug root beer](https://cdn.discordapp.com/attachments/945097632185995334/945099646009741403/unknown.png)
5. Add a `StartCommand` and an `UpdateCommand`, create a `queuecommand` for `'Start'` in `OnCommand`, and set `'Update'` as a `luaeffect` in `StartCommand`.![mug root beer](https://cdn.discordapp.com/attachments/945097632185995334/945105118985084968/unknown.png)
6. Add `children` to the `ActorFrame` that contains an `Actor` that will sleep permanently to prevent our FG code from being cleared immediately.![mug root beer](https://cdn.discordapp.com/attachments/945097632185995334/945105366813904946/unknown.png)
7. Create a new function that will track the mods we change.![mug root beer](https://cdn.discordapp.com/attachments/945097632185995334/945105620669972490/unknown.png)
8. Create a for loop in `UpdateCommand` that will update and apply modifiers at the correct beat.![mug root beer](https://cdn.discordapp.com/attachments/945097632185995334/945108470187835402/unknown.png)
9. Edit the file's `SM` to include your `XML` via `#FGCHANGES`.![mug root beer](https://cdn.discordapp.com/attachments/945097632185995334/945108776372043786/unknown.png)
10. Test for any Lua errors, reading the message to find what line of what file is causing the issue (In this case, no issues so far).![mug root beer](https://cdn.discordapp.com/attachments/945097632185995334/945109613479604295/unknown.png)
11. Insert a mod using our custom mod function.![mug root beer](https://cdn.discordapp.com/attachments/945097632185995334/945109906913099806/unknown.png)
12. Test for further issues (In this case, we used `mods` for a variable when we wanted `mod`). ![mug root beer](https://cdn.discordapp.com/attachments/945097632185995334/945110180163616788/unknown.png)
13. Make adjustments to code accordingly (Repeat these steps until no errors are shown).![mug root beer](https://cdn.discordapp.com/attachments/945097632185995334/945112654576488548/unknown.png)
14. MARVEL AT YOUR INFINITE POWER![mug root beer](https://cdn.discordapp.com/attachments/945097632185995334/945112894964641822/unknown.png)
