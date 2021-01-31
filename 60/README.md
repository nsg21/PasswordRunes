# 60-rune set

There are 120 total available patterns, 2 per rune give 60 runes.
There are multiple ways to group 120 tiles in 60 pairs. Additionally, one element of each given pair can be rotated 4 different ways relative to the other element. This allows to "fingerprint" a set, by creating a pair matching unique for this set. This may be undesirable.

A canonical way to pair faces is this: each face pairs with its reflected inverse. Whenever a face has a dot in some position, the opposite face has a dot of other color in the position that is directly under it. In another words, if tiles were transparent and dots' 2 colors were opaque and transparent, each tile would look like 3x3 opaque pattern (opaque being on one and only one face in each case).

This pairing ensures that each rune has exactly same amount of each color.

## SVG pattern

In the following drawing rune faces are paird with their canonical partner
[PasswordTiles60.svg](PasswordTiles60.svg)
