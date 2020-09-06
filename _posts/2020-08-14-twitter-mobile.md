---
title: "Twitter Mobile"
date: 2020-08-14
tags-mobile: [Android]
header:
  image: "../assets/images/twitter_mobile/twitter-compose-header.png"
excerpt: "Data Science"
classes: wide
---
# Introduction

Mobile reproduction of the `Twitter Sentiment Analysis` project.
Core idea is the same but I wanted a way to make more widely available as opening up a jupyter notebook to run a python script which takes a single input keyword is a lot of work for not a lot of return.



# App Architecture


# Jetpack Compose

I decided to build this app using Android's new Jetpack Compose Library(Still in Alpha).
Compose is the modern toolkit for building native UI. Google describes it's advantages in these 4 points

* Less Code
* Intuituve
* Accelerated Development
* Powerful

Being fully declarative, we are able to build the UI by calling as series of functions that turn data into a UI hierarchy, compared to methods of the past in which we needed separte view files described in `.xml` which we then referenced in our logic.


# Jetpack Compose Theming

Compose makes it easy to have consistent look and feels to your app by applying themes.
Material Theme is comprised of 3 attributes

1. Color
2. Typography
3. Shape

By customizing these attributes, changes are automatically reflected in the composable components.
Starting with a `themes package`, we can create classes to create and store these attributes.

![](/assets/images/twitter_mobile/theme_package.png)


### Color

Starting by defining the colors that will best represent the product.

Creating a Color Palette and utilizing `Material.Colors.darkColors()` and `Material.Colors.lightColors()`, we can create a complete color sets for the color specification.

Keep in mind this is all specified in our `Theme` class, making support for dark theme easier as seen in our Theme composable.

![](/assets/images/twitter_mobile/color_palette.png)


### Shape

Shapes are pretty simple with Jetpack Compose, they are catagorized into 3 categories.
* Small components
* Medium components
* Large components

Each category allows for specifying a `CornerBasedShape`, which takes a parameter for sizing corners.

![](/assets/images/twitter_mobile/shapes.png)


### Typography

By defining a custom type system, you can continue to create a feel and look that best represents your product. Starting with defining a `fontFamily` containing a list of custom font files(.ttf), which are store in your `res/font` directory; you can take control of `regular/bold/semi-bold/etc..` fonts giving you complete control.

Creating a Typography class, you can set defaults for each style...

![](/assets/images/twitter_mobile/typography1.png)


### Theme

This is all wrapped up into our Theme. Defined at the highest level of our UI hierarchy.

![](/assets/images/twitter_mobile/theme.png)








# Storing results with Jetpack DataStore


# Using Tensorflow Lite pre-trained model
