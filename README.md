# Long Practice: API Docs for a Music Archive

In this practice, you will document the request and response components for
API endpoints of a music archive server.

## Set up

Clone the practice from the [starter].

To set up the server that you will test your endpoints on, run `npm install`
inside of the __server__ folder. Please do not to look at the contents of the
__server__ folder until you finish this project.

To start the server, run `npm start` inside of the __server__ folder. This will
allow you to make requests to [http://localhost:5000] using any client (browser
and Postman).

To stop the server from listening to requests, press `CTRL + c` for
Windows/Linux or `CMD + c` for MacOS in the terminal that you started the server
(wherever you ran `npm start`).

## Resources

Below is a list of all the resources for this music archive server.

- artists:
  - artistId: unique identifier
  - name
- albums:
  - albumId: unique identifier
  - name
  - artistId: of the artist that released the album
- songs:
  - songId: unique identifier
  - name
  - lyrics
  - trackNumber: the order of the song in its album
  - albumId: of the album that the song was released with

## Documentation

The music archive server receives JSON request bodies and returns JSON response
bodies.

Below is a list of operations on the music archive server that you can perform.
For each operation, document what the components of the request should be and
what you should expect from the response. Document all the important components
of the request and the response. You can use a Google doc, VSCode for editing
a text/markdown file, or whatever text editor you want for creating the
API routes documentation for this music archive server.

Here's how to approach creating the documentation for the music archive server
operations:

1. Make a prediction based off of your knowledge of HTTP request and response
   components and API routes to determine what the request and response
   components of the given operation should be.
