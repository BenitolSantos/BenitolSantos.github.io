---
layout: post
title:      "Relationships are hard."
date:       2018-05-24 16:16:12 +0000
permalink:  relationships_are_hard
---


So are programming relationships. BAD DUM TISSHHH.

No but seriously. This was ridiculously confusing at first. 


![](https://scontent-sea1-1.cdninstagram.com/vp/aea3e95543706b62832543ab742d77bf/5BA39261/t51.2885-15/e35/12530737_702695059873625_1358105965_n.jpg?ig_cache_key=MTE1Njg4NDk0Mzc1NjEzNjc5NQ%3D%3D.2)



This is an artist class.


class Artist
  attr_accessor :name, :genre #no need for initialization check the spec.
  #its like a baby. the name isn't given while it's in the womb.
  #but when it is born.
  #when the method is called... then the connection are made between
end

This is a song class.

class Song
  attr_accessor :title, :artist
  #the specs are using both classes and connecting them together.
end


Eventually they are connected together by their attributes.
Their attributes are first initialized, then can be set and get.

And then you need to connect their the Song class attribute to a @songs array in Artist.
And Artist to an an :artist attribute in the class Song.



just take a look at this mess. *song_name used to be song too.

def add_song_by_name(song_name)
    song = Song.new(song_name) #initializing a new song with a song_name
    song.artist = self #self becaust the new instance of the class Artist is
    #the attribute artist of the song class
    @songs << song #push it  then check the song class
    @@song_count += 1
  end
	
	Thats how the pain began. Because now you have Song. @songs. and song and song_name. But if we take it apart piece by piece we can see what is happening.
	
	song is a new instance of the class Song. (song is a version of Song. how shocking)
	song is being initialized with a name because the initialize method in the Song class accepts a name as a parameter.
	
	  def initialize(name)
    @name = name
  end
	
	songs artist attribute is now being as the Artist class itself which is used. 
	
	Thats just a one way street. Once inheritance and through come in, it only gets harder to look at from there. But I'll give one tip. Visualize a bridge. Two sides connected by one path. 
	
	Those bridges connnects in three ways.
	
	One to one.
	Many to one.
	Many to many.












