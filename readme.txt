Now playing XSplit and OBS overlay for Foobar2000 by Farpenoodle
---------------------------------------------------------------------

To use, download and install the "Now Playing Simple" plugin by 
skipyrich from the following location:

http://skipyrich.com/wiki/Foobar2000:Now_Playing_Simple

Once done, copy the following into the plugin preference screen:

{
	"nowplaying": {
		"playing": $replace(%isplaying%,'?','0'),
		"paused": $replace(%ispaused%,'?','0'),
		"albumartist": "$replace(%album artist%,'"','\"','\','\\')",
		"album": "$replace(%album%,'"','\"','\','\\')",
		"artist": "$replace(%artist%,'"','\"','\','\\')",
		"title": "$replace(%title%,'"','\"','\','\\')",
		"tracknumber": $add($replace(%track number%,'?','0'),0),
		"length": $replace(%length_seconds%,'?','0'),
		"elapsed": $replace(%playback_time_seconds%,'?','0'),
		"path": "$replace($directory_path(%path%),'"','\"','\','\\')"
	},
	"config": {
		"fadeout": 10
	}
}

Make sure it's writing nowplaying.json to the same directory you
extracted the files. Then check all the events under the events tab.

Next just add the html files to your streaming software.

For XSplit
----------
Just drag the html file onto the stage. You may want to set the width
and height manually to 320x120 for the overlay with art or 220x120
for the overlay with no art.

For OBS
-------
Make sure you have the Browser Source Plugin installed. Get it here:

http://obsproject.com/forum/resources/clr-browser-source-plugin.22/

Add a CLR Browser source to your scene and point it to the
appropriate html file. You may want to set the width and height 
manually to 320x120 for the overlay with art or 220x120 for the 
overlay with no art. You may also want to add the Browser source as
a Global Source so it doesn't reload and show again on scene switch.

Configuration
---------------------------------------------------------------------

You can change the duration in seconds that the overlay will show on
track change by changing fadeout under config in the JSON file.

If you set fadeout to 0, then it will perpetually show the overlay
without fading after the next track change.

Overlay with album art only works if you store your music in a format
that seperates files by album into their own folder. And within each
folder you store a folder.jpg containing the album art.

For example:

C:\Music\Artist\Album\folder.jpg
C:\Music\Artist - Album\folder.jpg

---------------------------------------------------------------------