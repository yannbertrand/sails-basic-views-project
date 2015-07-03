# SailsBasicViewsProject

This simple Sails project shows you how you can take avantage of the powerful
[Blueprint API](http://sailsjs.org/documentation/reference/blueprint-api).

## The Blueprint API

When you use the API generator (`sails generate api <foo>`), the only 2 things
that gets created are:

* an empty model (&lt;Foo&gt;.js)
* an empty controller (&lt;Foo&gt;Controller.js)

You didn't write any controller "action" (a method in a controller),
any routes...

But when you lift your project (`sails lift`), you can already do some crud
operations, right? Well, that's where the Blueprint API magic comes into play.

### The Blueprint Routes

By default, some params are activated. You can disable each of them in the
`config/blueprints.js` file.

Each of them allows you to automatically create routes and bind them to your
controllers' actions at the launching of the server (`sails lift`).

Let's see them in details.

#### Blueprint RESTful Routes

They expose a conventional REST API on top of a controller's `find`, `create`,
`update`, and `destroy` actions. 

* *GET http://localhost:1337/&lt;foo&gt;*: list the existing &lt;foo&gt;s
* *GET http://localhost:1337/&lt;foo&gt;/&lt;id&gt;*: get the &lt;foo&gt;
with id &lt;id&gt;
* *POST http://localhost:1337/&lt;foo&gt;*: create a new &lt;foo&gt;
* *PUT http://localhost:1337/&lt;foo&gt;/&lt;id&gt;*: update the &lt;foo&gt;
with id &lt;id&gt;
* *DELETE http://localhost:1337/&lt;foo&gt;/&lt;id&gt;*: delete the &lt;foo&gt;
with id &lt;id&gt;

You can disable them by setting the `rest` param to `false`.

#### Blueprint Shortcut Routes

They allow you to access to a controller's CRUD actions from your browser's
URL bar. **Don't forget to disable them in production.**

* *GET http://localhost:1337/&lt;foo&gt;*: list the existing &lt;foo&gt;s
* *GET http://localhost:1337/&lt;foo&gt;/&lt;id&gt;*: get the &lt;foo&gt;
with id &lt;id&gt;
* *GET
http://localhost:1337/&lt;foo&gt;/create?&lt;attr1&gt;=&lt;val1&gt;&&lt;attr2&gt;=&lt;val2&gt;*:
create a new &lt;foo&gt;
* *GET
http://localhost:1337/&lt;foo&gt;/update/&lt;id&gt;?&lt;attr1&gt;=&lt;val1&gt;*:
update the &lt;attr1&gt; of the &lt;foo&gt; with id &lt;id&gt;
* *GET http://localhost:1337/&lt;foo&gt;/destroy/&lt;id&gt;*: delete the
&lt;foo&gt; with id &lt;id&gt;

You can disable them by setting the `shortcuts` param to `false`.

#### Blueprint Action Routes

The eliminate the need to manually bind routes for a controller's action.
**Warning**, GET, POST, PUT, and DELETE routes will be generated, don't forget
to limit these in production.

You can disable them by setting the `action` param to `false`.

### The Blueprint Actions

These are basic actions binded to a controller if you've used the API generator.
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