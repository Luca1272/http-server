Simple HTTP Server in C
This is my first attempt at creating an HTTP server in C. The server can handle basic GET and POST requests, and supports gzip compression for echo responses.

Features
GET Requests:

Serve files from a specified directory.
Echo messages with optional gzip compression.
Return user-agent information.
POST Requests:

Save the body of the request to a file in the specified directory.
Dependencies
zlib: For gzip compression.
pthread: For handling multiple client connections simultaneously.

Compilation
To compile the server, use the following command:
gcc -o http_server http_server.c -lpthread -lz

Functions
gzip_deflate: Compresses data using gzip.
handle_request: Handles incoming client requests.
main: The main function that sets up the server and handles incoming connections.

Handling Requests
GET /files/: Serves files from the specified directory.
GET /echo/: Echoes the message back to the client. If the client supports gzip encoding, the response is compressed.
GET /user-agent: Returns the user-agent string sent by the client.
POST /files/: Saves the request body to a file in the specified directory.

Multi-threading
Each client request is handled in a separate thread to allow multiple simultaneous connections. The pthread library is used for thread creation and management.


Example
GET Request to Echo Message:
curl http://localhost:4221/echo/Hello

POST Request to Save Data:
curl -X POST -d "This is the data" http://localhost:4221/files/data.txt

Get User-Agent:
curl http://localhost:4221/user-agent

This project has been a learning experience in socket programming, multi-threading, and working with HTTP protocols in C. Further improvements could include better error handling, support for more HTTP methods, and enhanced security features.