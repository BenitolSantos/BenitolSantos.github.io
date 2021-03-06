---
layout: post
title:      "Music Library Cli "
date:       2018-06-23 22:18:38 -0400
permalink:  music_library_cli
---


![](https://files.slack.com/files-pri/T04EWF8CP-FBCLLEV2S/image.png)

So far I've been working a long time on this music library cli.

Its been fun to say the least.

Lets just say its like everything I've learned in OOP Ruby and then some.

There's like over a hundred tests. 

But its a nice refresher before the big giant cli project.

How do you eat an elephant? One bite at a time

It took me two weeks. 

but I finally did it.

I'd explain what it is and how I did it. But these two vids helped alot.


https://instruction.learn.co/student/video_lectures#/193

https://instruction.learn.co/student/video_lectures#/195

And a special thanks to Erika Hughes for helping me with the final part. <3



106 examples, 0 failures

Here's all the tests and pain


Song
  #initialize
    accepts a name for the new song
  #name
    retrieves the name of a song
  #name=
    can set the name of a song
  @@all
    is initialized as an empty array
  .all
    returns the class variable @@all
  .destroy_all
    resets the @@all class variable to an empty array
  #save
    adds the Song instance to the @@all class variable
  .create
    initializes and saves the song


Artist
  #initialize
    accepts a name for the new artist
  #name
    retrieves the name of an artist
  #name=
    can set the name of an artist
  @@all
    is initialized as an empty array
  .all
    returns the class variable @@all
  .destroy_all
    resets the @@all class variable to an empty array
  #save
    adds the Artist instance to the @@all class variable
  .create
    initializes and saves the artist
		
		Genre
  #initialize
    accepts a name for the new genre
  #name
    retrieves the name of a genre
  #name=
    can set the name of a genre
  @@all
    is initialized as an empty array
  .all
    returns the class variable @@all
  .destroy_all
    resets the @@all class variable to an empty array
  #save
    adds the Genre instance to the @@all class variable
  .create
    initializes and saves the genre
		
		Associations — Song and Artist:
  Artist
    #initialize
      creates a 'songs' property set to an empty array (artist has many songs)
    #songs
      returns the artist's 'songs' collection (artist has many songs)
  Song
    #initialize
      can be invoked with an optional second argument, an Artist object to be assigned to the song's 'artist' property (song
belongs to artist)
    #artist
      returns the artist of the song (song belongs to artist)
    #artist=
      assigns an artist to the song (song belongs to artist)
  Artist
    #add_song
      assigns the current artist to the song's 'artist' property (song belongs to artist)
      does not assign the artist if the song already has an artist
      adds the song to the current artist's 'songs' collection
      does not add the song to the current artist's collection of songs if it already exists therein
  Song
    #artist=
      invokes Artist#add_song to add itself to the artist's collection of songs (artist has many songs)
    #initialize
      invokes #artist= instead of simply assigning to an @artist instance variable to ensure that associations are created up
on initialization

Associations — Song and Genre:
  Genre
    #initialize
      creates a 'songs' property set to an empty array (genre has many songs)
    #songs
      returns the genre's 'songs' collection (genre has many songs)
  Song
    #initialize
      can be invoked with an optional third argument, a Genre object to be assigned to the song's 'genre' property (song belo
ngs to genre)
    #genre
      returns the genre of the song (song belongs to genre)
    #genre=
      assigns a genre to the song (song belongs to genre)
      adds the song to the genre's collection of songs (genre has many songs)
      does not add the song to the genre's collection of songs if it already exists therein
    #initialize
      invokes #genre= instead of simply assigning to a @genre instance variable to ensure that associations are created upon
initialization

