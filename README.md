# ZbrushSubDivMacros
I've built a few zbrush macros for editing subdivisions over multiple subtools
These macros are useful for certain process (like adding IMM brush parts which need no subdivs on a subtool to work, see below for my IMM workflow) 

The macros
1. Zbrush macro for deleting all lower subdivisions from visible subtools and leaving the highest state. 
2. A seperate zbrush macro for then re-creating subdivisions for all visible subtools.
3. A macro that deletes all lowersubdivisons (including for hidden subtools)

This is my solution to retaining UV's for IMM brushes in Zbrush (which would otherwise all have to be rebuilt by hand)

The problem: In order to add an IMM mesh part to a subtool in zbrush the subtool needs to have no subdivisions. The subtool also needs UV's (if you want to retain the IMM's UVs, which I do, to save time UV unwrapping)

The Workflow Solution:

1. Firstly create quick and dirty UV's for all subtools (so that IMMs with UV's can be added)
  > In the subtools menu, select all low
  > In the Zplugin UV master, Unwrap all (with polygroups and symetry ticked if desired) 
  > This creates UV's for all subtools

2. Use the new 'DelLowerVisibleSubtools' macro to put all the subtools in their highest subdivision and delete all lower subdivs.
   > you can then add the IMM mesh where ever you choose and 'Split by masked points' in the subtool > split menu, this seperated the new IMM mesh from the part you have attached it to.
   (which is useful as you can then retain the UVs of the new IMM part and the IMM is then a seperate subtool)

3. Once the IMM has been seperated you can then user the 'ReconstructVisibleSubtools' macro
   > this cycles through every subtool and rebuilds it's subdivisions until it can no longer do so
   > I have set the reconstruct subdiv limit to 7, as anyone with more than 7 subdivisions per sub tool has a computer so powerful it's probablyt sentient anyway and wouldn't need these macros.

This process then results in you having IMM as sperate subtools that have retained their UV's, you can also do useful things with an IMM brush such as go into the brush menu > modifiers > projection strenght slider to 100 which conforms the IMM to the underneath shape of the subtool you are adding it to, which is great for straps etc. that you want to conform to a surface.  

To run in zbrush, these macros need to be placed in the following folder 
Zbrush/zstartup/Macros/Misc
They need to be added as .txt documents, zbrush will the load the macro and add the buttons (in the macros tab) on next start up. 
This works for Zbrush 2024 but may work in other versions. 
