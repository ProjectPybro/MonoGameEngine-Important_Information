# Vector2
#### Why they matter
A Vector is a type of matrix, specifically a Matrix with only 1 column (Column Matrix). Vector2 just means it has 2 rows and 1 column.
Thats right, our Math class is actually important for Game Dev!

Why is this important? Well its a great way of storing data. A Vector2 can store the X and Y coordinates of an object.  
If you think about it, the easy way of storing coordinates (24, 32) is really just a column matrix.


A separate Vector2 can also store the X and Y Velocity.  

The velocity combines 2 key pieces of information:
- The direction its going on the X and Y axis (which is a unit vector)
- The speed of the object (magnitude)


### Why Do We Normalize the Vectors?
Normalizing a Vector means turning it into a Unit Vector which have combined length (magnitude) of 1.

For example:
- If your going only RIGHT, your vector would be (1, 0)
- If your going only DOWN, your vector would be (0, 1)
- If your going RIGHT and DOWN, your vector would go from (1, 1) to (~0.7, ~0.7)

This is important because if you don't normalize the Vector, it means the object will actually go faster going diagonal than straight.
This is why in old games like Doom, moving diagonally would get you more speed.


Once the Vector is normalized, then you can apply the magnitude (the speed of the object). Don't apply the speed before hand, because normalizing the vector will lose it.

    Both (1, 1) and (900, 900) becomes (~0.7, ~0.7) when normalized.


### Lets put this in Practice

Lets say the player wants to go mostly right and a little down.

```C#
Vector2 playerVector = new Vector2(1.0f, 0.5f);
playerVector.Normalize();
// {X:0.8944272 Y:0.4472136}

playerVector *= 200;
// {X:178.88544 Y:89.44272}
```

