### Overview

If you want to generate a random number, use the `arc4random_uniform` method. Here are a few examples of how you use it:

```
// To generate a random number between 0 and 9
x = arc4random_uniform(10);

// To generate a number from 100 to 199
x = arc4random_uniform(100) + 100;

// To generate a number from -10 to 10
x = arc4random_uniform(21) - 10;
```