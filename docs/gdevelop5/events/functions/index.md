---
title: Functions - create your own actions, conditions or expressions
---
# Functions: create your own actions, conditions or expressions

An "Events Function" or simply Function is a powerful feature of GDevelop. [External events](/gdevelop5/interface), [links](/gdevelop5/events/link) and [groups](/gdevelop5/events/group) are useful to organize the events of your game, and even reuse some, in more than one place in your game. For example, you could put common events, to manage the enemies in some external events, and include these events, using a link, in various scenes.

Functions are going one step further: they allow you to declare **new conditions**, **new actions** and even **new expressions**, using events.

When you register a function, you can choose if it's a condition, an action or an expression. The Function contains events, like a scene or external events, that will be executed when the condition or the action is launched during the game.

In addition to events, functions also have parameters, just like usual conditions, actions and expressions. The parameters can be objects, number or text.

!!! tip

    See [an example of replacing external events by functions](/gdevelop5/events/functions/replace-external-events). You can also **[automatically extract events to a function](/gdevelop5/events/functions/extract-events)**.

!!! tip

    See an example of functions being used in [this video by gamefromscratch](https://www.youtube.com/watch?v=BQO9DDXdkjs).

![type:video](https://www.youtube.com/embed/-U8WFcpUmMg)

## Creating a new function

Functions are grouped into [extensions](/gdevelop5/extensions). They are the same as [the extensions that you can install for your game](/gdevelop5/extensions/search). You can see the list of extensions that the game has, as well as add a new extension in the [Project Manager](/gdevelop5/interface/project-manager):

![](pasted/20221118-093224.png)

Click on **Create or search for new extensions** on the bottom then on **Create a new extension** to [create a new extension](/gdevelop5/extensions/create). It's a good idea to have functions related to the same thing in a single extension. Careful, the name is sensitive to the case, so `DayNightEffects` and `Daynighteffects` are two different functions.

Click on the extension in the list to open its editor. By default, there are no functions in the extensions. Add one by clicking on "Add a new function", on the left:

![](pasted/20221118-093435.png)

A new function is added. You can rename it, to give it a name according to what you want to do inside. For example, if your function will be a condition that checks if the object passed as parameter is ready to fight, you can call it `IsReadyToFight` (only alphanumeric characters and underscores are allowed in names).

Click on the function to edit it: you'll be able to change its configuration and its events.

## Editing the configuration and the events of the function

When a function is selected, on the top, you can see the configuration of the function:

![](pasted/20221118-093605.png)

* The first parameter is the type of the function: "Action", "Condition", "Expression" or "String Expression". If you choose Action or Condition, you'll find the function in the list of actions and conditions, when editing your events in the game. If you choose Expression (or String Expression), you'll find it in the list of expressions when you edit a formula.
* You can then configure the name that will be displayed in the list.
* Enter the description that will be given in the window, when choosing the parameters for the function.
* For Action or Condition, you can enter the sentence that will be displayed in the events sheet. In case your function takes parameters (see below to learn more about these), you can include them by writing `PARAMx` between underscores, replacing `x` by the parameter number (starting at 1):

```
Rotate objects _PARAM1_
```

This is an example for a function named "RotateObjects", which is an action, with the description "Rotate the given objects", and with a single parameter, the objects to be rotated.

### Parameters

Functions are becoming really useful and powerful when you use parameters. Under the configuration of the function, you can add parameters. These parameters will be available when you use the action, condition or expression in the events sheet. It's just like the usual action/condition/expressions you're used to!

Add a parameter with the button "Add a parameter":

For each parameter, you can enter:

  * The name, that will be used to access the parameter in the *events of the function*.
  * The type. Parameters can be objects, numbers, texts, etc. [See the complete list of parameters](/gdevelop5/events/functions/#references-of-parameters).
  * A description, that will be shown in the window when configuring the action/condition or expression.

For example, we can add a parameter, that would return the objects to be rotated:

![](pasted/20221118-093700.png)

!!! note

    These parameters can be used in a Javascript event, [see here how to use parameters](/gdevelop5/events/js-code#use_javascript_to_get_a_value_from_parameters) in Javascript.

### Adding the events to the function and using the parameters

When your function is configured, you can add events to it. These events will be launched when the condition, action or expression is used in the rest of the game.

* You can use all the existing events, actions, conditions and expressions, but you are limited to the **objects that you entered as parameters**. This is to ensure that your function is only acting on them, and has no "side-effects" on the rest of the game - which would be a bad practice and make functions hard to reuse and to generate.

* Note that functions can be reused everywhere, and are not limited to a scene. You **won't have the list of variables of your scenes** in them. You can still manipulate them by using the usual actions and manually writing the variable you want to modify.

* **Links** are not available in functions, because a function is autonomous and is in theory not even tied to a project.

#### Object parameter

Here is an example of a function to rotate some objects:

![](pasted/20221118-093830.png)

This is a really simple and not really useful example of a function (you could as well use the action to rotate objects directly without writing a function). But, when you add more complex logic inside, a function's strength can be seen. It's then super easy to reuse this logic from the rest of the game!

!!! note

    If your function is a condition or an expression, [use the actions in "Functions" category to set the expression/condition value](/gdevelop5/events/functions/return) (also called the "return value").

#### Other types of parameters

A parameter can be an object, a text, a number or some other kind of data (the name of a layer, a boolean, etc...). You can use expressions and conditions to access the parameters passed to a function.

* Get a number from a parameter: `GetArgumentAsNumber(string)`
* Get a text from a parameter: `GetArgumentAsString(string)`
Here is an example of a text parameter that will get the name and use it in an action for change scene.

![](/gdevelop5/events/function_text_expression.png)


## Using the function in your game

When you have configured and created the events for your function, you can use it in the rest of your game.

Simply create a new action (or condition) and find in the list the name of your extension, then choose the function that you've created:

![](pasted/20221118-094110.png)

That's it! The function is used like any other condition, action or expression in the [Events Editor](/gdevelop5/interface/events-editor).

!!! tip

    The **Object Groups** feature, while creating functions, helps grouping similar object parameters. This way you can apply an action/condition to a group of object parameters (parameters pointing at objects) at once.

## Advanced usages

This page gave a basic overview of what functions are. They are one of the more powerful features of GDevelop, as you can extend the events by using them, enabling to create very readable and concise events sheets. By using them, you can reduce the amounts of events that you write for your game, avoid copy-pasting them and even reduce bugs by ensuring that functions are always used for common tasks on your objects.

!!! tip

    Functions that focus on an object can be grouped together in [custom behaviors](/gdevelop5/behaviors/events-based-behaviors/). It allows one step further to better organize a project.


### Recursive functions

A function can call itself! In the events of a function, you can use the same action/condition/expression as in the rest of the game. This is called a "recursive" function.

!!! warning

    Be very careful when writing a recursive function. If you don't add conditions, the function could call itself infinitely, blocking your game.

You can [use the actions in "Functions" category to return expression/condition values](/gdevelop5/events/functions/return).

### Sharing functions

Functions can be shared across projects (like actions/conditions that are built in GDevelop). The simplest way to do it is just to copy/paste them. But if you've created a useful set of functions, you may consider [sharing them with the community](/gdevelop5/extensions/share-extension).

!!! tip

    See [an example of replacing external events by a function](/gdevelop5/events/functions/replace-external-events), which is reusable and shareable. You can also **[automatically extract events to a function](/gdevelop5/events/functions/extract-events)**.


## References of parameters

Parameters in function can be various:

| Type                          | Data type    | Description                                               | Scope |
|-------------------------------|--------------|-----------------------------------------------------------|-------|
| [Objects](/gdevelop5/objects) | Objects list | A list of objects                                         | Condition, action |
| [Behavior](/gdevelop5/behaviors) | Behavior  | The behavior from an object                               | Condition, action |
| Expression                    | Number       | Integer or float                                          | Condition, action, expression |
| String                        | Text         | Just a text                                               | Condition, action, expression |
| String from a list of options | Text         | A list of multiple text                                   | Condition, action, expression |
| Keyboard Key                  | Text         | Let extension users choose a key from a list              | Condition, action, expression |
| Mouse button                  | Text         | A list of buttons                                         | Condition, action, expression |
| Color                         | Text         | The color in RGB. Format: `"255;255;255"`                 | Condition, action, expression |
| Layer                         | Text         | The name of a layer                                       | Condition, action, expression |
| Scene name                    | Text         | The name of a scene                                       | Condition, action, expression |
| Yes or No                     | Boolean      | A boolean value                                           | Condition, action |
| True or False                 | Boolean      | A boolean value                                           | Condition, action |
| [Object point](/gdevelop5/objects/sprite/edit-points) | Text         | The name of an point from an object | Condition, action, expression |
| [Object animation](/gdevelop5/objects/sprite/#adding-an-animation) | Text         | The name of an animation from an object | Condition, action, expression |
| [Identifier](/gdevelop5/events/functions#identifier-parameter) | Text         | Allow the auto-complete to suggest previously used values | Condition, action, expression |
| Scene variable              | Scene variable | The value from a scene variable          | Condition, action, expression |
| Created objects             | Objects list | A list of objects just created             | Condition, action |
| Image resource              | Text | The name of the image resource                     | The value of the parameter can only be read from a JavaScript code event. ([Read how](/gdevelop5/events/functions#resource-parameter)) |
| Audio resource              | Text | The name of the audio resource                     | The value of the parameter can only be read from a JavaScript code event. ([Read how](/gdevelop5/events/functions#resource-parameter)) |
| JSON resource               | Text | The name of the JSON resource                      | The value of the parameter can only be read from a JavaScript code event. ([Read how](/gdevelop5/events/functions#resource-parameter)) |
| Font resource               | Text | The name of the Font resource                      | The value of the parameter can only be read from a JavaScript code event. ([Read how](/gdevelop5/events/functions#resource-parameter)) |
| Bitmap font resource        | Text | The name of the Bitmap font resource               | The value of the parameter can only be read from a JavaScript code event. ([Read how](/gdevelop5/events/functions#resource-parameter)) |



### Identifier parameter

This parameter enables auto-completion for previously entered values from other events with the same identifier name and scope.

#### Scopes

- **Object** - To suggest previously used values on the same object.
- **Scene** - To suggest previously used values from the scene events.

#### Identifier name

Every parameter with the same identifier name share their values for the autocompletion.

### Resource parameter

These parameters can be, an image, an audio file, a JSON, a font, and a bitmap font. This parameter will return the name of the resource visible in the resource tab.
The returned value will be only available by getting the value in a JavaScript code events with [this method](/gdevelop5/events/js-code/#use-javascript-to-get-the-value-of-a-parameter-of-a-function).
