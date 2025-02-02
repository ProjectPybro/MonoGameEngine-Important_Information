#  Delta Time
Delta Time is one of the most important pieces of information to learn as a developer. Without DeltaTime, the players move faster on high FPS computers, and slower on low FPS computers.

For example, if you give a player the speed of 5, and update their movement every frame, what your really saying is that character will move 5 pixels per frame. 

* If you run the game on a regular PC and get 60 FPS, that player will go 300 pixels per second (5x60).  
* If you run the game on a very powerful PC, and get 240 FPS, that player will go 1,200 pixels a second (5x240).  
* If you run the game on a terrible laptop and only get 30 FPS, the player only goes 150 pixels a second (5x30).

To give a recent example, on launch Marvel Rivals had a problem where certain characters like Doctor Strange would leap significantly higher if you had a high FPS compared to a low fps. This is because your speed is tied to your frame rate. Therefore, we need to make it frame-independent.

This is where DeltaTime come in. DeltaTime is the time between frames (technically the time between your last frame and the frame before that).
It's actually quite complex when you get into the weeds. [For more see here](https://www.youtube.com/watch?v=yGhfUcPjXuE), but the concept is simple.

If something is **moving every frame**, then you multiply it by delta time. 


```C
// Without DeltaTime
SetPosition(GetX() + Speed, GetY() + Speed);
```
```C#
// With DeltaTime
SetPosition(GetX() + Speed * deltaTime, GetY() + Speed * deltaTime);
```

Its important to note that deltaTime is a very small number (if the game is at a consistent 60 FPS, it will be 0.0166666).  
So, if you times your speed of 5 by 0.016666, your new speed is 0.083333, which is extremely slow.
This means the players speed will need to be massively increased.  
For example, if a character was going 5 pixels per frame at 60 fps, the speed will now need to be 300 to go the same speed.

You can think of speed x deltaTime as how many pixels it will move in a second. So a speed of 300 is 300 pixels/second.

### When to Not use DeltaTime
It's important to know when to NOT use deltaTime, as it can be damaging when used incorrectly. 

It should not be applied to something thats moves only once. 
For example, if you have a enemy that instantly teleports 300 pixels, then you wouldn't apply deltaTime. Even if the teleport animation takes several seconds, as long as the calculation to determine where to teleport was done on a single frame, then deltaTime shouldn't be applied.

Also keep in mind that DeltaTime will vary. If you have every played a performance heavy game before, you know that frame rates are always in flux, bouncing up and down constantly, meaning deltaTime will also be changing up and down.

For reference, heres some common delta times numbers with their framerate:
- 030: 0.0333333
- 047: 0.0212765
- 060: 0.0166666
- 106: 0.0094339
- 144: 0.0069444
- 244: 0.0041666