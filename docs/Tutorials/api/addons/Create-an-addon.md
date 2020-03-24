# Introduction

BentoBox relies on **_Addons_ to provide new features or new _Gamemodes_**.
This tutorial will guide you through the process of **creating your first addon**.

Creating an Addon is often easier and quicker than creating a plugin from scratch, because BentoBox provides [wrappers](https://en.wikipedia.org/wiki/Wrapper_function) and key API features.
Addons also have direct access to the other addons' API, unlike plugins, due to the [visibility principle of Java Classloaders](https://www.javatpoint.com/classloader-in-java).
Moreover, they have access to BentoBox's [Config API](../../../BentoBox/Config-API.md) and [Database API](../../../BentoBox/Database-API.md).

In order to comfortably follow this tutorial, you should have previous experience in plugin development.
The addon development process is indeed very similar to the latter, and we will consider throughout this tutorial that you understand the key Java concepts, for the sake of concision.

# Table of Contents

[TOC]

# Prepare the project

## Using the pre-made Addon template

## Manually creating the project

### Import BentoBox as a dependency

#### Maven

#### Gradle

### Setup the project architecture

# Create the main Addon class

The **main class of an Addon** works similarly as to one of a plugin.
It most notably handles the code that runs when the addon is loaded, enabled, reloaded or disabled.

The main class **extends `Addon`**. 

*Example:*
```java
import world.bentobox.bentobox.api.addons.Addon;

public class MyAddon extends Addon {

}
```

*Note:* When creating it, it is **good practice to name it the same as your addon**.

*Genuine examples*: [Greenhouses](https://github.com/BentoBoxWorld/Greenhouses/blob/develop/src/main/java/world/bentobox/greenhouses/Greenhouses.java),
[Chat](https://github.com/BentoBoxWorld/Chat/blob/develop/src/main/java/world/bentobox/chat/Chat.java),
[Biomes](https://github.com/BentoBoxWorld/Biomes/blob/develop/src/main/java/world/bentobox/biomes/BiomesAddon.java).

## Mandatory methods

### onEnable()

### onDisable()

## Optional methods

### onLoad()

### onReload()

# Create the addon.yml

