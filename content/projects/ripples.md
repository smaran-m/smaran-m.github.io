---
title: "Ripples"
date: 2024-09-19T16:31:19-04:00
keywords: [ascii, image-manipulation, python3, python, pillow, PIL]
draft: false
tags: [graphics]
---
[![banner](/images/ripples.jpg)](https://github.com/smaran-m/ascii-ripples/)

# Ripples

## Live Demo

Check out [sammi.sh](http://sammi.sh). This also functions as my creative project website, and will be updated occasionally.

## Motivations

I'm still obsessed with ASCII art and textmode, but recently I've been wanting to learn a bit more about procedural content. I've been looking into simple procedural animations with inverse kinematics for an independent game project, and thought I'd showcase some of that over on my creative project website.

There's an animation where ripples spread across the screen, and a fish made of ASCII characters. The fish has two modes. It can either follow your cursor (with a red `◓` character showing the cursor's position and creating ripples) or move towards random points on the grid, toggling between modes when you click. I wrote prototypes in python, then converted it to JavaScript to make it accessible online and for better performance.

## Notes
The canvas is split into a grid, with each cell displaying an ASCII character. This setup ensures everything lines up neatly. Clicking generates ripples that radiate outwards. I calculate the wave amplitudes at each grid point using cosine functions, then map those values to different ASCII characters to create the visual effect. The fish is composed of multiple spheres that follow each other with a fixed distance, calculated independent of mouse movement (this would result in the segments detaching when the mouse moves quickly). The sizes of the segments increase to a midpoint and then decrease to make it a bit more fish-like, rather than a snake.

## Future
- Showing off my links on the website (like a school of fish swimming around them)
- Mobile optimizations (touch controls, scaling limits)
- More complex animations (like a school of fish with flocking behavior)
- Ascii shader with 3d model rendering for catching fish, this is a separate project I'm working on

## Acknowledgements
[A simple procedural animation technique](https://www.youtube.com/watch?v=qlfh_rv6khY)
[RippleEffectFragmentShader](https://www.shadertoy.com/view/ldBXDD)