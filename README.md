# SailsBasicViewsProject

This simple Sails project shows you how you can take avantage of the powerful
[Blueprint API](http://sailsjs.org/documentation/reference/blueprint-api).

We have [one model](./api/models/Article.js) defined as follows:

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

In the [corresponding controller](./api/controllers/ArticleController.js), we
just have created a `new` that allows the Blueprint action routes to create
a route to `/article/new`.

Now, the interesting things take place in [the views folder](./views/)...