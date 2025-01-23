# Vector2
#### Why they matter
A Vector is a type of matrix, specifically a Matrix with only 1 row or 1 Column. Vector2 just means it has 1 row and 2 columns, or 2 rows and 1 column.
Thats right, our Math class is actually important for Game Dev!

Why is this important? Well its a great way of storing data. A Vector2 can store the X and Y coordinates of an object. 
If you think about it, the easy way of storing coordinates (24, 32) is really just a row matrix.


A separate Vector2 can also store the X and Y Velocity. 
The velocity combines 2 key pieces of information;
- The direction its going on the X and Y axis (which is a unit vector)
- The speed of the Object (magnitude)



### Why Do We Normalize the Vectors?
Normalizing a Vector means turning it into a Unit Vector which have combined length (magnitude) of 1.

For example:
- If your going only RIGHT, your vector would be (1, 0)
- If your going only UP, your vector would be (0, 1)
- If your going Right AND up, your vector would go from (1, 1) to (0.5, 0,5)

This is important because if you don't normalize the Vector, it means the object will actually go faster going diagonal than straight.
This is why in old games like Doom, moving diagonally would get you more speed.


Once the Vector is normalized, then you can apply the magnitude, I.E. the speed of the object.
As long as the Vector is normalized first, then we don't have to re-normalize it unless we have to create an entirely new direction.
