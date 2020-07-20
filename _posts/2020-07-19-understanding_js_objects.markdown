---
layout: post
title:      "Understanding JS Objects"
date:       2020-07-20 01:18:55 +0000
permalink:  understanding_js_objects
---

JavaScript has objects. In this blog I would like to share what I have learned about how to modify properties that belong to them. In JS we can access properties that belong to objects by treating the object like a hash. Here is my basic object:
```
let restaurant = {cuisine: 'Italian', address: '123 Ave Way'}
```
If you have experience with Ruby and perhaps some other object oriented programming languages, you should notice how object values in JS look very similar to key value pairs. In JS, objects can be variables and even functions. In this blog I will simply look at how we can access and set the properties that belong to an object. The varaible object above is `restaurant` and it has two properties; `cuisine` and `address`.

To access the properties of the `restaurant` object we can use dot notation:
```
restaurant.address //=> 123 'Ave Way'; restaurant.cuisine //=> 'Italian'
```

We can also set new properties for the object:
```
restaurant.name = "Stan's Pasta Palace"
```
Notice that the value for the propety in this case is a string. Now:
```
restaurant.name //=> "Stan's Pasta Palace"
```


