# Tips and Tricks

## MonoGameEngine
MonoGameEngine disables the console so Console.Write won't work. Use Debug.Write or Debug.WriteLine instead!  

Make sure you download the newest version of MonoGameEngine when making a new program.  
Programming and Planning > Resources > Programming Stage 4 - Building a Graphical Game > BlankStudentProject.zip
After downloading the new zip file, make sure you right click it and mark it as safe.  


Try and avoid putting things in Update() when possible. Remember, Update() will be called 60+, so only put code in there that NEEDS to be checked every frame.  

Ask people for help. Bashing your head against a problem for 6 hours straight will just make you miserable (I speak from experience). If you cannot figure out something, ask someone for help. 



### Scaling the player
SetDrawDebug(true) is a handy command to draw the collision box. Very useful when you are trying to figure out why your collisions aren't working properly.  
``` C#
// Use this in a GameObject to draw it's collision box
SetDrawDebug(true);
```
Scaling a GameObject inside MonoGameEngine won't scale its collision box accordingly.
``` C#
// Scale the Texture
GetSprite().SetScale(4, 4);

// Scale the Collision Box
SetBounds(
    GetSprite().GetTexture().Width * 4,
    GetSprite().GetTexture().Height * 4
    );

// We use GetSprite().GetTexture() to get the original images dimensions
 ```



### Too Much Nesting
```C#
if (x > 0)
{
    if (y > 5)
    {
        if (z > 10)
        {
            while (true)
            {
                switch(expression)
                {
                    case 0:
                        return false;
                        break;
                    case 1: 
                        return true;
                        break;
                }
            }
        }
        else
        {
            return false;
        }
    }
    else if (x == -2)
    {
        return true;
    }
}
```
See how this code is really hard to understand? Too many statements are nested inside of each other, so its hard to follow. When possible, try and avoid nesting statements too many times. For more, [check out this CodeAestetic Video here.](https://www.youtube.com/watch?v=CFRhGnuXG-4)  
It's worth noting that this is more personal opinion rather than objective fact. Other programmers may disagree with me.



## C#
### Shorthands
* Shorthand operators are a very useful tool for writing code faster.
    * For example, you already know the i++ from a FOR loop. 
    * i++ is a shorthand for i = i + 1

```C#
position = position + 200
health = health - 1
speed = speed * multiplier
score = score / 2
```

```C#
position += 200
health -= 1
speed *= multiplier
score /= 2
```



### W3Schools
If you forget how to do basic something in C#, W3Schools is a fantastic resource.
https://www.w3schools.com/cs/index.php



### Visual Studio Shortcuts
Here are some helpful shortcuts for Visual Studio 2022.  
All of these are extremely helpful, and you should use all of them!
* Control + /
    * Comments / Uncomments lines of code
* Control + Shift + /
    * Comments / Uncomments the selected area. Used for inline comments.
* Tab
    * Indents the highlighted piece of code
* Shift + Tab
    * Removes an Indent from the highlighted piece of code

#### Minor shortcuts
These shortcuts are less important, but still nice to know.
* Alt + Up or Down Arrow Key 
    * Moves the code up or down. Can work with one line or a highlighted segment.
* Shift + Any Arrow Key
    * Highlights code.
* Control + Left or Right Arrow Key
    * Moves by whole words instead of single characters
* Control + Shift + Any Arrow Key
    * Selects whole words. Useful in conjustion with Alt + Up or Down.
* Control + L
    * Deletes the line of code but copies it to your clipboard
* Control + Shift + L
    * Deletes the line of code without copying it. 
* Alt + Shift + Up or Down Arrow Key
    * Allows you to type the same thing on multiple lines at once. Usually not helpful, but once in a blue moon it can save you a ton of time.



### Formating Numbers
Formatting Numbers is a simple way to make text look nicer.
```C#
// Here I use $strings, but other strings should work.

float timer = 97.23921f;
Debug.WriteLine($"Time: {timer}s");       // Time: 97.23921s
Debug.WriteLine($"Time: {timer:0.00}s");  // Time: 97.24s

// 0 is a mandatory place, # is a optional place.
float timer = 123.0f;
Debug.WriteLine($"Time: {timer:0.00}s");  // Time: 123.00s
Debug.WriteLine($"Time: {timer:0.##}s");  // Time: 123s

float score = 450.23f;
Debug.WriteLine($"Score: {score:00000}"); // Score: 00450
Debug.WriteLine($"Score: {score:#####}"); // Score: 450
// Since there was no decimal place (.) in the string, its rounds to the whole number.
```
You can format numbers anytime you display them. For example, you can format numbers for a Text object.
```C#
// Code from my Wac-A-Mole Project
_timeDisplay.SetMessage($"Time: {_timeRemaining:0.00}"); // Rounds timer to 2 decimal places (12.25s).
_scoreDisplay.SetMessage($"Score: {_player.Score:00000}"); // Forces at least 5 zeros (00400)
```



## Foreach
* Foreach is a handy alternative to a for loop when your looping through an array. Makes your code cleaner and more readable in my opinion.
``` C#
// For Loop
// Enabling every bullet in array
for (int i = 0; i < _bulletArray.Length; i++)
{
    if (_bulletArray[i].IsActive() == false)
    {
        _bulletArray[i].Enable();
    }
}
```
``` C#
// Foreach Loop
// Enabling every bullet in array
foreach (Bullet bullet in _bulletArray)
{
    if (bullet.IsActive() == false)
    {
        bullet.Enable();
    }
}
```


## Default Values
You can set default values in your methods.  
In the player constructor, it has the boolean drawDebug. It assumes that the value is false, unless its told otherwise.  
This way, you don't have to make a ton of constuctors, while making it easy to adjust every object.

``` C#
public Player(bool drawDebug = false)
{
    SetDrawDebug(drawDebug);
}

// All of these work
new Player();      // False
new Player(false); // False
new Player(true);  // True
``` 



## Named Parameters
You can also pick what values you want to pass in. 
Normally, if I wanted to set the drawDebug to true, I would need to go through and input values for speed and sprinting modifier first.
However, you can just call the parameter directly using a semi colon.

``` C#
// Player Constructor
public Player(float speed = 200.0f, float sprintingMultiplier = 2.0f, bool drawDebug = false) {...}

// All of these work
new Player(200.0f, 2.0f, true)
new Player(drawDebug: true); 
```

This only works if the value is optional (I.E if it has a default value). Without a default value, you will have to insert an value for every parameter.




### Params
Params is an interesting keyword. Normally, you are only allowed to add a specific number of values, but params allows you to add as many, or as little as you want.
```C#
public void AddNumbers(params int[] numberArray)
{
    int total = 0;
    for (int i = 0; i < numberArray.Length; i++)
    {
        total += numberArray[i];
    }
    Debug.WriteLine(total);
}
```
For example, heres a method to add numbers. We can add as many or as little arguments as we want. 

```C#
AddNumbers(); // 0
AddNumbers(6); // 6
AddNumbers(92, 3); // 95
AddNumbers(20, 30, 60, 129, 21340, 123, 123, 123, 12, 94, 239); // 22293
```
Params can be any data type. They can be ints, floats, strings, chars, objects, you name it.

There is some limitations though.   
You can only have one params.  
Every value has to be the same data type (so you can't add ints and strings to the same params as they are different data types).  
Params must be the last paramater in the paramater list.
```C#
public void AddNumbers(params int[] numberArray, string test) {} // Error: Params must be the last paramater
public void AddNumbers(string test, params int[] numberArray) {} // This is fine
```

