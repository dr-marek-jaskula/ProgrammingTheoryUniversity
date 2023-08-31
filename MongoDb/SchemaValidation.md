## Schema Validation

Rules that enforce some conditions when we insert or update data.

1. validationLevel -> we distinguish which operation we want to validate (or which collections/documents). 
    a. off -> No validation for inserts or updates.
	b. strict -> all inserts and updates
	c. moderate -> all insert and update to valid documents (we can have some invalid, because rules were made after we added invalid ones)
2. validationAction -> what action perform on the failure	
	a. error -> deny insert or update
	b. warn -> log warning but proceed


As a validator we use $jsonSchema (it is strongly recommended)
collMod is a collection name
```mongosh
db.runCommand({
  collMod: 'posts',
  validator: {
    $jsonSchema: {
      bsonType: 'object',
      required: ['title', 'text', 'creator', 'comments'],
      properties: {
        title: {
          bsonType: 'string',
          description: 'must be a string and is required'
        },
        text: {
          bsonType: 'string',
          description: 'must be a string and is required'
        },
        creator: {
          bsonType: 'objectId',
          description: 'must be an objectid and is required'
        },
        comments: {
          bsonType: 'array',
          description: 'must be an array and is required',
          items: {
            bsonType: 'object',
            required: ['text', 'author'],
            properties: {
              text: {
                bsonType: 'string',
                description: 'must be a string and is required'
              },
              author: {
                bsonType: 'objectId',
                description: 'must be an objectid and is required'
              }
            }
          }
        }
      }
    }
  },
  validationAction: 'warn'
});

```

1. **required** make that all provided key must be there.
2. **properties** defines each required property

more: https://www.mongodb.com/docs/manual/core/schema-validation/