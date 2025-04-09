---
title: "Making a Smash Clone"
date: 2025-04-08T15:53:03-04:00
slug: ""
description: "DUNJIN DEVLOG #1"
keywords: [gamedev, graphics, godot, indiegame]
draft: true
tags: [devlog]
math: false
toc: false
---
![banner](/images/dunjin1/dunjin.png)

# I have a lot of nostalgia
for games that I have never played. You know those fake games that they would put on in an episode of a 90s sitcom or something which had generic fantasy tropes, but nothing identifiable enough to get them sued? Or that episode where characters dress up to play D&D (which I found out way too late that no one does irl)? I miss those games. Or, maybe, the idea of those games.

There's this idea of "fantasy" which only exists in the collective consciousness - not particularly western, not particularly medieval, a distillation of tropes and aesthetics that eventually came to characterize JRPGs. There's traces of the lineage of Ultima, AD&D, Rogue, LotR, and hell, even Final Fantasy, but not committing to the specifics of any singular one of them. The floppy cone hat wizard, the fair skinned blonde elves, level 1 slimes. You can see this flavor of fantasy in the isekai genre, or modern MMOs, or in your average D&D5e game.

Unfortunately, for my twisted mind, these formats are much too slow. I dislike turn based games, and these games all feel way to restricted compared to what an ideal fight should look like - wizards bombarding fireballs from high above, knights parrying holy blades that make the ground reverberate with their force, that cool scene where you see someone power up for like a whole episode before blasting a hole in the moon. I want to do that. I want impact frames.

So what game would let me do something like that? Really, the only thing with that sort of real-time decision making and emphasis on movement is a fighting game, more particularly, Smash Bros. That's how we got here, to my medieval fighting game project.

# Dunjin
is a fighting game that plays into fantasy tropes, with a focus on gameplay. Honestly, all the stuff above was an overexaggeration. I just played D&D for the first time in a while and I was like "wow, combat suuuuucks". Then I watched a Smash Ultimate match and was like "dang there are so many swordies this suuuuucks. What if it was all swordies. Wait."

You get the rest. I was also unemployed after graduating so that might have played a part in it. Probably a big part, actually, but I digress. I've put in probably 3 months of work into this thing since, in between school and other work, but what is it actually about?

## Story
You have been thrown into an ancient megastructure, 'Dunjin', for crimes committed against the general public. It towers into the heavens, and digs deep into hell. The history of this structure has been lost to time, it is older than you, older than your people, older than recorded history. Some claim it once served as a stairway to the heavens; some claim it was the magnum opus of an architect who was then left inside to rot; some claim it was a gift from the gods for the suppression of evil. The words to describe its truth have not been spoken in millennia.

One thing is for sure: no one, and no thing, has ever left the Dunjin.

## Characters
Currently, the only character is the Knight, with a couple others in the works. They each represent a generic fantasy trope, and are modelled vaguely after the D&D class system. I actually feel like there's a benefit to genericism, as each character has an implied backstory afforded by the genericism, and the tropes can fill in the gaps. You imprint your own ideas on to the character, and it affords you opportunities to subvert or reinforce a given trope - the only truth of the character is in the story you tell, but you have some leeway regarding the blurry edges of that truth. That said, I think trope subversion is a little too heavily relied upon these days, and I prefer interrogations of the tropes themselves and their implications in real scenarios. Dungeon Meshi does this well.

I'm aiming for somewhere around 6 characters on release, since animating each character is quite a bit of work, but haven't decided on all 6. I might throw in some clones too, since those are easier to pump out with some of the tools I've made.

