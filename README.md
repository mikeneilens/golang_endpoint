# golang_endpoint

After playing around with go for a bit I tried the tuturial on how to create a webservice using gin package. https://go.dev/doc/tutorial/web-service-gin

I tried a few things not in the tuturial:
+ I created a new type called AlbumSlice to represent the slice (aka mutable array) of Albums.
+ I then created a function to find an album with a particular ID in an AlbumSlice using a receiver method instead of a standard function that acccesses the global albums.
+ I created the function so that it returned either a pointer to the album or nil as structs can't be nil. I used an if statement like this `if albumPtr := albums.findAlbum(id); albumPtr != nil { ... do some stuff} ` as it deals with the potential danger of the nil quite nicely. The variable called albumPtr is only accessable within the if statement so a nice way to stop the dangerous nil leaking into the code. I checked whether variable assignmetns in Go return a value and they don't.

It may be nicer to have Album and/or AlbumSlice in their own file (with the method renamed as FindAlbum). I don't know if I will get round to it, but it would interesting to know how to Mock the gin context and then add some unit tests that work with that instead of the real gin context.
