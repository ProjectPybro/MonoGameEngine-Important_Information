# Tips and Tricks

## MonoGameEngine
* Scaling the player inside MonoGameEngine will fuck up its collision. Try to export the image to the desired size instead.
* MonoGameEngine disables the console so Console.Write won't work. Use Debug.Write or Debug.WriteLine instead!
* The Camera is broken in the old BlankStudentProject.zip. Make sure you download the new one.
    * Programming and Planning > Resources > Programming Stage 4 - Building a Graphical Game > BlankStudentProject.zip
    * After downloading the new zip file, make sure you right click it and mark it as safe.
* SetDrawDebug(true) is a handy command to draw the collision box. Very useful when you are trying to figure out why your collisions aren't working properly.


## C#
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
* You can set default values. 
    * In the player constructor, it has the boolean drawDebug. It assumes that the value is false, unless its told otherwise.
    * This way, you don't have to make a ton of constuctors, while making it easy to adjust every object.

``` C#
public Player(bool drawDebug = false)
{
    SetDrawDebug(true);
}

// All of these work
new Player();      // False
new Player(false); // False
new Player(true);  // True
```
* You can also pick what values you want to change. 
    * Normally, if I wanted to set the drawDebug to true, I would need to go through and input values for speed and sprinting modifier first.
    * However, you can just call the parameter directly using a semi colon.
``` C#
public Player(float speed = 200.0f, float sprintingMultiplier = 2.0f, bool drawDebug = false) {}

// All of these work
new Player(200.0f, 2.0f, true)
new Player(drawDebug: true); 
```

