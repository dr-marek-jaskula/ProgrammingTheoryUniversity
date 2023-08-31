## Remove Fields

To remove field we use operator **$unset**.

The value for unset field is redundant (can be anything). Therefore, we usually use empty string.

> db.users.updateMany({isSporty: true}, {$unset: {phone: ""}})