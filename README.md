# SailsBasicViewsProject

This simple Sails project shows you how you can take avantage of the powerful
[Blueprint API](http://sailsjs.org/documentation/reference/blueprint-api).

## The Blueprint API

When you use the API generator (`sails generate api <foo>`), the only 2 things
that gets created are:

* an empty model (<Foo>.js)
* an empty controller (<Foo>Controller.js)

You didn't write any controller "action" (a method in the controller),
any routes...

But when you lift your project (`sails lift`), you can already do some crud
actions, right? Well, that's where the Blueprint API comes into play.

### The Blueprint Routes

#### Blueprint RESTful Routes

They expose a conventional REST API on top of a controller's `find`, `create`,
`update`, and `destroy` actions. 

* *GET http://localhost:1337/<foo>*: list the existing <foo>s
* *GET http://localhost:1337/<foo>/<id>*: get the <foo> with id <id>
* *POST http://localhost:1337/<foo>*: create a new <foo>
* *PUT http://localhost:1337/<foo>/<id>*: update the <foo> with id <id>
* *DELETE http://localhost:1337/<foo>/<id>*: delete the <foo> with id <id>

You can disable them in `config/blueprints.js` and set `rest` to `false`.

#### Blueprint Shortcut Routes

They allow you to access to a controller's CRUD actions from your browser's
URL bar. **Don't forget to disable them in production.**

* *GET http://localhost:1337/<foo>*: list the existing <foo>s
* *GET http://localhost:1337/<foo>/<id>*: get the <foo> with id <id>
* *GET http://localhost:1337/<foo>/create?<attr1>=<val1>&<attr2>=<val2>*:
create a new <foo>
* *GET http://localhost:1337/<foo>/update/<id>?<attr1>=<val1>*: update the
<attr1> of the <foo> with id <id>
* *GET http://localhost:1337/<foo>/destroy/<id>*: delete the
<foo> with id <id>

You can disable them in `config/blueprints.js` and set `shortcuts` to `false`.

#### Blueprint Action Routes

The eliminate the need to manually bind routes for a controller's action.
**Warning**, GET, POST, PUT, and DELETE routes will be generated, don't forget
to limit these in production.

You can disable them in `config/blueprints.js` and set `action` to `false`.

### The Blueprint Actions

These are basic actions binded to a controller if you've used the API generator
Here is the list of actions concerned:

* find
* findOne
* create
* update
* destroy
* populate
* add
* remove

You can update or override the Blueprint Actions in the /api/blueprints folder
(checkout [the docs](http://sailsjs.org/documentation/reference/blueprint-api)
for more informations).

## The project

As we said, we used the API generator to create
[one model](./api/models/Article.js) defined as follows:

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
just have created a `new` action that allows the Blueprint action routes to
create a route to `/article/new`.

Now, the interesting things take place in [the views folder](./views/)...