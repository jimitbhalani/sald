#Sprite Library

1. Create a new sprite object in your game scene file like below

var sprite = require('sald:Sprite.js');
var heroImg = require('../img/spritesheet.png'); 

All the spritesheet objects to be animated have to be strictly defined as below: 

var heroSprite = new sprite(heroImg, {
	'walk' : {
		x:0,y:0,
		width:40,height:60,
		size:4
	},
	'run' : {
		x:0,y:60,
		width:40,height:60,
		size:4
	}
})

The first parameter is the spritesheet image, heroImg in this case is the entire spritesheet image with several different animation frames within it.
The second parameter has to be a list of animations by name along with x, y, width, height and size properties.

[x,y represent the indexes in pixel coordinates of start column and row of animation from the spritesheet image]
[width,height represent the width and height of each sprite in pixel size, you can check the same in paint for image width and height in pixels]
[size is the max number of frames till which that animation needs to be played from the spritesheet image]

A note about proper sprite splicing: The x and y properties above are what the engine will ultimately use to splice the individual sprites from the sprite
sheet. x is the horizontal offset, while y is the vertical offset (with 0,0 representing the top-left corner of the image). There are two things to keep in mind
when dealing with pixel coordinates. One - if you truly wish to have well defined and proportional sprites, it helps if the pixel width is divisible by the number 
of columns and the pixel height is divisible by the number of rows. Otherwise you risk them being clipped at weird positions. Two - If you wish to
start cutting from the middle of a sprite sheet and not from the far left, you'll need to make sure that you're providing the top-left corner of the sprite you wish
to start at (not the center of the sprite).
