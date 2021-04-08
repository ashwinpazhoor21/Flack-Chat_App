# Project 2: Flack 
### Web Programming with Python and JavaScript

## Demonstration Video 

Link: https://youtu.be/RQL9zjZp6SU



## Flack, a Chat-App

This is a simple Flask web application where users can enter a name and create Chatrooms called Channels or go into one of the existing ones (if at least one already exists).

You can type and send messages into a channel that only exist within that channel and other users can read and respond to them.


**Application.py**

After a Flask instance is created and a few session parameters configured, a SocketIO instance is created too. That makes the normal app.run() for socketio.run(app) at the bottom of the file appropriate to modify.

Its first view is *index*. There are a few 'try's in the event that the user closes the tab and enters the app again. The application can then remember the name and also remember the last channel in which the user was.


*name* Takes note of the 'username' selected in the first input and remember in the session the name.


*lastChannel* Is responsible for recalling the last Channel the user has used and returns nothing.


*channel* Used to create new channels and then store the above-declared global variable 'channels.' All channels are instances of a custom class I created in a separate file called *channels.py* so that this class can store a channel name and a dict list where each dict matches a message and contains the message itself, the sender name, the channel name (this is redundant) and the time it was sent.

*delete* Is for the deletion of messages only. The user selects the one she or he needs to delete and just with a nice gif, that's gone. (personal touch)

The last two views are relative to sockets. The first is to take care of new messages, store them in their correspondent channel, then send them back to the showing chatroom. It also stamps the time before appending it to the Channel for that message. 

The second view of socketio is then used when the user is changing the channel. All messages that are available that belong to that channel are collected and sent. 

**Static**

This is where three images are stored. Also the custom CSS stylesheet *styles.css* and *formName.js* that is used to handle the case when the first time the user arrives on the webapp, they give their name.

**Templates**

At last, there are only two files in *templates*. *Layout.html* is used to build a base template (just for good habit because there is only one more template in this app and it's not very helpful). There you can find all the 'rel' for stylessheets, the jquery code, the socketio and the navbar as well. 

There are many lines in the index that are not only in HTML but also in JavaScript. There are severals types, one for adding the username, another for creating a new channel and the third for typing and sending messages.

Channel room is a div, there is another div within this div that includes an unordered list of 'id' *chatMessages*. Any new messages are appended here. We find the two big scripts with comments at the end of the file that help us understand how the channel name is provided and how messages are sent and received.



**Personal Touch**

In this project my personal touch was to introduce the right to delete your own messages. Upon hovering with the cursor, an X appears above the post, and the post disappears with a css animation. The message will be deleted from the database.
