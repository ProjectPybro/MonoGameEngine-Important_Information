#  Delta Time
Delta Time is one of the most important pieces of information to learn as a developer. Without DeltaTime, objects move faster on high FPS computers, and slower on low FPS computers.

For example, if you give a player the speed of 5, and update their movement every frame, what your really saying is that every frame that character will move 5 pixels. 

If you run it on a regular PC and get 60 FPS, that player you will go 300 pixels per second (5x60).
However, if you run it on a very powerful PC, and get 240 FPS, that player you will go 1,200 pixels a second (5x240).
If you run it on a terrible laptop and only get 30 FPS, the player only goes 150 pixels a second (5x30).

To give a recent example, on launch Marvel Rivals had a problem where certain characters like Doctor Strange would leap significantly higher if you had a high FPS compared to a low fps. 

This is because your speed is tied to your frame rate. Therefore, we need to make it frame-independent.

In comes DeltaTime. DeltaTime is the time between frames (technically the time between your last frame and the frame before that).
It's actually quite complex when you get into the weeds, [for more see here](https://www.youtube.com/watch?v=yGhfUcPjXuE), but the concept is simple.

If something is **moving every frame**, then you multiply it by delta time. 

```
SetPosition(GetX() + (Speed * deltaTime), GetY() + (Speed * deltaTime));
```

Its important to note that deltaTime is a small variable (if its running perfectly at 60 FPS, it will be 0.0166666).
This means speed will need to be massively increased. For example, a character that was going 5 pixels per frame at 60 fps, the speed will now need to be 300 to be the same.

You can think of speed * deltaTime as how many pixels in will move in a second, so a speed of 300 is 300 pixels/second.

It's important to know when to NOT use deltaTime, as it can be damaging when used incorrectly. It should not be applied to something thats moves only once. 
For example, if you have a enemy that instantly teleports 300 pixels, then you wouldn't apply deltaTime. Even if the teleport animation takes several seconds, as long as the calculation to determine where to teleport was done on a single frame, then deltaTime shouldn't be applied.

DeltaTime will also vary. If you have every played a performance heavy game before, you know that frame rates are always in flux, bouncing up and down constantly, meaning deltaTime will also be changing up and down.

For reference, heres some common delta times numbers with their framerate:
- 030: 0.0333333
- 047: 0.0212765
- 060: 0.0166666
- 106: 0.0094339
- 144: 0.0069444
- 244: 0.0041666