---
title: "Twitter Mobile"
date: 2020-08-14
tags-mobile: [Android]
header:
  image: "../assets/images/twitter_mobile/twitter-compose-header.jpg"
excerpt: "Data Science"
classes: wide
---
# Introduction

Mobile reproduction of the `Twitter Sentiment Analysis` project.
Core idea is the same but I wanted a way to make more widely available as opening up a jupyter notebook to run a python script which takes a single input keyword is a lot of work for not a lot of return.



# App Architecture

There are multiple design paradigm's typically employed in an Android application. Model-View-ViewModel is a very popular one. The 3 main players here are obvious but let's talk a little about their interactions with one another. MVVM does a great job, in my opinion, of abstracting the <em>View's</em> behavior.


MVVM
![](/assets/images/twitter_mobile/mvvm.png)


 The <em>ViewModel</em> may provide a stream of events to which the <em>View</em> may subscribe to and take some action. It retrieves data from the <em>Model</em> layer, applies logic and exposes what it needs for the View. These exposures are happening via `Channels`, essentially `Observables` for Kotlin Corroutines.



The <em>Model</em> is there to easily expose consumable data, either retrieved from some local data source(Room DB, Jetpack DataStore, Shared Preferences, etc..) or from a remote web service.


 The <em>View</em> may notify the viewmodel of some actions the user takes, this is 2 way data binding between view and viewmodel and results in the view keeping a reference to the viewmodel but the viewmodel having no information of the view. The viewmodel is the producer of data here and the view the consumer, consumer needs to know where the data is coming from but the producer does not care about who consumes the data down the line. \n

 This is the actual interface of the app. Typically, A Fragment, Activity, or any other custom android `View`. Normally we have to take care to bind/unbind from the event streams in the appropriate lifecycle events, but as you'll see later on. Kotlin Corroutines and Lifecycle aware components will take care of that for us.




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





# Building Views








# Fetching Tweets

The main Twitter API method used in this app is `/search`. For now, all we are interested in is searching a keyword and receiving a certain number of tweets that have been designated to have our search term as the core topic.
 [Standard Search API](https://developer.twitter.com/en/docs/twitter-api/v1/tweets/search/api-reference/get-search-tweets)

 The challenge here was that before now, I have only used RxJava for my asynchronous streams. I decided to give Kotlin Corroutines a try. Since I'm already using `Android ViewModel`, an android Architecture component, which provides 1st class support for corroutines due to the built in Coroutine scopes, I figured it shouldn't be too much work. The biggest hurdle was just understanding the differences (conceptual and syntatic) between RxJava world and Corroutine world.

 Let's take for example Authentication.

![](/assets/images/twitter_mobile/getToken.png)

 All Coroutines are started from a `CoroutineScope`, which depend on our life-cycle aware component scope.`launch{}` is just an extension function of the `ViewModelScope` because it implements interface `CoroutineScope`. By default, we code inside the `launch{}` block is run off the main thread(Dispatchers.Main), this allows a simple, straight forward way to run non-blocking code.

 3 Dispatchers: Tells coroutine which type of threads to use for execution of corrotine block.

1.a
2.b
3.c


In our viewmodel's search function. We are preforming an asynchronous call to the network. These calls typically take less than a second but in the case of a slow network response, we are not blocking the UI, allowing the user to make any desired navigation.

![](/assets/images/twitter_mobile/search.png)




# Storing results with Jetpack DataStore


# Using Tensorflow Lite pre-trained model
