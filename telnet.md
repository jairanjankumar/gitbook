---
description: Playing chess using telnet
---

# Telnet

Playing chess using telnet

```
# I am running telnet on docker
$ docker run -it mikesplain/telnet freechess.org 5000


$ docker start -i 95e28cf7ddd4

             _       __     __                             __      
            | |     / /__  / /________  ____ ___  ___     / /_____ 
            | | /| / / _ \/ / ___/ __ \/ __ `__ \/ _ \   / __/ __ \
            | |/ |/ /  __/ / /__/ /_/ / / / / / /  __/  / /_/ /_/ /
            |__/|__/\___/_/\___/\____/_/ /_/ /_/\___/   \__/\____/ 
       ^^__                  _____________________                 _  _  _ 
      /  - \_               / ____/  _/ ____/ ___/   _            | || || |
    <|    __<              / /_   / // /    \__ \   (_)           |_______|
    <|    \               / __/ _/ // /___ ___/ /  _              \__ ___ /
    <|     \             /_/   /___/\____//____/  (_)              |___|_|
    <|______\                                                      |_|___|
     _|____|_        ======================================        |___|_|
    (________)         freechess.org  ----  167.114.65.195        (_______)
    /________\       ======================================       /_______\ 
                       (Login screen designed by Alefith)

   ****** Welcome to the Free Internet Chess Server at freechess.org ******

Webpage: http://www.freechess.org
Head admin : mattuc   Complaints to : complaints@freechess.org
Server location: freechess.org   Server version : 1.25.20

      If you are not a registered player, enter guest or a unique ID.
             (If your return key does not work, use cntrl-J)

login: g



fics% e
GuestLWZR (++++) seeking 3 0 unrated blitz ("play 76" to respond)
fics% 
Starting a game in examine (scratch) mode.




fics% bxf7

Game 145 (GuestFZSG vs. GuestFZSG)

       ---------------------------------
    8  | *R| *N| *B| *Q| *K| *B| *N| *R|     Move # : 4 (Black)
       |---+---+---+---+---+---+---+---|
    7  | *P| *P| *P| *P|   | B | *P|   |     White Moves : 'Bxf7+   (0:00)'
       |---+---+---+---+---+---+---+---|
    6  |   |   |   |   |   |   |   |   |
       |---+---+---+---+---+---+---+---|
    5  |   |   |   |   |   |   |   | *P|     Black Clock : 0:00
       |---+---+---+---+---+---+---+---|
    4  |   |   |   | *P| P |   |   |   |     White Clock : 0:00
       |---+---+---+---+---+---+---+---|
    3  |   |   |   |   |   |   |   |   |     Black Strength : 38
       |---+---+---+---+---+---+---+---|
    2  | P | P | P |   |   | P | P | P |     White Strength : 38
       |---+---+---+---+---+---+---+---|
    1  | R | N | B | Q | K |   | N | R |
       ---------------------------------
         a   b   c   d   e   f   g   h
         
```

Though telnet is outdated, Use ssh instead.

Telnet a terminal emulation program that is used to access remote servers. It's a simple, command line tool that runs on your computer and it will allow you to send commands remotely to a server.&#x20;
