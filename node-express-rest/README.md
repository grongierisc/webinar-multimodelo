# Description of the project

In this example we use node.js and access Globals directly from InterSystems IRIS to establish, retrieve and delete stored data. We build a REST API that is able to receive GET, POST and DELETE from a custom JSON object and structure its properties in InterSystems IRIS Globals.

This project uses:
Express Web server (<https://expressjs.com/>)

By default according to the configuration the server is raised on port 8000 and the base URL is:
 <http://localhost:8000/api/test>.

You can try it next:

URL | Description
--- | -----------
GET /api/test/:id | Retrieves an object with the specified id
GET /api/test| Retrieves all stored objects
POST /api/test| Creates a new object, the object is an arbitrary JSON object
POST /api/test/:id | Updates the object with the specified id
DELETE /api/test/:id| Deletes the object with the specified id

In general the API returns:

CODE | Description
---- | -----------
200 | Updated OK
201 | Created OK
404 | Object with specified id not found
500 | Server error

## How to test this example

**npm** retrieves all packages for you except *iris.node* which must be copied manually. So we should copy the file iris.node to the folder `/node_module/iris` (create the directory if it doesn't exist previously).

The file iris.node can be obtained from WRC or also from the /bin directory of an InterSystems IRIS instance (be careful because it is binary and depends on the specific IRIS distribution).

Be careful and check that the file of the copied adapter is a version compatible with the version of our installation of node. In my case I'm using the **node v8.12.0** version so I'll need the `iris800.node` file (the idea is that version 8 of node matches the first number in the filename of the adapter). Remember to rename the file to iris.node when copying it to the folder.

After getting and copying the adapter it is very important to properly configure the connection parameters to an IRIS instance that are in the `/config/config.js` file. Once configured we can test the connectivity with the following command:

```bash
npm install
node ./tests/test.js
```

Once we confirm that the connectivity is correct, execute the following command to start the server:

```bash
npm start
```

From now on we can start testing HTTP invocations:

Create a new object

```bash
curl -d '{"key1": "value1", "key2": "value2"}' -H "Content-Type: application/json" -X POST http://localhost:8000/api/test
```

Update an existing object

```bash
curl -d '{"key1": "abc", "key2": "abc"}' -H "Content-Type: application/json" -X POST http://localhost:8000/api/test/1
```

Retrieve all objects

```bash
curl http://localhost:8000/api/test
```

Retrieve a specific object

```bash
curl http://localhost:8000/api/test/1
```

Delete an existing object

```bash
curl -X DELETE http://localhost:8000/api/test/1
```
