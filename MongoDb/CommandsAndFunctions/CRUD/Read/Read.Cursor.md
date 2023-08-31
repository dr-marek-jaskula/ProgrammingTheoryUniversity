## Cursor

We get result with cursor of the next document.

To get the next document we use the .next() method.

1. Store the cursor in the variable
```
const dataCursor = db.movies.find()
```
we can use .next() to get next data
```
dataCursor.next()
```

Other methods of cursor (from current point of the cursor):

.forEach(doc => {printjson(doc)})

If we call .next() when we fetch all data, we would get error
```
MongoCursorExhaustedError: Cursor is exhausted
```

to check this we can use method .hasNext()

we can use this like that
```
while (myCursor.hasNext()) {
   print(tojson(myCursor.next()));
}
```

Cursors that aren't opened under a session automatically close after 10 minutes of inactivity, or if client has exhausted the cursor.