Associations — Artist and Genre:
  Artist
    #genres
      returns a collection of genres for all of the artist's songs (artist has many genres through songs)
      does not return duplicate genres if the artist has more than one song of a particular genre (artist has many genres thr
ough songs)
      collects genres through its songs instead of maintaining its own @genres instance variable (artist has many genres thro
ugh songs)
  Genre
    #artists
      returns a collection of artists for all of the genre's songs (genre has many artists through songs)
      does not return duplicate artists if the genre has more than one song by a particular artist (genre has many artists th
rough songs)
      collects artists through its songs instead of maintaining its own @artists instance variable (genre has many artists th
rough songs)
Song
  .find_by_name
    finds a song instance in @@all by the name property of the song
  .find_or_create_by_name
    returns (does not recreate) an existing song with the provided name if one exists in @@all
    invokes .find_by_name instead of re-coding the same functionality
    creates a song if an existing match is not found
    invokes .create instead of re-coding the same functionality

Concerns::Findable
  defines a module named Concerns::Findable
Artist
  extends the Concerns::Findable module
Genre
  extends the Concerns::Findable module

Concerns::Findable
  .find_by_name
    is added as a class method to classes that extend the module
    isn't hard-coded
    works exactly like a generic version of Song.find_by_name,
      searching the extended class's @@all variable for an instance that matches the provided name
  .find_or_create_by_name
    is added as a class method to classes that extend the module
    works exactly like a generic version of Song.find_or_create_by_name:
      finds (does not recreate) an existing instance with the provided name if one exists in @@all
      isn't hard-coded
      invokes .find_by_name instead of re-coding the same functionality
      invokes the extended class's .create method, passing in the provided name, if an existing match is not found

MusicImporter
  #initialize
    accepts a file path to parse MP3 files from
  #path
    retrieves the path provided to the MusicImporter object
  #files
    loads all the MP3 files in the path directory
    normalizes the filename to just the MP3 filename with no path
Song
  .new_from_filename
    initializes a song based on the passed-in filename
    invokes the appropriate Findable methods so as to avoid duplicating objects
  .create_from_filename
    initializes and saves a song based on the passed-in filename
    invokes .new_from_filename instead of re-coding the same functionality
		
		MusicImporter
  #import
    imports the files into the library by invoking Song.create_from_filename
MusicLibraryController
  #initialize
    accepts one argument, the path to the MP3 files to be imported
    creates a new MusicImporter object, passing in the 'path' value
    the 'path' argument defaults to './db/mp3s'
    invokes the #import method on the created MusicImporter object
  #call
    welcomes the user
    asks the user for input
    loops and asks for user input until they type in exit
MusicLibraryController - CLI Methods
  #list_songs
    prints all songs in the music library in a numbered list (alphabetized by song name)
    is not hard-coded
  #list_artists
    prints all artists in the music library in a numbered list (alphabetized by artist name)
    is not hard-coded
  #list_genres
    prints all genres in the music library in a numbered list (alphabetized by genre name)
    is not hard-coded
  #list_songs_by_artist
    prompts the user to enter an artist
Please enter the name of an artist:
    accepts user input
    prints all songs by a particular artist in a numbered list (alphabetized by song name)
    does nothing if no matching artist is found
  #list_songs_by_genre
    prompts the user to enter a genre
		
		Please enter the name of a genre:
    accepts user input
    prints all songs by a particular genre in a numbered list (alphabetized by song name)
    does nothing if no matching genre is found
  #play_song
    prompts the user to choose a song from the alphabetized list output by #list_songs
Which song number would you like to play?
    accepts user input
    upon receiving valid input 'plays' the matching song from the alphabetized list output by #list_songs
    does not 'puts' anything out if a matching song is not found
    checks that the user entered a number between 1 and the total number of songs in the library
MusicLibraryController - CLI Commands
  'list songs'
    triggers #list_songs
  'list artists'
    triggers #list_artists
  'list genres'
    triggers #list_genres
  'list artist'
    triggers #list_songs_by_artist
  'list genre'
    triggers #list_songs_by_genre
  'play song'
    triggers #play_song
		
		


