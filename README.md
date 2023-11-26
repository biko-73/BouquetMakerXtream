# BouquetMakerXtream
A plugin to allow the easy creation of bouquets for IPTV playlists.  Based on my original JediMakerXtream plugin, but completely rewritten and code modernised.

How to use BouquetMakerXtream (BMX)
Main Menu - No providers
 <img src="https://i.ibb.co/XWB2tBN/1.png" alt="1" border="0">
Main Settings
<img src="https://i.ibb.co/GPbwfyr/2.png" alt="2" border="0">
Add Playlist
<img src="https://i.ibb.co/Dk9H52c/3.png" alt="3" border="0">
Main Menu - provider added
<img src="https://i.ibb.co/yBzr1yy/4.png" alt="4" border="0">
Playlists
<img src="https://i.ibb.co/CbnNW49/5.png" alt="5" border="0">
Xstream/XUI ONE Playlists - Info Screen
<img src="https://i.ibb.co/wcnZSgx/6.png" alt="6" border="0">
Bouquet Settings
<img src="https://i.ibb.co/myfFS6j/7.png" alt="7" border="0">
Category and Channel Selection
<img src="https://i.ibb.co/jZdNGDp/8.png" alt="8" border="0">
Main Menu - After bouquets have been created
<img src="https://i.ibb.co/86p0pdq/9.png" alt="9" border="0">
Main settings - Catchup options. Needs turning on.
<img src="https://i.ibb.co/mhS9dQ6/10.png" alt="10" border="0">
Channel Select screen for catchup - Most images its down keypad button.
<img src="https://i.ibb.co/2SXCdyH/11.png" alt="11" border="0">
Catchup List - Triggered by Stop, List, PVR, Video, File or FAV buttons
<img src="https://i.ibb.co/34nPhTK/12.png" alt="12" border="0">
 
BouquetMakerXtream has no playlists in it.
All playlists have to be sourced by user.

Main Settings

•	playlists.txt location - the playlists.txt file can be placed anywhere or even shared with my other plugins.
•	Local M3U File location - plugin can play local m3u8 playlists. This folder of playlists can be placed anywhere.
•	Automatic live bouquet update - plugin uses epg importer to import the epg. This is the time my plugin will redownload and refresh the provider channels to be used by epg importer. The EPG is downloaded at the time set in EPG Importer. Set this value earlier than EPG importer time.
•	Live/VOD/Series Stream types - All providers are different. Some play better with 1, most play better with 4097, ideally though use service app and use exteplayer 5002. Dreambox users also have the option of DreamOS gstreamer 8193. These are the default types for any new providers added. These values can be individually changed for each provider in Bouquet Settings.
•	Max channels - The defaults should be fine for most users. If you are a power user and want 20000+ channels, there is an unlimited option.
•	Group bouquets into its own folder - Have a parent group in bouquets with sub bouquets inside that. i.e. iptv2023 folder with individual bouquet folders inside that. Useful if using mutiple playlists.
•	Parental Control - This does not stop adult channels. This prevents the settings and bouquet creation being accessed unless the adult pin is entered. It is up to the user to hide adult channels in the selection screen.
•	Exit plugin on bouquet creation - If the is on, the plugin exits after creating bouquets. If this is off, the plugin returns to the playlists screen.
Main Settings - Catchup
•	As catchup is taking over a core component of your box. Catchup needs to be turned on by user. It is off by default
•	Prefix Catchup channels - this is the symbol used in channelselect so you can identify which channels your provider has catchup for.
•	Margins - This adds a time margin before and after the catchup time slot. I.e. Starts 5 minutes earlier. Finishes 5 mins later.


Add Playlists

Add a playlist via main menu, or you can manually add a playlist to the file.
/etc/enigma2/bouquetmakerxtream/playlists.txt

Xtream/XUI ONE playlists
In the format
https://domain.xyz:8001/get.php?username=user&password=password&type=m3u_plus&output=ts #iptv2023

Port can be blank if your provider doesn't have a port number.
type can be m3u or m3u_plus/
output can be ts or m3u8 (not hls or mpegts).

if you want to add a name here. space hash name. As shown in the example. Avoid hyphens and underscores where possible. It might cause confusion

External playlists
Must be in standard m3u8 format

#EXTM3
#EXTINF:-1 blahblahblah
http://blahblahbla
#EXTINF:-1 blahblahblah
http://blahblahblah

Can be any url, shortlinks, bitly etc as long as it starts with http:// or https://
If copying from pastebin or github etc. Use the raw address


Make Bouquets

Each playlist has its own individual bouquet settings. Each provider is different. So select your preferred stream type for that provider, and which options, live, vod, series you wish to show.

User alternative EPG url: This option is only if your provider recommends an alternative epg address other than xtream default. Channels have IDs in them that are referenced in the EPG data. You cannot just use random EPGs for providers. They have to match. My other plugin JediEPGXtream can be used to assign 3rd party epg to IPTV channels if you are missing EPG data.

The whole point of this plugin is to only select the channels and/or streams that your are likely to watch.
Who really wants 20000 worldwide channels. Nobody. The more you select, the slower to build.

