---
layout: post
title:      "Scope in JavaScript(JS)"
date:       2020-08-06 20:12:31 -0400
permalink:  scope_in_javascript_js
---


What is scope? According to Merriam-Webster, scope is space or opportunity for unhampered motion, activity, or thought. Merriam-Webster also defines it as the extent of treatment, activity, or influence. Scope in computer science terms is defined as the region of a computer program where the binding is valid: where the name can be used to refer to the entity. According MDN (javascript documentation) - “scope is the current context of execution. The context in which values and expressions are 'visible' or can be referenced.”

There are three levels of scope in JavaScript (JS).

**1. Global Scope** <br>
**2. Function Scope** <br>
**3. Block Scope**

Let's take a look at each of these scopes in this read.

**Global scope** is the outer most scope in JS. Any variable defined outside of `{}`'s (not in a function) lives in global scope. Variables defined in global scope are "visible" anywhere in the application file. For example:
```
let pizzaDough = 'brooklyn style'

// pizzaDough lives in global scope (notice it is defined outside of any function). You can ignore the rest of this code for now.

function orderPizza() {
  const sauce = 'marinara'

  function pizzaToppings() {
    const cheese = 'mozzarella'
   
    return pizzaDough + ' with ' + sauce + ' and ' + cheese + ' please!'
    
  }

  const wholePizza = pizzaToppings();

  return wholePizza;
}

orderPizza();
```

Both **function scope** and **block scope** are considered to be local scopes. Variables defined in a local scope are 'visible', and therefore executable, only in a specific part of your code. Let’s first look at an example of **function scope:**
```
let pizzaDough = 'brooklyn style'

// sauce is NOT visible here (sauce's outer context). Remember, this is global scope.

function orderPizza() {
  const sauce = 'marinara'

  // sauce is defined and visible in the function orderPizza. The variable sauce is not visible in it's outer context.

  function pizzaToppings() {
    const cheese = 'mozzarella'


   
    return pizzaDough + ' with ' + sauce + ' and ' + cheese + ' please!'
    
  }

  const wholePizza = pizzaToppings();

  return wholePizza;
}

orderPizza();
```

Before we look at an example of **block scope**, I would first like to breifly discuss the scope chain in JS. 
When resolving variables, inner functions first look at their own scope. If the variable is not assigned locally (inside the aforementioned inner function's scope), then JS will look at the outer context of said function for the variable's value. Earlier we saw that vairiables defined in **global scope** are "visible" anywhere in the application file. It is beacuase of the scope chain that this is true! A final note on the scope chain: scope chaining is unidirectional. This means that JS will chain in only one direction; from inner most context(**function scope** in the example below) to outer most context(always**global scope**).

In the code below, we can see an example of this in action. Go ahead and try running this code yourself! You should see the following output:
```
let pizzaDough = 'brooklyn style'

function orderPizza() {
  const sauce = 'marinara'

  function pizzaToppings() {
    const cheese = 'mozzarella'

    return pizzaDough + ' with ' + sauce + ' and ' + cheese + ' please!'
    
  }

  const wholePizza = pizzaToppings();

  return wholePizza;
}

orderPizza();

// => 'brooklyn style with marinara and mozzarella please!'
```

In the above code, the function `pizzaToppings` first looks inside its own scope for the values to the variables: `pizzaDough` `sauce` and `cheese`. It sees that `cheese` is assigned a value of "mozzarella" but it cannot see the assigned values for the other two variables, yet. JS then checks `pizzaToppings`'s outer context (this is `orderPizza` in this case) and sees the value for `sauce`. Finally, JS continues up the scope chain to find the assigned value for `pizzaDough`. Check out the picture below for a visual representation of what we just discussed.

![](https://i.imgur.com/CGnMgx7m.png)

Lastly, **block scope** is the area within conditional statements and interations. For example, if statements and for loops. It's worth noting that scope chaining applies to the block scope too and in the same manner we've seen above.  

Pretty neat huh!? Now, hopefully you understand a bit more about scope and scope chain in JS.


