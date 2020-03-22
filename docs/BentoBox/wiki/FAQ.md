# FAQ

## How do I install BentoBox, BSkyBlock and all those other addon things?
[Click here!](/BentoBox/wiki/Install-Bentobox)

## How do I make my own custom island?
Have a look at this video here: https://youtu.be/4gvaG89uxAs

## My server lags when a new island is created!
The paste speed may be too much for your machine. Try lowering it. Look in the BentoBox config.yml for this setting:
```
# Number of blocks to paste per tick when pasting blueprints.
  # Smaller values will help reduce noticeable lag but will make pasting take slightly longer.
  # On the contrary, greater values will make pasting take less time, but this benefit is quickly severely impacted by the
  # resulting amount of chunks that must be loaded to fulfill the process, which often causes the server to hang out.
  paste-speed: 64
```
And change it to 8 or something.

## What version of MySQL is required? Or any database?

Minimum required versions:
* MySQL versions 5.7 or later
* MariaDB versions 10.2.3 or later
* MongoDB versions 3.6 or later
* SQLite versions 3.28 or later

## How do I start writing addons for BentoBox? Is there an API?

Yes, there is definitely an API! Writing addons is very similar to writing plugins except there is a lot more API available for things like teams, protections, commands, panels and pasting.

Look at the [Getting started with addons](/BentoBox/wiki/Getting-started-with-Addons) page.

## I am getting super flat after a while, help!

If you see super flat then it is because the world generator is not working for the world anymore. There are a few reasons why this may be the case:

1. BentoBox is not actually running, or the addon is not running but you managed to get into the world. This usually doesn't happen because if the world generating addon or BentoBox is not running the server will usually dump you into the main world. If this happens, the obvious fix is to run the addon and BentoBox again and use the fix-superflat setting in admin settings to regenerate the chunks.
2. You set the default world to be the addon world but you didn't list the generator in Bukkit.yml. This is often the situation. Check out [this page](/BentoBox/wiki/Set-a-BentoBox-world-as-the-server-default-world) for how to set up your server with a default world. Again, you may need to run the super flat fixer in settings to regenerate chunks.
3. You have another plugin that is trying to control the generator for this world. This is very rare.
4. There's a bug in the addon or BentoBox. This is extremely rare (haha) - actually, nowadays it is, but it might happen for some reason, but check #1 and #2 first before filing a bug report. 