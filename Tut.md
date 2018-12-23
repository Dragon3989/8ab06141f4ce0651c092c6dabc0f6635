# 8ab06141f4ce0651c092c6dabc0f6635
Yu-Gi-Oh Duel links Asset file decryption guide  

Before I begin credit to XOF#7007 and Marko#2691 (Xellos) For teaching me how to do all of this mentioned.
**Decrypting basic game assets.**

So firstly we'll start with being able to decrypt "Compiled assets" such as raw Images and some basic elements such as 3d models text assets etc. To do this download Asset studio from the following link https://ci.appveyor.com/project/Perfare/assetstudio/branch/master/artifacts

Once you've done that and opened the program you're going to go 
File, Load File and go to your local data **C:\Program Files (x86)\Steam\SteamApps\common\Yu-Gi-Oh! Duel Links\LocalData** 
Now you're going to want to go to the search bar up the top right and sort by "date modified" so you'll be able to tell the files you just downloaded from an update. https://i.gyazo.com/d8df8a27541e59d652f482647687b19d.mp4 
Once you've found the file assets just select the applicable ones (via control + shift) and allow them. i'd advise also copying the files to make decrypting the binary assets later easier and then just open up the files.
Now you'll have access to all the textures, sounds and whatever was applied in the base update for most unity assets. Feel free to mess around with the program and I'd advise setting the "Use orginal file names" to be on to make it more clean when extracting aswell as giving hints such as ID's for events etc.

**Binary**

so we're gonna make a new folder now and paste those files that we just copied to that new location so we can extract the binary from those files aswell 
Now we're gonna download "Quickbms" and download the extention https://aluigi.altervista.org/bms/yugioh_ydlz.bms 
Once we've got that done, place them in a seperate folder and instead of just launching quickBMS drag the yugioh extention over to it and launch it with that.
Now we have that open go to the location of the update files and select them all and then you can choose to place the extracted files in that location or a new folder (up to you)
Then simply let that run its course and open the .DAT files with notepad++

**Server interactions** 

One thing this guide cannot do is let us see stuff such as ranked tickets etc because that's handled by the server. 
To do this you need a way to modify the interaction the client sends to the server (Ideally use NOX and charles web debugger and look for seperate tutorials elsewhere because It's not worth explaining here.)  One thing to note is after ~20 to 30 seconds it will time you out for not connecting to the server and you'll have to restart and modify your request again.
So we're gonna breakpoint (which stops all data being sent) before clicking any type of ticket which will return us with a ItemID in this case {550320111} Now the main thing to notice here is 32 and 11 as the formating for a ranked ticket goes 550- Season So season32 in this case 11 is a common 21 is a rare 31 is a super rare and 41 is a ultra rare and the last 1 on the end in that case is because it's a glossy. You can tell when tickets have have been added because in the binary assets you'll be able to find an item ID with the season after the current one. so you just simply replace the ItemID in this case with the ticket ID you want to see, you can always just check other tickets base ID's and work out from there.

**Event info.**
This is done via md5 hashs and as such is pretty much impossible to decrypt and generally takes alot of guessing. The basic ones are stuff like:
Campaign12 is double duelist Campaign14 is bonus rewards and Campaign15 is 1.5XP. Feel free to mess around
Now firstly to get into this "prompt" menu you're gonna need to find something in the menu that allows a pop up to go to an event dialog popup or a bonus duelist/1.5 xp, breakpoint it and then enter the new MD5 hash. You can convert names to MD5 hashes here https://www.md5-generator.de/ and just copy the code on the right and replace the md5 hash in your breakpoint with it and submit it.
