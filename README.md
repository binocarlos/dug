dug
===

A simple todo application based on digger - used as an example in the docs

##installation

The app runs as a web-page and connects to digger.io to load data.

Change the name of your warehouse on this line:

```html
<digger warehouse="binocarlos/todo-example" selector="todo:sort(name)">
```

This controls where the data is loaded from.

To clone this app - you can fork the binocarlos/todo-example warehouse and you can then write todos to the warehouse.

##How it works

### connect to digger
The page runs as a [digger](http://digger.io) angular application and so at the foot of the page we connect to digger:

```html
<script src="http://digger.io/api/v1.angularplus.js"></script>
```

This will include angular also and so we don't need that on the page.

We also include twitter bootstrap on the page.

### load data
The warehouse we are pointing to: **binocarlos/todo-example** contains **todo** models.

Each model has **done** and **important** checkboxes that set the classname accordingly.

So - we can load all todo models and filter them using the .done classname:


load the data:

```html
<digger warehouse="binocarlos/todo-example" selector="todo:sort(name)">
```

### looping and filtering the tasks
loop over things that do not have .done classname:

```html
<tr digger-repeat="filter('.done:not')">
```
### the 'importnat' label
only show the important label if the important class is present:

```html
<span ng-if="$digger.hasClass('important')" class="label label-danger">important</span>
```