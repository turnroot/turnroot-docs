# Turnroot Editor Architecture Design and Structure
This document outlines the architecture design and structure of the Turnroot Editor, as well as some of the design decisions that have been made along the way. It is intended to be a high-level overview of the system, and is not intended to be a comprehensive guide to the codebase.

The Turnroot Editor is, at a high-level, two Node.js applications that communicate with each other. The first application is the Editor itself, which is a web-based application that allows users to create and edit games. The second application is the Schema Server, which is a RESTful API that handles the storage and retrieval of game data. 

## Turnroot Editor
The Editor runs on Node.js, using ExpressJS as the server engine, and a heavily customized version of [w2ui](http://w2ui.com/) for the GUI. Initial versions of Turnroot (long, long, ago) were written in Python and used PyQT. Slightly later, I attempted to use DearPyGui instead, but I ultimately decided to switch away from Python to JavaScript. JavaScript is faster, simpler, and it's much easier to write GUI applications in JavaScript than in Python. It also makes the Editor far more accessible to a wider audience.

### My w2ui
w2ui, out of the box, is a very nice library that makes building visual components quick. However, it's a complete disaster under the hood. It's not at all customizable, and the CSS is- to put it nicely- abominable. If you don't like the default look of w2ui, you have no way to change it, and the CSS is convoluted and verbose to a level I genuinely didn't think was possible.

After struggling briefly to do _anything_ with the CSS, I decided to save myself a headache and throw away all the non-essential CSS. I then wrote my own CSS using proper techniques such as variables, combined properties, and so forth. My w2ui is about 1/5 the size of the original, and it can be themed or customized in any way you like. 

You're welcome and encouraged to use my w2ui CSS instead of the default (keep the JS, that works pretty well). 

You can find my cleaned-up, essentials-only version of the w2ui CSS here: [GitHub - w2ui3.css](https://github.com/turnroot/turnroot-editor-server/blob/main/server/view/style/w2ui3.css)

This is essentially unstyled- it's just positioning stuff. If you like the style of the Turnroot Editor, you'll also want to use my additional CSS, which you can find here: [GitHub - w2theming.css](https://github.com/turnroot/turnroot-editor-server/blob/main/server/view/style/w2theming.css) You'll also need some variables; you can set those up yourself, use my themes file as reference: [GitHub - themes.css](https://github.com/turnroot/turnroot-editor-server/blob/main/server/view/style/themes.css)

## Schema Server
The Schema Server is a RESTful API that handles the storage and retrieval of game data. It is written in Node.js, using ExpressJS as the server engine, and MongoDB as the database. 

## Why two applications?
I thought long and hard before writing any code about whether I should make a monolithic application or break it up. I realized it would be best to break it up for the following reasons:
- **Scalability**: If the Editor and the Schema Server are separate, I can scale them independently. This also makes it simpler to move one application to a different server if the traffic should ever reach that level. 
- **Weekly Builds**: The Editor is updated weekly, it's pretty much always a WIP and probably always will be. The Schema Server is updated as needed. There's no need to have weekly builds for the Schema Server.
- **Security**: By keeping the Schema Server isolated, I can lock it down very tightly while keeping the Editor more accessible. 
- **Ease of Development**: It's easier to work on two smaller applications than one large one. And it's much easier to find files this way.
- **Parallel Processing**: By running the two applications separately, I can take advantage of multi-core CPUs. 

## Databases
There are two databases used by the Turnroot Editor: MariaDB and MongoDB. MariaDB is used for user data, and MongoDB is used for game data.

### Why?
SQL is much better for rapid-fire, small queries, and MongoDB is much better for large, complex queries. The game data very much needs a NoSQL structure- it's a complex, nested, and frequently-changing data structure, and MongoDB just _works_ for that in a way that SQL couldn't. On the flip side, MongoDB is slow and overly powerful for user data, which is why MariaDB is used for that.

Essentially, MongoDB is a semi-truck moving huge amounts of cargo (data) slowly, and MariaDB is a Lamborghini moving small amounts of cargo (data) quickly. 

## The downside- local install is a pain
This architecture design is perfectly optimized so the Editor can be as fast, performant, and stable as possible. I'm a huge fan of compartmentalization, and having each part do exactly one thing well. That's what I've set up here- two apps, two databases, each working in their own sphere. It's beautiful -joyful even- to use, to work on, and to see.

It is, however, _not_ joyful to setup locally. Sorry about that. You're always welcome to use the cloud version at [editor.turnroot.com](https://editor.turnroot.com) if you don't want to deal with the hassle. And hey, on the bright side, the enterprise software I work on daily has six databases and dozens of applications, so it could be a lot worse! ;) 


