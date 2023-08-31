## Mongo import

After instaling a tool to import we can use "mongoimport" in the powerShell:

Import CSV, TSV or JSON data into MongoDB. If no file is provided, mongoimport reads from stdin.

1. Navigate to the directory where we have our "tv-shows.json"
```
mongoimport .\tv-shows.json -d movieData -c movies --jsonArray --drop
```

This command will use or create the "movieData" database (-d parameter), and use or create (-c) movies collection.

Option --jsonArray will say that we have multiple documents to insert.

Option --drop will say to drop and recreate the movies collection