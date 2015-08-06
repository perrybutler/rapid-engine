Don't really have a permanent name for this thing yet. It's an HTML5 game engine developed from scratch.

![editor](https://dl.dropboxusercontent.com/u/541743/rapid/captures/editor.gif)

*The current version has been tested to work with Google Chrome 43, FireFox 31, Internet Explorer 11 and iPhone 4/5 (w/ latest iOS). Not yet tested with any console or portable gaming system.*

Unminified/uncompressed sizes:

* Without editor: **90 KB**
* With editor (jQuery + Font Awesome): **1.04 MB**
* Breakout game (with editor): **1.14 MB**

##Core Architecture##

The engine is divided into modules:

**ai.js** - provides artificial intelligence functions that can be applied to any game entity. The goal is to offer a flexible AI system and designer similar to Skyrim and/or Final Fantasy XII gambits. Design AI "packages" containing unique behaviors that can be hot-swapped at runtime.

**camera.js** - provides camera support. The goal is to offer intuitive scrolling and locking options as discussed in [Scroll Back: The Theory and Practice of Cameras in Side-Scrollers](https://docs.google.com/document/d/1iNSQIyNpVGHeak6isbP6AHdHD50gs8MNXF1GCf08efg/pub?embedded=true) by Itay Keren.

**editor.js** - provides live editing of the game during run-time and includes visual debugging tools. The goal is to offer non-technical users and non-programmers a way to build games from start to finish.

**engine.js** - provides the game loop and render pipeline for 2d graphics. The engine *pushes the game forward in time or state*. Automatically handles text, sprites with frame-based animations, and composite sprites. Supports Google web fonts, tile maps and image-based levels. Handles display size, resolution and screen scaling. Includes an entity component system as discussed in [Introduction to Component Based Architecture in Games](http://www.raywenderlich.com/24878/introduction-to-component-based-architecture-in-games) by Ray Wenderlich.

**input.js** - provides keyboard and mouse input. Input events can be attached to any game entity e.g. entity.on("click", function() { //do something }). The goal is to offer more types of input devices such as gamepads, touchscreens, touchscreen remoting, Wiimote, voice/gesture commands, etc.

**physics.js** - provides the physics pipeline for object movement and collision detection. Runs in real-time, or at a fixed timestep independent of the rendering. For example, set the timestep to 100ms and the physics will update only 10 times per second. The timestep can be changed during run-time, which is great for testing/debugging. Currently provides grid-based space partitioning for broad-phase collision detection. Collision events can be attached to any game entity e.g. entity.on("collision", function() { //do something }). Entities can be told to ignore others. The goal is to support very fast moving objects, multiple collisions and conservation of momentum.

**sound.js** - provides sound effects and music, with overlapped sounds. The goal is to offer distance-based volume and other features typical to 2d games.

**loader.js** - handles the loading of modules and game assets. Incorporates a custom, high performance asynchronous module loading pattern (somewhat like RequireJS/AMD without the ceremony). Supports loading scripts and other resources in parallel or in series on-demand, dynamically at run-time. Utilizes <script>, <style> and <link> tags when possible to allow cross-domain/CDN resource loading. Utilizes XMLHttpRequest for other types of resources. Never uses eval().

There is a separate loader for game assets that works similarly, but allows .json files to act like relational data (not unlike MongoDB) for designing re-usable game objects that incorporate any number of properties and data from other assets and components.

**ui.js** - provides re-usable UI components, such as dialog boxes and form-based controls. Development has not started on this module yet, but the goal is to migrate the UI components from the editor into this module so that they can be used not only by the editor but also for the in-game UI.

**network.js** - provides multiplayer capabilities through a local listen server or hosted internet server. Development has not started on this module yet, but the goal is to adapt the very high performance networking code from Rapid Server (a .NET project) into this module as native JavaScript. Considering socket.io/node.js as well.

##Cross Platform - Write Once, Run Anywhere##

The source code consists of standards-compliant HTML, CSS and JavaScript. This means Rapid Engine is write-once run anywhere and cross platform. It is designed to work on major mobile OS's (iOS, Android, Windows Phone), major desktop web browsers (Chrome, FireFox, IE, Opera, Vivaldi), and major gaming consoles (Playstation 4, Nintendo Wii U, X-Box One). There is no other language that comes close to JavaScript's cross-platform write-once run anywhere nature. Total cross platform capability is never guaranteed because each vendor may implement features at different times, but when possible the aim is to carefully make compromises that forgo vendor-specific features in favor of more standards-compliant methods.

All entities are created equal but may later specify new behaviors and capabilities via the entity component system, so the rendering and physics pipelines rely on *duck typing*, as clarified by John Peterson in the article [What is "duck typing"?](http://ericlippert.com/2014/01/02/what-is-duck-typing/) by Eric Lippert, to determine when and how an entity is handled at run-time. The goal is to let designers build unique game objects and collaborate on them without writing code.

Games can be developed and played offline/without a server/from the local file system (by opening the .html file in a web browser), but some features such as the visual editor and multiplayer networking will not work at all from the local file system, or may require some kind of utility/emulator. For a fully integrated experience, set up a local development web server and host the entire package rather than working straight from the file system. There are currently no databases to set up or manage, no proprietary languages or formats, and no compiling or build tools. This could change if larger projects demand it, but for now it's all HTML, CSS, JavaScript, JSON, image and sound files organized into various folders. The plain file structure makes team collaboration easy, and integration with various workflows (Git, Dropbox hosting) should be extremely simple.

##Is HTML5 Even Viable?##

The HTML5 landscape has been riddled with caveats since its inception. There are still issues - web audio is not fully supported by all web browsers, canvas rendering slows down for certain mobile devices, etc. Even so, HTML5 was completed less than a year ago, so there is a lot of work ahead for game developers to discover new patterns and optimizations, and for browser developers to optimize these new HTML5 features further. There are some inspiring hobby projects and a few AAA titles that prove HTML5 can be a viable platform moving forward.

There are other obstacles as well - if the game just runs in a web browser, that means anyone can simply visit your URL and play it, but how are you going to publish it to Apple's App Store so it can get exposure (ratings) and so users can find it easily from their iPhone? Luckily, there are things like CocoonJS that can wrap an entire HTML5 game into a native-like app.

The barriers continue to be eliminated, so now is a good time to discover what HTML5 game development is all about.

##Captures##

![push](https://dl.dropboxusercontent.com/u/541743/rapid/captures/push.gif)

![loader](https://dl.dropboxusercontent.com/u/541743/rapid/captures/loader.jpg)

![breakout-1](https://dl.dropboxusercontent.com/u/541743/rapid/captures/breakout-1.gif)

![editor-2](https://dl.dropboxusercontent.com/u/541743/rapid/captures/editor-2.gif)

##Roadmap##

* Wrap up alpha version and submit an entry for JSBreakouts.

##History##

##Disclaimer##

I do not own the graphics depicted in this article, nor do I have permission to use them in a commercial product. The graphics were found using Google Image search, and they are being used here solely for showcasing the engine’s capabilities and progress. The tree sprites are from Here Be Monsters, and the player/wolf sprites are from Ragnarok Online.