2. Formulate the request using Postman and submit the request to see what the
   response is. The music archive server can be accessed at
   [http://localhost:5000].
3. If the request or response is not what you predicted it to be, then update
   your documentation.

If you don't see the response you want, or if you see an error status code, then
the components of the request are wrong. Try playing around with the request
components to get closer to the response you expect.

If you get stuck, make sure to ask for help!

The request and response components to get all the artists are filled out for
you as an example.

### Get all the artists

Request components:

- Method: GET
- URL: /artists
- Headers: none
- Body: none

Response components:

- Status code: 200
- Headers:
    - Content-Type: application/json
- Body: information about all the artists
  ```json
  [
    {
      "artistId": 1,
      "name": "Red Hot Chili Peppers"
    }
  ]
  ```

Test this in Postman or by using `fetch` in the browser.

### Get a specific artist's details based on artistId

Request components:

- Method: GET
- URL: /artists/:artistId
- Headers: none
- Body: none

Response components:

- Status code: 200
- Headers:
    - Content-Type: application/json
- Body: information about the specific artist

### Add an artist

Request components:

- Method: POST
- URL: /artists
- Headers:
    - Content-Type: application/json
- Body: {
  "name": "System Of A Down"
}

Response components:

- Status code: 201
- Headers:
    - Content-Type: application/json
- Body: {
    "name": "System Of A Down",
    "artistId": 2
}

### Edit a specified artist by artistId

Request components:

- Method: PUT
- URL: /artists/:artistId
- Headers:
    - Content-Type: application/json
- Body: {
  "name": "System of a Down"
}

Response components:

- Status code: 200
- Headers:
    - Content-Type: application/json
- Body: {
    "name": "System of a Down",
    "artistId": 2,
    "updatedAt": "2024-01-16T02:12:03.759Z"
}

### Delete a specified artist by artistId

Request components:

- Method: DELETE
- URL: /artists/2
- Headers: none
- Body: none

Response components:

- Status code: 200
- Headers:
    - Content-Type: application/json
- Body: {
    "message": "Sucessfully deleted"
}

### Get all albums of a specific artist based on artistId

Request components:

- Method: GET
- URL: /artists/:artistId/albums
- Headers: none
- Body: none

Response components:

- Status code: 200
- Headers:
    - Content-Type: application/json
- Body: [
    {
        "name": "Stadium Arcadium",
        "albumId": 1,
        "artistId": 1
    }
]

### Get a specific album's details based on albumId

Request components:

- Method: GET
- URL: /albums/:albumId
- Headers: none
- Body: none

Response components:

- Status code: 200
- Headers:
    - Content-Type: application/json
- Body: information of the specified album

### Add an album to a specific artist based on artistId

Request components:

- Method: POST
- URL: /artists/:artistId/albums
- Headers:
    - Content-Type: application/json
- Body:
{
  "name": "Californication"
}

Response components:

- Status code: 201
- Headers:
    - Content-Type: application/json
- Body: {
    "name": "Californication",
    "albumId": 2,
    "artistId": 1
}

### Edit a specified album by albumId

Request components:

- Method: PUT
- URL: /albums/:albumId
- Headers: 
    - Content-Type: application/json
- Body: {
  "name": "Californication (explicit)"
}

Response components:

- Status code: 200
- Headers:
    - Content-Type: application/json
- Body: {
    "name": "Californication (explicit)",
    "albumId": 2,
    "artistId": 1,
    "updatedAt": "2024-01-16T03:28:37.719Z"
}

### Delete a specified album by albumId

Request components:

- Method: DELETE
- URL: /albums/:albumId
- Headers: none
- Body: none

Response components:

- Status code: 200
- Headers:
    - Content-Type: application/json
- Body: {
    "message": "Sucessfully deleted"
}

### Get all songs of a specific artist based on artistId

Request components:

- Method: GET
- URL: /artists/:artistId/songs
- Headers: none
- Body: none

Response components:

- Status code: 200
- Headers:
    - Content-Type: application/json
- Body: list of songs and details in an array

### Get all songs of a specific album based on albumId

Request components:

- Method: GET
- URL: /albums/:albumId/songs
- Headers: none
- Body: none

Response components:

- Status code: 200
- Headers:
    - Content-Type: application/json
- Body: list of songs and details in an array

### Get all songs of a specified trackNumber

**Note: This one is meant to be a little more challenging, but should still
follow a similar pattern to those above.**

Can you see a pattern between this endpoint and the two previous endpoints?

Hint: Think of how you solved getting all songs by a specific artist and by a
specific album. What is resource that you wanted to get back for those
endpoints? What information was that resource constrained by for each of those
endpoints? Now think about getting all songs by a specific `trackNumber`.
What is the resource you want to get? What information is the resource
constrained by for this endpoint?

Request components:

- Method: GET
- URL: /TrackNumbers/:tracknumber/songs
- Headers: none
- Body: none

Response components:

- Status code: 200
- Headers:
    - Content-Type: application/json
- Body: list of songs and details in an array

### Get a specific song's details based on songId

Request components:

- Method: GET
- URL: /songs/:songId
- Headers: none
- Body: none

Response components:

- Status code: 200
- Headers:
    - Content-Type: application/json
- Body: song details

### Add a song to a specific album based on albumId

Request components:

- Method: POST
- URL: /album/:albumId/songs
- Headers:
    - Content-Type: application/json
- Body: {
  "name": "Scar Tissue"
}

Response components:

- Status code: 201
- Headers:
    - Content-Type: application/json
- Body: {
            "name": "Snow (Hey Oh)",
            "lyrics": null,
            "trackNumber": null,
            "songId": 2,
            "createdAt": "2024-01-16T03:43:55.983Z",
            "updatedAt": "2024-01-16T03:43:55.983Z",
            "albumId": 1
        }

### Edit a specified song by songId

Request components:

- Method: PUT
- URL: /songs/:songId
- Headers:
    - Content-Type: application/json
- Body: {
  "trackNumber": 2
}

Response components:

- Status code: 200
- Headers:
    - Content-Type: application/json
- Body: {
    "name": "Snow (Hey Oh)",
    "lyrics": null,
    "trackNumber": 2,
    "songId": 2,
    "albumId": 1,
    "updatedAt": "2024-01-16T03:46:17.370Z"
}

### Delete a specified song by songId

Request components:

- Method: DELETE
- URL: /songs/:songId
- Headers: none
- Body: none

Response components:

- Status code: 200
- Headers:
    - Content-Type: application/json
- Body: {
    "message": "Sucessfully deleted"
}

[http://localhost:5000]: http://localhost:5000
[starter]: https://github.com/appacademy/practice-for-week-08-music-archive-docs-long-practice