# Random Tips
* Scaling the player inside MonoGameEngine will fuck up its collision. Try to export the image to the desired size instead.
* MonoGameEngine disables the console so Console.Write won't work. Use Debug.Write or Debug.WriteLine instead!
* The Camera is broken in the old BlankStudentProject.zip. Make sure you download the new one.
    * Programming and Planning > Resources > Programming Stage 4 - Building a Graphical Game > BlankStudentProject.zip
    * After downloading the new zip file, make sure you right click it and mark it as safe.
* SetDrawDebug(true) is a handy command to draw the collision box. Very useful when you are trying to figure out why your collisions aren't working.

* Foreach is a handy alternative to a for loop when your looping through an array. Makes your code cleaner and more readably in my opinion.
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
