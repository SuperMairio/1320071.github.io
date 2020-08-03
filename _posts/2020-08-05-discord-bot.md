---
layout: post
title:  The Adventures of RockyBot (part two)
subtitle: The Return of the King
date:   2020-08-05 15:38:35 +0100
tags: [Coding, Python]
---

---

If you have read <a href="https://1320071.github.io/2020-07-14-twitter-bot/"> part one </a> of the Adventures of RockyBot then you will know that I prevously attempted to make this in Twitter. Not wanting to simply give up on providing the world with photos of my cat I decided to try and make the bot on Discord instead. (Spoiler alert: it went really well and im an amazing programmer)

## Set-up

Lucky for me Discord has a beautiful web client for creating bots and it was so easy to use.
To create RockyBot I first had to create an application, which was as easy as pressing 'New Application' and giving it a name. 
From here I gave the application a photo and a brief description.
<p align="center">
  <img src="DiscordDesc.png" alt="Screenshot of application details"/>
</p> 

To make the actual bot that I can invite to servers I went to the 'Bot' tab and pressed 'Add Bot'

<p align="center">
  <img src="CreateBot.png" alt="Screenshot of option to add new bot"/>
</p> 

This gave me access to a bot token, required for doing anything with python, and allowed me to set the permissions required. I made sure to turn off 'PUBLIC BOT' so only I can add RockyBot to a server. I don't want him on too many servers incase there's a bug and I get 100 emails asking to fix it.


Once the inital bot set-up was complete I moved on to ensuring that all the python libraries I wanted to use were installed.
The libraries I used are; os, random, shutil and discord.


## Programming

After discovering that `from topsecretfile.py import *` does not work (Something I should have checked on my TwitterBot script...) I decided to use Linux enviromental variables instead. 
This allows me to not include sensitive information in Git commits but still access them in my Python script. 
To do this I ran the command `export VARNAME=CONTENTS` in my terminal, I discovered that using `os.environ` in Python only works for as long as the script is working but using the alternative persists for as long as the terminal itself does.
I then accessed the data using the os library.

<p align="center">
  <img src="EnvVars.png" alt="Screenshot of me using os.getenv"/>
</p> 

(When trying to get a channel ID make sure you have developer mode **on** first)

The functionality of this bot is slightly different to that of my original, Twitter, version.

I decided that instead of sending a photo of my cat every so many hours, people on the server could instead request one whenever they wanted.
How this works is the bot reads the messages on the channel and if a user sends one that contains a certain phrase such as "Im sad" or "I miss Rocky" the bot will then send a photo.
I also added some replies for the bot to send alongside the images to make it a little more wholesome.

<p align="center">
  <img src="onMessage.png" alt="Screenshot of my on_message function"/>
</p> 


As with my Twitter bot I am using the shutil library to then move the sent images into another folder, however I updated the method slightly by concatinating the file path to the file name.



## Docker
`sudo docker run -v $(pwd):/app/ -it --rm python:3.7 bash
pip freeze > requirements.txt`

-v = volume
mount current working directory (my pc) to app (inside container)  
-it = interactive + terminal
lets me interact with it because it knows im in a terminal
--rm = remove
when i close the container delete it else it will sit in my file system forever



## Final Thoughts
The <a href="https://discord.com/developers/applications"> Discord Developer Portal </a> is super straightforward to use and there are plenty of online resources available relating to it. 
So it was really fun to build RockyBot and honestly, I was just glad I didnt have to write an essay in order to get API Keys.

<p align="center">
  <img src="FriendshipMeme.png" alt="My friendship has ended with twython now discord.py is my best friend meme"/>
</p> 

In all seriousness I would love to complete my Twitter bot and have it working along side the Discord one. Even if I use it for another reason such as making a staggered queue system for my art so I dont just tweet five pieces in one day then nothing for a month.
If I ever do go back to it and am successful in obtaining API keys I will be sure to update my first blog post.

## References 
<details>
 <summary markdown="span"></summary>
Discord Developer Portal: <a href="https://discord.com/developers/applications">https://discord.com/developers/applications</a>
</br>
Docker Tutorial: <a href="https://www.docker.com/101-tutorial">https://www.docker.com/101-tutorial</a>
 </details>