There is a screen for each category selected to be shown. Live / Vod / Series.
Press ok to hide the categories or channels you wish to hide.
If you wish to start blank, press the yellow button to invert all the selected ones to hidden. Then add only the ones you want.
All hidden categories/channels are remembered next time you go to make bouquets. Newly added channels will be classed as unhidden.
When you have finished your selection, finally press OK and your bouquets will be built.
To open user created bouquets you need to exit out of the plugin to main tv, and then open channelselect screen. (keypad down). Then blue button (favourites) to find your bouquets.

Do note there is a limit on the amount of Live, VOD and Series you can download. There is a setting for this in Main Settings.
Experiment with these values if all your bouquets are not being shown.

EPG Importer

Once you have created your bouquets. There will be a folder in EPG Importer sources.
You need to tick the checkbox to add it to EPG importers schedule.
<img src="https://i.ibb.co/3TGXYWb/image.png" alt="image" border="0">
You can wait for EPG importer automatic update, or you can do a manual update of selected sources if you wish to see EPG straight away.

My plugin is designed to work only with the original EPG Importer plugin. Not mods of it, or crossepg.


Catchup / MediaTek

Due to nearly every provider doing something different with the main epg nowadays and its getting very hard to reference this epg screen on all images, the catchup option has been moved to channelselect screen. Most providers still have very similar code for this screen and is easy to reference. This also prevents any clashes with my JediMakerXtream Plugin or other plugins that are manipulating the main EPG screen.

A reminder Catchup needs to be turned on in main settings.

To view catchup channels.
•	Visit channelselect screen (keypad down - on most images)
•	Press blue button (Favourties)
•	Enter your IPTV Bouquet.
•	Look for channels with your catchup prefix symbol. (I assume you have this symbol turned on)
•	Press one of the trigger buttons to open up the catchup list. Stop, List, PVR, VIDEO, FILE or FAV
•	Select the programme you wish to watch
•	Your programme will play in movie player. - You might need to edit movie player plugin settings to allow the exit key to exit the player.

Picon Downloader










FREQUENTLY ASKED QUESTIONS

General Questions

Is this plugin a clone of JediMakerXtream
No - Jedi became far too complicated. This is a new plugin, totally new modern code.
There is no plans at the moment to have a name swap - this was originally put in due to UK Virgin cable channels and to allow channels to pick up epg from Rytec. Since then I wrote JediEpgXtream plugin which allows the assigning of epg to iptv channels. So that code no longer needs to be in this plugin

Main Menu Options
•	Menu options are conditional. They only appear when that option is available.
•	Playlists will only appear if you have added a playlst via the plugin or playlists.txt file
•	Delete & Picon Downloader will only appear after you have created at least one bouquet of channels

Bouquet Creation

Best practice
On selecting channels - It is probably best to invert the category selections (yellow button). Then only select the channels you want. That is the entire point of the plugin
Selections are remembered so you can always add or remove more if required.

Missing channels after creation
In main settings there are options to set the maximum amount of channels to download per category type. Live and VOD are reasonably quick. Series is slow to create. It is highly recommended you do not set "Series" to 0 No Limit. It will probably freeze your box and fail to create.


Picon Downloader


Why are some picons missing?
•	Pillow library cant process SVGs. So I only process jpegs and pngs.
•	If picon source is too big, I ignore it. Can be changed in main settings.
•	If picon source is an image builder url, with no mention of jpg or png in the url. I ignore it.
•	If picon source is corrupt. I try and ignore it.
•	Dead picon source urls - provider issue

Picons are too small
Unfortunately all providers are different. I reduce large picons to the correct size, but I do not enlarge small picons. This will just make them blurry.
If picons are too small this is purely because the source images are too small.

Picon Locations
Most images have set folders where picons are meant to be placed. Each image is different so google your images picon location

Picon Symlinks
If you want to create a symlink/shortcut from one location to another so your image can pick up this location, the telnet/putty syntax is
ln -s /media/hdd/picon /usr/share/enigma2
ln -s [new-location] [original-location]

Picon Folder clashes.
You cannot have 2 active picon locations as far as I believe.
Delete any picon files and "picon" folder from other known locations for your image. Use only one location globally for your box.

Picon priorities
SRP picons will override and take precedence over SNP picons.

LCD Picons
There is no code in the plugin to create seperate LCD picons.
I do not have a box with a LCD. So this will not be a thing in this plugin.

Embedded Base64 Picons
Nope that unnecessary bulky code just gets ignored. I doubt hardly any IPTV apps actually use them. Waste of time.

General Picon Questions
I am not a picon expert on these boxes. Questions relating to your image default locations, formats etc etc is what google is for.


Playing Streams


The streams are played via your enigma2 libraries. This is not a standalone IPTV player. Use my Xtreamity plugin if you want an IPTV player.
If a stream is black, no audio, buffering, or has noise artifacts. There is not a lot I can do about that.
Do try different stream types. 1, 4097, 5001, 5002(serviceapp) etc. All providers are different and you need to find what works best for your provider.

Catchup/TV Archive/MediaTek

My provider has catchup but catchup isn't working.
Catchup is now in channelselect screen and not main EPG guide.
Catchup needs to be turned on in main settings as it changes the functionality of core components on your box.

How do I know if a channel has catchup.
Turn on catchup prefixes in main settings. Select the prefix you wish to show in front of your channels. Prefixes shouldn't effect EPG or Picons.

Catchup only shows 2 days worth of catchup
This is provider related - Some default to 2. Some show up to 10 days

Can you record catchup channels.
Er... Don't know - catchup channels are played via MoviePlayer. Try it and see.


