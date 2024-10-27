## Introduction

This is a proof of concept project for something I have wanted to solve for a long time. Saving and organising music in YouTube or Spotify sucks. For most people I’m sure it is fine, but I’m not most people: I want something that is not dependent on any particular platform, that is intuitive and easy to use, and that supports tagging.

It just so happens that, as part of my degree course, I am taking a module on building a web app using Java Spring Boot, and I could do with a personal project to try stuff out on and experiment with while I learn, and this seemed like a perfect fit (or at the very least, it will give me a good idea of what not to do).

## Inspiration

A couple of years back I started recording songs that I liked or that got stuck in my head in an Excel spreadsheet; since then it has reached over 1000 songs. I listen to most of my music on YouTube, and this is for a few main reasons: not all of the songs I listen to are available through a dedicated app like YouTube Music or Spotify, and I listen to music almost entirely on my laptop where I make full use of browser tabs and video queuing to separate and organise the songs I am currently listening to. This makes it really easy for me to keep music for different moods readily available.

Originally, I had used a single YouTube playlist to save songs, but this had some problems: a single playlist is really hard to query and organise, and sometimes videos just disappear meaning I loose the record of the song with it (often the case if I didn’t/couldn’t find the original artist and save their video). Ideally, I need a way to save and organise music that is not reliant on a particular platform, and would support easy creating and playing of playlists, especially on desktop. My hope is that this project goes a small way in realising this goal.

## Current Goals

1. To build a RESTful API using Java Spring Boot that can be used to interact with a database through a web interface
    - To properly implement authentication using standard libraries
    - To make use of JUnit and Postman to fully test the API before deployment
2. To design and configure a MySQL database, that initially will run locally but can later be deployed in Microsoft Azure
3. To experiment using Docker for running services in containers, and deploying this in Azure, too

## Key Requirements

- To be able to store songs as records, alongside various information about them:
    - Song Name
    - Song Variant (for if it is a cover, live version, etc.)
    - Artist(s) involved (could have a band, a collab, a main person ft. someone else)
    - Album(s) it is part of (supports ordered tracks)
    - Link to song on YouTube, Spotify, etc.
    - Related Tags
    - Date Added
    - Notes on that song
- To be able to edit and add information to a particular song record
- To be able to search for songs, and have a list returned - should be able to search for any information related to that song, for example an artist or album
- To be able to search for artists, albums, etc. and view pages for these where they can be updated, as well as see the various songs, albums, etc. associated with them
- To be able to edit the list of tags available and add new tags
- To be able to add songs to playlists which are dated and can be named (supports ordered tracks)
- To be able to navigate between songs using related artists, albums, tags and playlists

## Notes & Observations

- Tagging is a way to group songs by genre or mood, such as “80s” or “Unhinged”. Any song can be given any number of tags
- Playlists are an additional feature designed to create associations between songs that could be listened to together, but don’t have a clear theme that groups them - it is a manual alternative of what YouTube or Spotify does when it suggests further songs you usually listen to when
- The notes stored on a song would probably be better stored in a non-relational way, which would require either multiple databases (one relational, one non-relational) or a database solution which supports both structured and unstructured data, such as Azure Cosmos DB - this may become especially helpful if song lyrics were also to be stored.
- In the future, the goal would be to be able to add songs to a playlist through this application, then have them play somehow, either pulling them from YouTube, or by opening a playlist or album open in YouTube with all of the songs queued up.
- A browser extension might be a good way to interface with this program, as it would allow for interaction between the page I’m listening to songs on: it could track the song I’m listening to and use the sequence I play songs to create automatic associations between songs I often pay together. Plus it might be able to “plug into” the website and to make actions such as queuing songs easier.