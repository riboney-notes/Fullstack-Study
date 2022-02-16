# Mongoose Notes

## Misc

- To enforce field is unique, need to set `unique` to true and wait for the index to build using `Model.on(index)` event
  - See [link](https://mongoosejs.com/docs/faq.html#unique-doesnt-work)
  > In a production environment, you should create your indexes using the MongoDB shell rather than relying on mongoose to do it for you. [link](https://docs.mongodb.com/manual/reference/method/db.collection.createIndex/)

## Validation
- You can manually run validation using `docVaidate(cb)` or `doc.validateSync()`
- 
