---
title: "Twitter Mobile"
date: 2020-08-14
tags-mobile: [Android]
header:
  image: "../assets/images/twitter/twitter-header.png"
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

Being fully declarative, we are able to build the UI by calling as series of functions that tuyrn data into a UI hierarchy, compared to methods of the past in which we needed separte view files described in `.xml` which we then referenced in our logic.


# Jetpack Compose Theming

Compose makes it easy to have consistent look and feels to your app by applying themes.
Material Theme is comprised of 3 attributes

1. Color
2. Typography
3. Shape

By customizing these attributes, changes are automatically reflected in the composable components.
Starting with a `themes package`, we can create classes to create and store these attributes.

![](assets/images/twitter_mobile/theme_package.png)




# Storing results with Jetpack DataStore


# Using Tensorflow Lite pre-trained model
