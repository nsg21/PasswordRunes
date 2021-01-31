# PasswordRunes
Set of runes (tiles) to assist in generation and management of high entropy secret passwords


## Prior Art
- DiceWare https://diceware.dmuth.org/
- DiceKeys https://dicekeys.com/

The main inspiration 

## Rune sets

The runes are square tiles with 3x3 pattern of black and white dots on each face.
The patterns for each set are chosen in such a way that each face in any of the 4 orientations is distinguishable from any other face in any orientation.

### PasswordRunes60
All possible 3x3 2 color patterns that remain different under all 4 rotations. There are 120 such patterns. Since each rune has 2 sides, this allows for a set of 60 runes. 60 distinct runes arranged in random order, each in one of 8 possible positions gives 452 bits of entropy.

[More details](60/README.md)

### PasswordRunes36
Set of 36 runes allows passords with up to 246 bits of entropy.

[More details](36/README.md)

### PasswordRunes18
Set of 36 runes allows passords with up to 246 bits of entropy.

[More details](18/README.md)

### Other sets
I considered other underlying patterns of dots and more than 2 colors.

Summary of these considerations are presented in the following table:

It looks like, the most obvious choice of 2 colors and 3x3 pattern of dots provides opportunity for the adequate amount of entropy in generated passwords, while being not too large and overall aesthetically pleasing.


## Software
The primary intended purpose of PasswordRunes is to assist in generating a passphrase without computer.
However, having a utility that is capable of scanning the image of rectangular arrangement of runes and converting it into a usable password seems like a good idea.
The pattern structure of the runes is simple and regular. It may be possible to create a 

DiceKeys has such scanning component (in a form of javascript library)

## Other projects

* https://gist.github.com/atoponce/86308d5cc0500dd1db7914000afdf885 -- implements a roll of 36 out of 120 tiles.
