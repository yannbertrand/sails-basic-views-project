# SailsBasicViewsProject

This simple project shows you how you can take avantage of the Sails Blueprint
API.

We just have one model defined as follows:

```javascript
// Article.js

module.exports = {

  schema: true,
  attributes: {

    title: {
      type: 'string',
      required: true,
      unique: true
    },

    content: {
      type: 'text',
      required: true
    }

  }
};
```

Now, the interesting thing take place in [the views folder](./views/)...