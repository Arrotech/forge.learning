# Forge Learning

To view tutorials, please visit [forgetutorials.autodesk.io](http://forgetutorials.autodesk.io). This repository is for creating the tutorials.

# Adding a new language

Create a project in the programming language that supports the UI described on [Viewer](viewer/readme.md) front-end. In summary, the back should implement:

 - GET **/api/forge/oauth/token**: return a valid access token in the form of `{'access_token':value, 'expires_in':value}`
 - POST **/api/forge/oss/buckets**: create a new bucket, receive input in the form of `{'bucketKey': 'theKey'}` and return 200.
 - GET **/api/forge/oss/buckets**: return all buckets or objects in form of list of nodes: 

```json
[
  {
   'id':'bucketKey|objectNameAsURNBase64',
   'text':''bucketKey|objectName',
   'type': 'bucket|object',
   'children': true|false
  }
]
```
It receives a querystring with `id`: if **#** return all buckets, if a **bucketKey** all objects for the bucket.

 - POST **/api/forge/oss/objects**: receive a file and `bucketKey` as a `multipart/form-data`. For simplicity, non-resumable.
 - POST **/api/forge/modelderivate/jobs**: translate the file, receive input in the form of `{'bucketKey': 'theKey', 'objectName': 'theName'}`

For reference, when adding a new language, replicate all `net.md` for the new language. The **Viewer** section should be the same for all languages.

The project should be named `forge.learning.TUTORIAL.LANGUAGE`, for instance, `forge.learning.viewmodels.net` or `forge.learning.viewmodels.nodejs`. Tutorial project should be ready to use and include a readme. 

Use convention:

- PORT: 3000
- FORGE\_CLIENT\_ID
- FROGE\_CLIENT\_SECRET
- FORGE\_CALLBACK\_URL: default `http://localhost:3000/api/forge/oauth/callback`

> This is importat so developers can reuse this with other samples on **Autodesk-Forge** Github.

### Animated GIFs

Whenwhere applicable, use animaged GIF to demonstrate a complex setup. Good results with [EZGIF](https://ezgif.com/video-to-gif) in 5FPS (smaller).

# Running locally

Install `docsify`:

```bash
npm i docsify-cli -g
```

Clone this project.

Now serve the `/docs` folder:

```bash
docsify serve ./docs
```

Open `http://localhost:3000`

# License

This sample is licensed under the terms of the [MIT License](http://opensource.org/licenses/MIT). Please see the [LICENSE](LICENSE) file for full details.