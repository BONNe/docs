# Table of Contents

[TOC]

# Installation

## How do I install BentoBox, BSkyBlock and all those other addon things?

We have set up various ways to allow you to easily install BentoBox and its addons.
You can check out [this tutorial](BentoBox/Install-Bentobox.md) to learn about all of them.
**Welcome in our community!**

# Configuration

## How do I make my own custom islands?

You are referring to our **in-house schematic format** we call **_Blueprints_**.
The [Blueprints page](BentoBox/Blueprints.md) provides all the relevant information to get you started with the Blueprints, as well as a few hints and tricks you can use to further customize them.
You can also have a look at [this video](https://youtu.be/4gvaG89uxAs) which, although outdated, might help you create your first Blueprint within minutes.

## What version of any database is required?

Minimum required versions:

* **MySQL** 5.7 or later
* **MariaDB** 10.2.3 or later
* **MongoDB** 3.6 or later
* **SQLite** 3.28 or later

## How can I increase some players' island size?

There are two ways to grant players a greater island size: the permissions or the commands.
Both have pros and cons, and **should not be used concurrently**.

**Permissions**

Grant players the `[gamemode].island.range.<number>` permission.

* This will only work if the island owner has that permission
* The island owner will have to reconnect on the server in order to apply the changes

**Commands**

Use the `/[admin_command] range` commands.

# Issues

## Superflat chunks are generating in my worlds

*Relevant issues:*
[BentoBox#1212](https://github.com/BentoBoxWorld/BentoBox/issues/1232),
[BSkyBlock#247](https://github.com/BentoBoxWorld/BSkyBlock/issues/247).

![Superflat world](https://static.planetminecraft.com/files/resource_media/screenshot/1215/2012-04-15_205556_2000620.jpg)
*A superflat world. (Credit: [1213videogamer on PlanetMinecraft](https://www.planetminecraft.com/member/1213videogamer/)).*

If you start seeing superflat chunks being generated in your world, then it is because the world generator is not working for the world anymore.
There are a few reasons why this may be the case. They are ordered according to their likeliness.

**We strongly recommend you to revert to backups made prior to this situation**.
Although we are providing additional instructions to help recover from such an event in case you do not have backups available, we **do not guarantee their effectiveness**.
Moreover, these solutions are **designed to address the problem as much as possible, however, ignoring the impact on performance or player islands**.
Use them knowingly.

In any case, **stop your server immediately to prevent further damage from being done to your worlds**. 

### Causes

#### BentoBox or the Gamemode addon is no longer running

**Why?**

BentoBox or the Gamemode addon is not enabled on the server.
This can occur if you updated BentoBox or the Gamemode addon to a version which is not compatible with your server or which is incompatible with one of your plugins.

**Solutions**

Investigate as to why BentoBox or the Gamemode addon is no longer enabled.
Read the logs to find errors at startup.
Try booting your server up while adding a single plugin at a time to find out which plugin is causing the issue.

#### There is no generator set for this world in the `bukkit.yml` file

**Why?**

This is often the situation.
While setting the default world of your server to be the Gamemode addon's world, you forgot to specify the right generator for said world in the `bukkit.yml` file.

**Solutions**

Make sure you followed each step of [this tutorial](BentoBox/Set-a-BentoBox-world-as-the-server-default-world.md) thoroughly.

#### The `use-own-generator` option from the Gamemode's config is set to `true`

**Why?**

This is a common mistake.

Users tend to misunderstand this option as allowing them to activate a "magic" cobblestone generator (but [it's an addon](addons/MagicCobblestoneGenerator/index.md)!).
This is indeed not what this option is designed for, and this is clearly explained in the comments surrounding this option in the config file:

```yaml
# Use your own world generator for this world.
# In this case, the plugin will not generate anything.
# If used, you must specify the world name and generator in the bukkit.yml file.
# See https://bukkit.gamepedia.com/Bukkit.yml
use-own-generator: false
```

Ultimately, this can also happen if you forgot the specify the world name and generator in the `bukkit.yml` file.

**Solutions**

If you do not plan to use an external plugin to generate the world, then you should set this option back to `false`.

On the contrary, you should make sure you have specified the world name and the corresponding plugin name as its generator in the `bukkit.yml` file.

#### Another plugin is trying to control the generator of this world

**Why?**

Although very rare, this can still happen.

Some plugins, especially world management ones (e.g. Multiverse), tend to provide settings that could override the generator of our worlds.

**Solutions**

Review all of your plugins to find out which one is the most likely to cause the issue.
World management plugins or custom-coded ones that are interacting with worlds are to be investigated first.
Either report the issue to their developers or fix the configuration files that are involved.  

#### There is a bug in BentoBox or in the Gamemode addon

**Why?**

*Woopsie!*

Nowadays, this is extremely rare.
But it might still happen for some reasons.

**Solutions**

Make sure this is actually a BentoBox-related bug: remove all the plugins from your server one by one until only BentoBox is left.

If the issue is no longer occurring, this means another plugin is causing it.
In that case, please refer yourself to [this section](https://bentobox-world.readthedocs.io/en/latest/FAQ/#another-plugin-is-trying-to-control-the-generator-of-this-world).

If the issue still occurs, this means this is a BentoBox bug.
Please [report it on our bug tracker](https://github.com/BentoBoxWorld/BentoBox/issues).

### How to clean the superflat chunks afterwards?

If you have backups, use them to revert your server's worlds and BentoBox databases to their previous states.

If you do not have backups, log into your server and open the Admin Settings Panel using the `/[admin-command] settings` command.
Find the "*Clean Super Flat*" flag and toggle it on.
Depending on your settings, locales and on the BentoBox version you are running, the name, icon or description might be different.
But we are sure you will be able to find that flag by yourself nonetheless!

![image](https://user-images.githubusercontent.com/20014332/77770414-8256c380-7045-11ea-8ab6-8efe31d6fb87.png)
*The Clean Super Flat flag in BSkyBlock's Admin Settings Panel*.

This flag will **slowly regenerate any superflat chunk from your world over time**.
This happens when chunks are loaded, so you might want to either teleport to said chunks to force the regeneration, or you could leave the flag enabled for a few days.
**Do not forget to disable the flag at some point!**
It is quite resource-intensive...

## My server lags when a player creates their island!

Pasting the island or generating the chunks are the main causes of this issue.

Firstly, the paste speed may be too much for your server.
Try lowering it.
Look in the BentoBox `config.yml` for this setting:

```yaml
# Number of blocks to paste per tick when pasting blueprints.
# Smaller values will help reduce noticeable lag but will make pasting take slightly longer.
# On the contrary, greater values will make pasting take less time, but this benefit is quickly severely impacted by the
# resulting amount of chunks that must be loaded to fulfill the process, which often causes the server to hang out.
paste-speed: 64
```

If you are running timings, the `BlueprintPaster` task should ideally be taking a long time, yet take a low percentage of a tick time.

If the server still struggles when pasting islands, then that implies it struggles to generate the chunks.
That is something we have little control on as a plugin, but here are a few things you could do to mitigate this:

* Try reducing the "distance between islands" setting in the gamemode's config file. 
Lower values means fewer chunks to generate.
This will require you to entirely reset the worlds and databases.
* Use Paper as your server software.
Paper handles asynchronous chunk generation.
* Pre-generate the world.
Especially for gamemodes whose generators are resource-intensive, such as CaveBlock or SkyGrid.

# API

## How do I start writing addons for BentoBox? Is there an API?

Yes, there is definitely an API.
Writing addons is very similar to writing plugins except there is a lot more API available for things like teams, protections, commands, panels and pasting.

Follow [this tutorial](Tutorials/api/Create-an-addon.md) to create your first addon!