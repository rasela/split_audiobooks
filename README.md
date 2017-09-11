# Audible file to mp3 files for each chapter

Audio books from Audible (AAX files) can only be played using software provided by Audible. Customers who do not convert them to a more open format like mp3 are likely to lose the ability to listen to their audio books at some point in the future. Converting an audio book to one long mp3 file is relatively easy. These scripts help with the more tedious task of splitting it into chapters.

## requirements

* a converter like aax2mp3 and an Audible player (works on Windows or Mac, should work with Wine on Linux)

* [Audacity](https://en.wikipedia.org/wiki/Audacity_%28audio_editor%29)

* the console program [mp3splt](http://mp3splt.sourceforge.net/mp3splt_page/documentation/man.html)

This works on Linux. Small changes may be necessary for other operating systems.

![video](http://paste.watchduck.net/1709/split_audiobooks_video.png)
A video tutorial can be found [on Vimeo](https://vimeo.com/233148975). Maybe it is back [on Youtube](https://www.youtube.com/watch?v=oztnCJlY3bo) after it was [removed](http://paste.watchduck.net/1709/split_audiobooks_youtube_strike.png).

## usage

* use a program like aax2mp3 to create the long mp3

* create a working folder (This is where all the following steps happen.)

* move the long mp3 there and call it `uncut.mp3`

* put `audible_to_audacity.py` and `audacity_to_mp3splt.py` there

* copy the chapter list from Audible to `audible_chapters.txt`

* (adapt the regex in `audible_to_audacity.py` if the lines in your chapter list look different)

* run `audible_to_audacity.py`, which will create `audacity_labels_in.txt`

* (If you are fine with the makeshift chapter names and the times in that file, you could just skip the Audacity part, and rename it to `audacity_labels_out.txt`.)

* open `uncut.mp3` in Audacity and import the labels in `audacity_labels_in.txt`

* modify chapter names and times as you wish (Make sure to enter names that will sort the files in the correct order. This usually requires starting the file name with a number - starting with leading zeros if necessary.)

* export the labels as `audacity_labels_out.txt`

* run `audacity_to_mp3splt.py`

This creates a folder with mp3 files for the chapters. The names are like they were entered in Audacity.

## _War and Peace_ example

The example of `audacity_labels_out.txt` is for the 61 hour [recording of _War and Peace_](https://www.audible.com/pd/Classics/War-and-Peace-Audiobook/B002V0PVJC) (translated by Garnett, read by Davidson). For this book the times from the chapter table are not much help. In the Audacity screenshot it can be seen, that the start label for chapter 4 in part 9 is five minutes before the actual start on the right of the image.

![audacity screenshot](http://paste.watchduck.net/1709/war_and_peace_audacity.png)
