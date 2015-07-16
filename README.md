An HTML5 game engine developed from scratch.

![rapid-engine](http://i.imgur.com/KoVKzJv.gif)

The engine is divided into modules:

**ai.js** - provides artificial intelligence functions that can be applied to any game entity. The goal is to offer a flexible AI system and designer similar to Skyrim and/or Final Fantasy XII gambits.

**camera.js** - provides camera support. The goal is to offer intuitive scrolling and locking options as discussed in [Scroll Back: The Theory and Practice of Cameras in Side-Scrollers](https://docs.google.com/document/d/1iNSQIyNpVGHeak6isbP6AHdHD50gs8MNXF1GCf08efg/pub?embedded=true) by Itay Keren.

**editor.js** - provides live editing of the game during run-time and includes visual debugging tools. The goal is to offer non-technical users and non-programmers a way to build games from start to finish.

**engine.js** - provides the game loop and render pipeline for 2d graphics. The engine "pushes the game forward in time or state". Automatically handles text, sprites with frame-based animations, and composite sprites. Supports tile maps and image-based levels. Includes an entity component system as discussed in {Introduction to Component Based Architecture in Games](http://www.raywenderlich.com/24878/introduction-to-component-based-architecture-in-games) by Ray Wenderlich.

**input.js** - provides keyboard and mouse input. Input events can be attached to any game entity e.g. entity.on("click", function() { //do something }). The goal is to offer more types of input devices such as gamepads, touchscreens, touchscreen remoting, Wiimote, voice/gesture commands, etc.

**physics.js** - provides the physics pipeline for object movement and collision detection. Runs in real-time, or at a fixed timestep independent of the rendering. For example, set the timestep to 100ms and the physics will update only 10 times per second. The timestep can be changed during run-time, which is great for testing/debugging. Currently provides grid-based space partitioning for broad-phase collision detection. Collision events can be attached to any game entity e.g. entity.on("collision", function() { //do something }). Entities can be told to ignore others. The goal is to support very fast moving objects, multiple collisions and conservation of momentum.

**sound.js** - provides sound effects and music, with overlapped sounds. The goal is to offer distance-based volume and other features typical to 2d games.

**toolkit.js** - provides startup/shutdown methods and handles the loading of other modules and game assets. It incorporates a custom, high performance asynchronous module loading pattern (somewhat like RequireJS without the ceremony).

**ui.js** - provides UI components for the game, such as dialog boxes and form-based controls.
