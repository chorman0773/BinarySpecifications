# ShadeNBT #

This Site/Directory is the main page for Versions of the ShadeNBT Specification. 

The ShadeNBT Specification is used to provide some strong protection against corrupt save files, while maintaining Binary Version Compatability, using the easily used Named Binary Tag Format, created by Markus "Notch" Person, for the Game Minecraft. 


The ShadeNBT Specification is designed to be easy to implement. 
Existing NBT Libraries may even be built ontop of to implement the specification. 
However, not all valid NBT Files can be used inside a valid ShadeNBT File, and not all NBT Files that can be used inside a ShadeNBT File are Valid Standalone NBT Files. There are various differences between the specifications:
1. The original NBT Specification allows for gzip compressed NBT Files, while ShadeNBT offers no such option. However ShadeNBT Files themselves may be compressed using a variety of compression algorithms, including gzip. 
2. The original NBT Specification has a hard upper limit for the number of nested Compound and List Tags, at 32, while ShadeNBT Implementations are required to support at least 128. 
3. For compliance with LCLib Binary IO, NaN values are prohibited in both `TAG_Floats` and `TAG_Doubles`. 

The above list is not exhaustive, there are a large number of differences between the normal NBT Specification, and the Specification for the "NBT Part" of the ShadeNBT Specification. 

## Released Versions ##

So Far, 3 versions of the ShadeNBT Specification have been released, the latest being 1.2. Each Version can be found here:

[1.0](https://chorman0773.github.io/BinarySpecifications/ShadeNBT/1.0)

[1.1](https://chorman0773.github.io/BinarySpecifications/ShadeNBT/1.1)

[1.2](https://chorman0773.github.io/BinarySpecifications/ShadeNBT/1.2)



