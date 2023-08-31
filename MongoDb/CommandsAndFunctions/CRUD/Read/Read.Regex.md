## Regex

Search on text.

Available syntaxes:
```
{ <field>: { $regex: /pattern/, $options: '<options>' } }
{ <field>: { $regex: 'pattern', $options: '<options>' } }
{ <field>: { $regex: /pattern/<options> } }
```

Options:
i -> case insensitivity
m -> include anchors like '^' at the start or '$' at the end of a line for strings with multiline values. 
x -> ignore are white space characters in the regex pattern unless escaped or included in a character class
s -> allows the dot character '.' to match all characters including newline character

NOT: You cannot use $regex operator expressions inside an $in.
Use: (example for $in with option of case insensitivity)
```
{ name: { $in: [ /^acme/i, /^ack/ ] } }
```

Examples:
```
{ name: { $regex: /acme.*corp/i, $nin: [ 'acmeblahcorp' ] } }
{ name: { $regex: /acme.*corp/, $options: 'i', $nin: [ 'acmeblahcorp' ] } }
{ name: { $regex: 'acme.*corp', $options: 'i', $nin: [ 'acmeblahcorp' ] } }
{ name: { $regex: /acme.*corp/, $options: "si" } }
{ name: { $regex: 'acme.*corp', $options: "si" } }
```

### Regular expression objects

Regular expression objects (i.e. /pattern/)
```
db.inventory.find( { item: { $not: /^p.*/ } } )
```

### $regex operator expressions
```
db.inventory.find( { item: { $not: { $regex: "^p.*" } } } )
db.inventory.find( { item: { $not: { $regex: /^p.*/ } } } )
```

LIKE: 
```
db.products.find( { sku: { $regex: /789$/ } } )
```

is Equivalent to SQL
```
SELECT * FROM products
WHERE sku like "%789";
```

With case insensitivity
```
db.products.find( { sku: { $regex: /^ABC/i } } )
```

Results:
```
[
   { _id: 100, sku: 'abc123', description: 'Single line description.' },
   { _id: 101, sku: 'abc789', description: 'First line\nSecond line' },
   { _id: 104, sku: 'Abc789', description: 'SKU starts with A' }
]
```

Have line Starting with 
```
db.products.find( { description: { $regex: /^S/, $options: 'm' } } )
```

results
```
[
   { _id: 100, sku: 'abc123', description: 'Single line description.' },
   { _id: 101, sku: 'abc789', description: 'First line\nSecond line' },
   { _id: 104, sku: 'Abc789', description: 'SKU starts with A' }
]
```

results without 'm' option
```
[
   { _id: 100, sku: 'abc123', description: 'Single line description.' },
   { _id: 104, sku: 'Abc789', description: 'SKU starts with A' }
]
```

String contains the word:
> db.movies.find({summary: {$regex: /musical/}})