# Notes
* is a note
# Explainations
` is a explanation to describe!`

# Need to do
Need to remove the streamers functionality of the websocket as the streamers dont interact via the websocket anymore and instead use the http server to stream the video files.

So we need to implement a auto deletion of the tmp folder on crashes or shutdowns or such events.

Also need to implement a way to store the full video data in the database. potentially for reconstructions later maybe in the future....

Need to implement a way to limit the tmp folder size so broadcasters cant fill it up past a certain set amount. and need to have the broadcasters handle the cancel request. properly in the future maybe come up with a status call they can check the status of the size to ensure there is enough space.

Also need to make sure the broadcasters only stream when they are requested using a seperate server like sse to ensure they don't flood the server with multiple requests. which thankfully using the providerId is a potential way to do this in the future. which the sse server already has implemented. But be sure not to restructure it where it will break this concept of protection.

Need to update to auto delete video files based on tv show or movie type. to ensure different serving times for different types. such as for movies 4 hours and tv shows 1 hours.

Come up with a database to store the full video data buffer. to collect from later again if the streamer is still requesting later on to ensure serving also potentially may include backup database providers which store the buffer video data. in a sqlite database. to ensure it is not lost and can be brought up again.

by making a databaseProviders connections on the websocket we can relay all broadcasts to all database providers. who may want to cache video data and lazy provide movies and tv shows. from the relaying of all chunk data. to databaseProviders we can ensure backup providing via the databaseProviders. and those providers can provide without actually having to do anything... besides running a program and modifying a config file to set the max size of the database folder. which me would have to come up with a seperate chunking constructor to make it work by appending chunkIndex, timestamp, tmdbid, filetype, type

if its a tv show we append type=tv season=seasonNumber and episode=episodeNumber.
if its a movie we append the type=movie season=999 and episode=999. this is also how we will know its a movie.

so this way our database providers can handle the different chunking constructor for processing the data. to ensure they can provide without actually having to do anything...

# Finished
We have a video streaming server.
That serves video files via the /video endpoint. with query params:
* broadcasterId
* filetype
That stores the video files via the ./tmp/{broadcasterId}.mp4 location inside the tmp folder within the node application of the server.
We have the broadcaster code on how to send the stream to the server via websocket connection!
We have the client side streamer code via html and css using video players.