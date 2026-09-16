# obsidian-couchdb

A quick deployment of [CouchDB](https://docs.couchdb.org/en/stable/) on [Render](render.com) for use with [obsidian-livesync](https://github.com/vrtmrz/obsidian-livesync)

## Deploy on Render

1. Create a new [Web Service using Docker](https://render.com/docs/docker) using this public git repository `https://github.com/jjamesstark/obsidian-couchdb`or your fork. 
2. Name your service
3. Leave the default configurations (except free should be sufficient)
4. Add Environment Variables `COUCHDB_USER` and `COUCHDB_PASSWORD` your CouchDB deployment
  - you will use these to authenticate for database creation and setting up LiveSync in Obsidian
5. Deploy!

## Create Database

Once your deployment is up render provides a public URL for the service. You can verify it with something like

```bash
curl -u username:password https://your-service.onrender.com/_node/_local/_config
```

 which should return the configuration details for your couch db instance, which means you're ready to create your CouchDB database (needed within the Self-Hosted LiveSync configuration)

```bash
curl -X PUT username:password https://your-service.onrender.com/your-db-name
```

very it's creation with

```bash
curl -u username:password https://your-service.onrender.com/_all_dbs
```

you should a use a new database for each vault you're syncing

Now you should be ready to set up Self-hosted LiveSync using [the CouchDB quick Setup](https://github.com/vrtmrz/obsidian-livesync/blob/main/docs/quick_setup.md#configure-couchdb-manually-on-the-first-device) using the `Configure a remote manually` option.
