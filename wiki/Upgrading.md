The new version 2 brings some cool new features and a simplified api.

All the previous file configuration functions like `identifier`, `metadata`, `filename`, `chunkSize` and `root` were removed in favor of a single function named `file`. 

Unlike the previous versions callbacks are not supported in the new configuration function, it is invoked with only the `req` and `file` parameters. If you need to 
do some asynchronous work you have to return promises.

It is now possible to start receiving files without waiting for the connection to open. This module will handle incoming files and store them as soon as is opened.

The dependency on `gridfs-stream` was removed. The reason for this is that the module is a nice wrapper around GridStore but this feature has been deprecated since mongodb 2.2. If you still need an older mongodb version for some reason this is not a problem; this module will fall back to GridStore and deal with the differences internally.

Another feature of using `gridfs-stream` was the ability to reuse the connection to the database. This is still possible but using the `db` object directly. This
allows you to deal only with the familiar mongodb objects instead of forcing you to learn a new api to deal with GridFs and use the new and improved GridFSBucket
class.

The `grid` property of uploaded files was removed and all it's properties were merged with the file object. This removes the need for deep property lookup to
access file information.

Logging configurations were removed in an effort to make the api as simple as possible. If you are looking for a way to debug your files use events instead.
