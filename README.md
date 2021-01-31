# PasswordRunes
Set of runes (tiles) to assist in generation and management of high entropy secret passwords
The runes are square tiles with 3x3 pattern of black and white dots on each face.

## Prior Art
- DiceWare https://diceware.dmuth.org/ -- system of generating english passphrases by rolling dice
- DiceKeys https://dicekeys.com/ -- system of generating and storing passphrases by rolling dice
- [ElsieFour](https://eprint.iacr.org/2017/339.pdf)  -- human executable encryption algorithm that uses 36 labeled tiles as an encryption device and a random permutation of 36 tiles as a key

The main inspiration is DiceKeys project. I wanted something that is easier to make and easier to store and copy by hand.

## Dimensions
The runes are square tiles with rounded corners. The square side is 5/8" and the radius of a corner is 1/16". I've chosen 5/8" because this is same size the standard dice cubes are. Rounded corners are needed to make shuffling and arranging runes into array structure easier (sharp corners tend to snag at each other). It would still be usable without rounded corners, but of your technology allows them, go for it, they are beneficial.

The dots of 3×3 pattern have centers with coordinates x,y ∈ {0,±1/6"}, where (0,0) is the center of a tile. They can be circle, square, diamond, or any other shape with D4 symmetry. The shapes should be small enough so that neighbours do not overlap. For drilling or punching, the circle is probably the easiest to implement, so I expect it to be the default shape.

Thickness depends on the available material. Plywood and acryliuc often comes in 1/8" and to me it feels about right. I think 1/4" would be too thick and 1/16" too thin. For 5/8" tile.

## Rune sets
The patterns for each set are chosen in such a way that each face in any of the 4 orientations is distinguishable from any other face in any orientation.

### PasswordRunes60
All possible 3x3 2 color patterns that remain different under all 4 rotations. There are 120 such patterns. Since each rune has 2 sides, this allows for a set of 60 runes. 60 distinct runes arranged in random order, each in one of 8 possible positions gives log2(60! \* 2^60 \* 4^60) ~= 452 bits of entropy.

[More details](60/README.md)

### PasswordRunes36 (Chaos Runes)
It is possible to select 72 out of 120 pattenrs of PasswordRunes60 and combine them into 36 tiles which are easier to manufacture on laser cutter or 3d-printer.
This set of 36 runes allows passords with up to log2(36!)+36*3=246 bits of entropy.

[More details](36/README.md)

### PasswordRunes18
PasswordRunes36 come in pairs: with and without a dot in the center, all other dots being identical. Therefore it is possible to separate the set into 2 visually homomorphic subsets. Alternatively, the dot pattern for the subset without a central dot may be rearranged by moving side dots closer towards the center. This gives patterns that are less obviously "rectangular", which may be beneficial for some applications.

The set of 18 runes allows passords with up to log2(18!)+18*3=106 bits of entropy. This is probably not enough for long term keys, but may still be acceptable in some situations.

[More details](18/README.md)

### Other sets
I considered other underlying patterns of dots and more than 2 colors.

Summary of these considerations are presented in the following table. It shows the number of eligible patterns for a configurations of a given number of dots and given number of colors. The underlying (uncolored) pattern of dots must be symmetric under rotation, so it can only be 4n or 4n+1 dots.

colors:|2|3|4|5
dots| | | | 
4     |   3|    18|       60|      150
5     |   6|    54|      240|      750
8     |  60|  1620|    16320|    97500
9     | 120|  4860|    65280|   487500
12    |1008|132678|4.19e6|6.10e7
13    |2016|398034|1.67e7|3.05e8

It looks like, the most obvious choice of 2 colors and 3x3 pattern of dots provides opportunity for the adequate amount of entropy in generated passwords, while being at the same time not too large, overall aesthetically pleasing, and easy to make.

Interstingly, there are 150 eligible 2×2 patterns colored in 5 colors. This is exactly enough to label all faces of 25 dice cubes. This is equivalent to DiceKeys in terms of available entropy.

## Software
The primary intended purpose of PasswordRunes is to assist in generating a passphrase *without* a computer.
However, having a utility that is capable of scanning the image of rectangular arrangement of runes and converting it into a usable password seems like a good idea.
The pattern structure of the runes is simple and regular. It may be possible to create an implementation of a simple scanner that can be complrehended and trusted by an average crypto-nerd.

DiceKeys has such scanning component (in a form of javascript library). I cannot comment yet on its readability.

## Other projects

* https://gist.github.com/atoponce/86308d5cc0500dd1db7914000afdf885 -- implements a roll of 36 out of 120 tiles.
