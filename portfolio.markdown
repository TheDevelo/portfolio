---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page
title: "Portfolio"
---
## Computer Graphics
# Vulkan Renderer
For the Realtime Rendering class at CMU, I wrote a full rendering engine completely from scratch using C++ and Vulkan.
The renderer loads a custom scene format similar to glTF and renders the scene in real time, either to screen or an image sequence for video.
The renderer currently supports features such as frustum culling, transformation-based animation, and environment maps.
[The source code can be found here](https://github.com/TheDevelo/vulkan-renderer).

# Spline Generator
As a part of my Counter Strike level design, I wanted to easily create 3D models of spline curves that weave through my levels.
To help create these models, I wrote a tool that lets me freehand these splines easily, and then export them into a format that I could use in Counter Strike.
The tool uses a custom engine, loading the Counter Strike map format to allow me to visualize how the splines look within the environment.
I can easily add new points to my spline, as well as adjust the position and rotation of existing control points, all within the tool.
The tool is written in Rust and uses WebGPU to render both on native and the web. [The source code can be found here](https://github.com/TheDevelo/botpath-generator/tree/rust).

![](/assets/spline1.png)

![](/assets/spline2.png)

## Game Development
# surf_polytron
As a part of the [KSF Winter 2021 Mapping Contest](https://www.youtube.com/watch?v=kLc7ZYVy6ro) for Counter Strike, I designed and created the level **surf_polytron** for the custom surf gamemode. Inspired by the game _Fez_, **surf_polytron** has you traverse through many varying environments.
![](/assets/poly1.png)

![](/assets/poly2.png)

![](/assets/poly3.png)

![](/assets/poly4.png)

![](/assets/poly5.png)

![](/assets/poly6.png)

![](/assets/poly7.png)

![](/assets/poly8.png)

![](/assets/poly9.png)

[A video showcase of the map can be found here](https://youtu.be/mPkLjx4JwGs).

# Painters for Hire
Painters for Hire is an web-based multiplayer drawing and party game designed for 3 to 10 players. In a round of Painters for Hire, one players is assigned as judge. The judge submits a text prompt, which the other players must then draw in a short timeframe. After all players submit their drawings or time expires, the judge then ranks their 3 favorite drawings, who then gain points. The judge then cycles to another player, and another round is played. After a set amount of rounds, the player with the most points is determined winner.
![](/assets/pfh1.png)

![](/assets/pfh2.png)

![](/assets/pfh4.png)

![](/assets/pfh3.png)

![](/assets/pfh5.png)

Painters for Hire is written in the Godot game engine, with all client code written in GDScript. Additionally, the game server that connects clients together is written in Rust. Painters for Hire utilizes the WebRTC protocol to create a seamless Peer-to-Peer connection between players, allowing the server to be as minimal as possible. [The source code for Painters for Hire can be found here](https://github.com/TheDevelo/painters-for-hire).
