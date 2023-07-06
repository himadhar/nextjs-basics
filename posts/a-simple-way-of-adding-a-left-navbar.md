---
title: 'A Simple Way Of Adding A Left Navbar'
date: '2022-03-21'
---

# A Simple Way Of Adding A Left Navbar

## Introduction

![](/images/blogs/tulip.jpeg)

The left navbar is always a key starting point of any project. It gives a visual cue to the end-user to figure where the navigations for the app resides (heuristic / mental shortcut). Coming up with a lightweight solution for any problem is the best way to go about it.

And, here, I am trying to provide a simple approach to managing the navigation control/navbar to be easily available and animate smoothly without over-engineering it.

Many plugins, frameworks among others, are currently available to solve this area of concern. But, then you also have to proceed with the extra methods/hooks they provide along with the implementation. If the whole purpose is to achieve the left navbar and proceed with your other implementations, it’s probably better to go about it the simpler way. Below is one such implementation that is out-n-out CSS driven and zero JS to achieve it.

---

## Magic Ingredient
The key to achieve this is by using a checkbox and its state of being checked or not — to control whether you show your left tree or not. as illustrated below;

```
<div id="root">
  <input type="checkbox" id="masterToggler" />
  <i class="hamburger-icon"></i>
  <div class="left-navbar">
    ...
    ...
  </div>
  <div class="everything-else">
    ...
    ...
    ...
  </div>
</div>
```

You can sprinkle some animations once you are done implementing them. Since the structure is more or less decided here, let’s dive into implementation.

---

## Implementation

```
// SCSS variables
$dimension: 40px;
$leftNavWidth: 26vw;
$zeroD: 0;
$fullD: 100%;

#root {
  width: $fullD;
  height: $fullD;
}
.left-navbar {
  width: $leftNavWidth;
  height: $fullD;
  transition: width .5s;
}
.everything-else {
  width: calc(#{$fullD} - #{$leftNavWidth});
  height: $fullD;
  transition: width .5s;
}
#masterToggler {
  position: absolute;
  top: $zeroD;
  left: calc(#{$leftNavWidth} - #{$dimension});
  opacity: $zeroD;
  height: $dimension;
  width: $dimension;
  &:checked {
    left: $zeroD;
    ~ .hamburger-icon {
      left: $zeroD;
      }
    ~ .left-navbar {
      width: $zeroD;
    }
    ~ .everything-else {
      width: $fullD;
    }
  }
}
.hamburger-icon { /* same as checkbox or #masterToggler */
  position: absolute;
  top: 0;
  left: calc(#{$leftNavWidth} - #{$dimension});
  opacity: 0;
  height: $dimension;
  width: $dimension;
}
```
---
## Conclusion

As you can see, the checkbox state controls the position, width, visibility of the components residing as its sibling. A very straight forward way of achieving the left nav bar with zero Javascript!

Few additional things achievable this way are — when collapsed, the left tree can show just the icons instead of all the nav controls, active state of the currently navigated view can be better highlighted when collapsed and so on. You can also place the controls in the header, or the bottom of the navbar can even sit on the right side of the view and the CSS will still work since it’s “nearby” logic-driven — all of it driven by the state of the checkbox — selected or not.

I have created this project in Codepen for reference. Let’s connect if you want to discuss the idea behind it.

---

## Conclusion

![](/images/blogs/clock.jpeg)

Choosing the right IDE for web development is crucial for optimizing your workflow and efficiency. The IDEs listed above are among the best options available in 2021, offering a range of features, flexibility, and customization. Consider your specific needs and preferences when selecting an IDE for your web development projects.

---

<h6 style="text-align: right">
- Himadhar
</h6>