## Setting
Medieval fighting game has actually been done before, like in [Battle Fantasia](https://www.youtube.com/watch?v=hbXkcEZhflA). That's not the extent of my gimmick. My gimmick has far wider implications and is embedded in the very mechanics of the game. My gimmick is a feature.

I'm trying very hard to tie everything into the mechanics, while staying in line with the relevant tropes. More info on this in a future blog post, when I'm done with single player.

# Gameplay
This is a bulk of where my work went. I was able to get a lot of the core smash mechanics in place, with help from the [Apano platform fighter tutorial series](https://www.youtube.com/watch?v=FKMBkZsPCCA&list=PLeJDGeZe3by2tQIJmCZfaSRl95cot070t), and made a lot of changes for my own purposes, like to movement and shields. At the moment, there's just 1 character (Knight), and I modelled him somewhat after Fox/Marth, but I have others in the works. I've actually already gotten a prototype playtested, and I think people had enough fun with it for me to feel comfortable posting this devlog and continuing with the project.

## Systems
### Offensive options
The Knight has a set of 3 types of attacks, normals, specials, aerials - which are all directional. Normals are just tilts and smashes, if you're familiar with the Smash Bros system. The main motivation behind not having separate smashes is that I didn't want to do more animations for unique smash attacks - instead just making them tilts with more damage, endlag, startup. This system isn't in the game yet since it depends on me reworking the input system, which I'll get into later.

Specials are a little more interesting, but still ultimately basic. They're similar ot normal attacks, but they either have more knockback, or add momentum to the player for traversal. I haven't done any more interesting specials yet, but they'll come with other characters. There's 1 protectile attack, the neutral special, which doesn't do any knockback, and acts more like a fox laser.

### Grabs/Throws
Grabs and throws are in, but pummels are not. I just didn't animate it, and dont think it's super readable at the sprite scale we're working with. That said, throws just work by putting out a small hitbox that does the relevant knockback as if it was a normal attack, and it scales a lot less with damage.

### Defensive options
The Knight has a shield, which is a little different from smash. It has a fixed size, does not drain on hit, and is not directional, but it does have a parry mechanic. There is a 4-frame window at the start of shield where you can parry an attack, putting the enemy in a 60 frame stun. Parrying also reflects projectiles, like powershielding. Which leads to fun games of dodgeball.

Shields automatically drop after 5 seconds, and you can roll out of shield, with a decent bit of endlag. The shield system as a whole is another major target for improvement, as I want to add shield health and shield breaks. I want there to be a risk/reward system for shielding, and maybe be able to balance it for individual characters - so less shield health for a weaker character or something similar. The details aren't ironed out yet, but I'm planning on taking more inspo from D&D, so something like Armor Classes, where you don't fully nullify attacks but just take a percentage of the original damage based on your AC.

Crouching is in, but it doesn't do anything yet. I want to add crouch cancelling, but I honestly don't know what it entails that well. I'm just going to mess with knockback values in the hitbox class and see what works.

### Hitboxes
Hitboxes are a massive area for improvement at the moment, as I currently only have 1 rectangular hurt and collision box for the character, and the hitboxes are all rectangles. Also, hitboxes do not currently take rotation as an argument, which means on any diagonal motion, you get a huge disjoint. While I can instantiate multiple square hitboxes to approximate a given attack, this really is not the ideal solution, and I'm going to try improving this to allow for different collision shapes.

That being said, currently there are Hitboxes, Hurtboxes and Grabboxes. Parries and shielding is assumed when the hurtbox is disabled, and based on character state, but I could afford to make them into their own classes too. Hitbox is a pretty beefy class, since all knockback calculation and hitstun and hitlag are handled in the hitbox class. The formula for this is available in great documentation on the [Smash Wiki](https://www.ssbwiki.com/Knockback), a majority of the setup is just in making sure you have access to the variables it asks for.

One note to add is that since I do not have a rigged model I can attach the hitboxes to, hitboxes are defined on a frame-by-frame basis, active for a given number of frames. This actually ends up being fine because of the animations staying on a given attack frame for a significant amount of time, but it does also mean that in-betweens that would hit in a 3d game do not over here.

That being said, I have a solution for future hit detection: runtime collision polygon bounding boxes. Godot has in-built support for generating collision polygons based on a given sprite2D node, but doing this for an animated sprite is a little frustrating. I also think that checking this every frame could be super resource intensive (especially if networked), so I'm only doing this when a given hitbox is entered, like when a successful attack is registered. Using the rectangular collision boxes as a bounding box, I can then convert the hurt object's sprite into a collision polygon, and check for collision with the relevant hitbox. This does not solve the in-between frame collision issue, and I have looked into frame interpolation as a potential solution, but that leaves a lot to be desired currently.

### Movement
One such example of changes I made compared to base smash is fixed 4-frame landing lag, as I don't really like L-cancelling as a mechanic, and feel like Rivals 2 made the right decision there. I also added the wavedash macro from rivals, but normal wavedashing should be in the game too. I haven't been particularly consistent in hitting them, so I think a bit more testing is in order, but wavelanding has felt pretty close to Melee. Other than that, you've got your:
- shorthop/fullhop/double jump
- dashdancing
- double jumps
- airdodges/rolls
- moonwalking

Most of the basics are in but some of the movement-related systems aren't in yet, like shield dropping, wall jumps, techs and ledgedashes (among others). In general, ledge states are kinda jank at the moment, and I'm trying to figure out a better system for it.

## Game Loop
You may notice that, so far, this is just a description of local multiplayer. I intend to have single player segments, inspired somewhat by smash singleplayer, and online multiplayer. I really want it to stand on its own as a single player game, like with how people still enjoy surfing in CSGO, and that'll be by creating fundamental gameplay systems that work for people.

I personally think my plans for integrating the two are pretty cool, but I don't want to spoil it too much. Keep an eye out.

# Graphics
## Animation
I initially animated everything with a fixed 100ms frame duration in Aseprite, but this was way too slow for fighting game timings, since that means each frame is equal to roughly 6 frames in engine at 60fps. That said, animating at actual 60fps (17ms between frames) is way too much work and it also looks too fluid for pixel art, so I'm working with a variable fps, with anywhere from 33-100ms frame timings depending on the animation. A lot of animations have more frames on startup than during endlag, so they come out quick, and linger for a while. As you can imagine, this is hell to manage in-engine, but it's good, honest work. In total, the Knight character has 242 frames of animation, and I envision this rising to 300 with all the nice-to-haves.

## Graphics Pipeline
This is one of the things I'm happiest for the current state of the game, and it's how I'm getting the blended 2d-3d look. A lot of the work has been done already, and I just had to put everything together to get the look I wanted. You could argue that graphics starts with the sprites, but all the sprites are flat colors, and unshaded. This is what the game looks like in its base state.

The pipeline is as follows:
### Automatic Normal map generation

### Lighting In-Engine

### Palette Remapping Shader

### CRT Shader

## Audio
### SFX
It's there, but it's mostly placeholders right now. I don't want to commit too hard to the bitcrushed audio sound, but I probably will have a slight effect on the bus. Currently, I think damage in particular is grating, but I'm in the process of finding better sounds. Admittedly, audio is one of my weaker points, and I haven't worked on audio systems enough to know about the magic that audio engineering entails.

Each character currently only has voice sfx on specials, grabs, and taunts. I'm undecided on voice acting, and frankly don't think I'll have full VA. I think there's a charm to basic grunts with each dialong bos to indicate tone, or a beep noise on every letter like in classic JRPGs. Animal-crossing style phonetic sounds are also in fashion right now, but they don't feel authentic to what I'm doing.

### Music
I've worked on some songs for the soundtrack, but haven't really been happy with any of them except the main menu theme. It interpolates a sweet trip song. Here's the inspo:
[![main theme](https://img.youtube.com/vi/FseYuqzoLSQ/0.jpg)](https://www.youtube.com/watch?v=FseYuqzoLSQ)

## Tools
A lot of the work I've been doing has been in making tools that allow for the creation of skins, characters, and swaps easier.

### Palette Swapping

### Animation setup in Aseprite

### Batch Editing Script


# Clairvoyance
What does the future hold?
## WIP
### Inputs
The godot input system leaves a lot to be desired.
- Buffer
- Stick sensitivity (soft presses)
- Controller inconsistency
- Input remapping
- Macros

## Planned roadmap
- 1 more character
- Gameplay changes
- Rollback Networking using GodotSteam and Delta
- Singleplayer

![banner](/images/dunjin1/wizard-downb-bg.gif)
