# PasswordRunes
Set of runes (tiles) to assist in generation and management of high entropy secret passwords


## Prior Art
- DiceWare https://diceware.dmuth.org/ -- system of generating english passphrases by rolling dice
- DiceKeys https://dicekeys.com/ -- system of generating and storing passphrases by rolling dice
- [ElsieFour](https://eprint.iacr.org/2017/339.pdf)  -- human executable encryption algorithm that uses 36 tiles as an encryption device and a random permutation of 36 tiles as a key

The main inspiration is DiceKeys project. I wanted something that is easier to make and easier to store and copy by hand.

## Rune sets

The runes are square tiles with 3x3 pattern of black and white dots on each face.
The patterns for each set are chosen in such a way that each face in any of the 4 orientations is distinguishable from any other face in any orientation.

### PasswordRunes60
All possible 3x3 2 color patterns that remain different under all 4 rotations. There are 120 such patterns. Since each rune has 2 sides, this allows for a set of 60 runes. 60 distinct runes arranged in random order, each in one of 8 possible positions gives 452 bits of entropy.

[More details](60/README.md)

### PasswordRunes36
It is possible to select 72 out of 120 pattenrs of PasswordRunes60 and combine them into 36 tiles which are easier to manufacture on laser cutter or 3d-printer.
This set of 36 runes allows passords with up to 246 bits of entropy.

[More details](36/README.md)

### PasswordRunes18
PasseordRunes36 come in pairs: with and without a dot in the center, all other dots being identical. Therefore it is possible to separate the set into 2 visually homomorphic subsets. Alternatively, the dot pattern for the subset without a central dot may be rearranged by moving side dots closer towards the center. This gives patterns that are less obviously "rectangular", which may be beneficial for some applications.

The set of 18 runes allows passords with up to 106 bits of entropy. This is probably not enough for long term keys, but may still be acceptable in some situations.

[More details](18/README.md)

### Other sets
I considered other underlying patterns of dots and more than 2 colors.

Summary of these considerations are presented in the following table:

colors:|2|3|4|5
dots| | | | 
4     |   3|    18|       60|      150
5     |   6|    54|      240|      750
8     |  60|  1620|    16320|    97500
9     | 120|  4860|    65280|   487500
12    |1008|132678|4.19e6|6.10e7
13    |2016|398034|1.67e7|3.05e8

It looks like, the most obvious choice of 2 colors and 3x3 pattern of dots provides opportunity for the adequate amount of entropy in generated passwords, while being at the same time not too large, and, overall aesthetically pleasing.

Intersting note: there are 150 of 2×2 5 color patterns which lack any c5 symmetry. This is exactly enough to cover faces of 25 dice cubes. This is equivalent to dicekeys.

## Software
The primary intended purpose of PasswordRunes is to assist in generating a passphrase *without* a computer.
However, having a utility that is capable of scanning the image of rectangular arrangement of runes and converting it into a usable password seems like a good idea.
The pattern structure of the runes is simple and regular. It may be possible to create an implementation of a simple scanner that can be complrehended and trusted by an average crypto-nerd.

DiceKeys has such scanning component (in a form of javascript library). I cannot comment yet on its readability.

## Other projects

* https://gist.github.com/atoponce/86308d5cc0500dd1db7914000afdf885 -- implements a roll of 36 out of 120 tiles.
