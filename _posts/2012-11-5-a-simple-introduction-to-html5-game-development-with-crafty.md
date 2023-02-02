---
title: "A simple introduction to HTML5 game development with Crafty"
tags:
  - JavaScript
  - Game Development
  - Crafty
---


As browsers become more and more capable, and JavaScript proliferates to all corners of the software development world, it was only a matter of time before we saw the rise of JavaScript game libraries.

A library that caught my eye recently was [Crafty](http://craftyjs.com/). Crafty embraces common JavaScript practices and patterns that not only make HTML5 games simple to write, but a joy to code.

## The basics

First, you must define a "viewport" for the game to run in. Crafty supports both the newer &lt;canvas&gt; element, as well a plain old &lt;div&gt; elements for less compliant browsers. To define a viewport, you only need to make a single call:

	Crafty.init(600, 400);

Crafty uses an "Entity Component System". Basically, each "thing", be it the player, an enemy, a bullet, a platform, or even the score, is a simple object that has one or more attributes attached to it. Instead of inheriting a bunch of classes or interfaces, you define the behavior an entity has by assigning it various components, much like CSS classes can be assigned to HTML elements.

A basic entity would be defined like this:

	Crafty.e("player, 2D, Canvas, Color, Twoway, Gravity, Collision")

Above, you can see a variety of components assigned to an entity (unfortunately the entity moethod is abbreviated as "e"). Some of the components have predefined functionality. The "Collision" component will cause the entity to check if it has intersected over entities. "Gravity" causes the entity to fall.

Components can be user-defined. I named this entity "player". All the pre-defined components have uppercase names. I'm using lowercase to denote my custom components. This convention is not required.

Unfortunately, just defining behavior via components is not enough. Some components, such as gravity, need to have additional information. Luckily, many Crafty objects support chaining. The following code tells the entity to stop falling when it intersects with another entity that is labelled as a "solid".

	Crafty.e("player, 2D, Canvas, Color, Twoway, Gravity, Collision")
		.gravity('solid');

## Events

Much like jQuery and other JavaScript frameworks, Crafty utilizes events to respond to situations within the game. The framework provides the standard bind, unbind, and trigger functions.

	Crafty.e("player, 2D, Canvas, Color, Twoway, Gravity, Collision")
		.gravity('solid')
		.bind('Moved', function(from) {
			if (this.hit('solid')) {
				this.attr({x: from.x, y:from.y});
			}
		});

The preceding code stops the player from walking through solid objects (which have the "solid" component). It accomplishes this by setting the player's x/y coordinates back to where they where from when that collision occurs.

## Simple game

Now that we have the basic principles, let's create a simple platformer (all 159 lines of it). Source available on [GitHub](https://github.com/Fammy/crafty-platformer) as well. But let's be honest, you really want to play this awesome game. Do that [here](http://famularo.org/Games/CraftyPlatformer).

	var stageW = 800;
	var stageY = 600;

	Crafty.init(stageW, stageY);
	Crafty.background('#00BFFF');

	Crafty.e("player, 2D, Canvas, Color, Twoway, Gravity, Collision")
		.color('#0000ff')
		.attr({ x: 0, y: 540, w: 15, h: 40 })
		.twoway(5, 5)
		.gravity('solid')
		.onHit("enemy", function(entities) {
			for (var i in entities) {
				if (entities[i].obj.y > this.y) {
					entities[i].obj.destroy();
					Crafty("score").each(function () {
						this.text(++this.score + " kabillion points");
					});
				}
				else {
					this.x = 0;
					this.y = 540;
				}
			}
		})
		.onHit("exit", function(entities) {
			for (var i in entities) {
				Crafty("score").each(function () {
					this.score += 100;
					this.text(this.score + " kabillion points");
				});
				this.x = 0;
				this.y = 540;
			}
		})
		.bind('EnterFrame', function () {
			if (this.x >= stageW - this.w) {
				this.x = stageW - this.w;
			}

			if (this.x <= 0) {
				this.x = 0;
			}
		})
		.bind('Moved', function(from) {
			if (this.hit('solid')){
				this.attr({x: from.x, y: from.y});
			}
		});

	// exit
	Crafty.e("exit, 2D, Canvas, Color, Collision")
		.color('#00ff00')
		.attr({ x: 785, y: 40, w: 15, h: 40 });


	// solids
	Crafty.e("solid, 2D, Canvas, Color, Collision")
		.color('#8B7355')
		.attr({ x: 0, y: 580, w: 800, h: 20 });

	Crafty.e("solid, 2D, Canvas, Color, Collision")
		.color('#8B7355')
		.attr({ x: 500, y: 540, w: 100, h: 20 });

	Crafty.e("solid, 2D, Canvas, Color, Collision")
		.color('#8B7355')
		.attr({ x: 550, y: 480, w: 100, h: 20 });

	Crafty.e("solid, 2D, Canvas, Color, Collision")
		.color('#8B7355')
		.attr({ x: 600, y: 420, w: 100, h: 20 });

	Crafty.e("solid, 2D, Canvas, Color, Collision")
		.color('#8B7355')
		.attr({ x: 760, y: 380, w: 40, h: 20 });

	Crafty.e("solid, 2D, Canvas, Color, Collision")
		.color('#8B7355')
		.attr({ x: 600, y: 320, w: 100, h: 20 });

	Crafty.e("solid, 2D, Canvas, Color, Collision")
		.color('#8B7355')
		.attr({ x: 320, y: 280, w: 100, h: 20 });

	Crafty.e("solid, 2D, Canvas, Color, Collision")
		.color('#8B7355')
		.attr({ x: 120, y: 240, w: 40, h: 20 });

	Crafty.e("solid, 2D, Canvas, Color, Collision")
		.color('#8B7355')
		.attr({ x: 0, y: 200, w: 40, h: 20 });

	Crafty.e("solid, 2D, Canvas, Color, Collision")
		.color('#8B7355')
		.attr({ x: 160, y: 160, w: 80, h: 20 });

	Crafty.e("solid, 2D, Canvas, Color, Collision")
		.color('#8B7355')
		.attr({ x: 320, y: 120, w: 20, h: 20 });

	Crafty.e("solid, 2D, Canvas, Color, Collision")
		.color('#8B7355')
		.attr({ x: 360, y: 120, w: 20, h: 20 });

	Crafty.e("solid, 2D, Canvas, Color, Collision")
		.color('#8B7355')
		.attr({ x: 400, y: 120, w: 20, h: 20 });

	Crafty.e("solid, 2D, Canvas, Color, Collision")
		.color('#8B7355')
		.attr({ x: 500, y: 80, w: 300, h: 20 });

	Crafty.e("solid, 2D, Canvas, Color, Collision")
		.color('#8B7355')
		.attr({ x: 200, y: 380, w: 60, h: 20 });

	Crafty.e("solid, 2D, Canvas, Color, Collision")
		.color('#8B7355')
		.attr({ x: 200, y: 360, w: 20, h: 20 });


	// score
	Crafty.e("score, Canvas, 2D, Text")
		.attr({ x: 5, y: 0, w: 100, h: 15, score: 0 })
		.text("0 kabillion points");

	setInterval(function () {
		if (Crafty.isPaused()) {
			return;
		}

		SpawnEnemy(780, 0);

	}, 5000);

	function SpawnEnemy(x, y) {
		Crafty.e("enemy, 2D, Canvas, Color, Twoway, Gravity, Collision")
			.color('#ff0000')
			.attr({ x: x, y: y, w: 15, h: 40, dX: 2 })
			.gravity('solid')
			.bind('EnterFrame', function () {
				this.x += this.dX;
			})
			.onHit("solid", function() {
				this.dX *= -1;
			})
			.bind('EnterFrame', function () {
				if (this.x >= stageW - this.w) {
					this.x = stageW - this.w;
					this.dX *= -1;
				}

				if (this.x <= 0) {
					this.x = 0;
					this.dX *= -1;
				}
			});
	}

## In closing

If you are comfortable with JavaScript and want to make browser-based games, Crafty is an excellent place to start. I've only touched on a few features of Crafty, but hopefully this small tutorial whets your appetite.