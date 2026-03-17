# ZbrushSubDivMacros
ZBrush Multi-SubTool Subdivision Macros

I built a small set of ZBrush macros for editing subdivision levels across multiple subtools.
These macros are useful for workflows where you need to temporarily remove lower subdivision levels from a subtool, especially when inserting IMM brush parts that require the target subtool to have no subdivisions.
They are mainly intended to help with an IMM + UV preservation workflow in ZBrush.

Included macros:
**DelLowerVisibleSubtools**
Moves all visible subtools to their highest subdivision level, then deletes all lower subdivision levels.
**ReconstructVisibleSubtools**
Reconstructs subdivision levels for all visible subtools.
**DelLowerAllSubtools**
Deletes lower subdivision levels for all subtools, including hidden ones.

**What problem this solves:**

When adding an IMM mesh part to a subtool in ZBrush, the target subtool usually needs to have no subdivision levels.
If you also want the inserted IMM part to retain its UVs, the target subtool needs to already have UVs. Otherwise the IMM UVs are lost.

This creates an awkward workflow:
the target subtool must have UVs
the target subtool must not have subdivision levels
after inserting the IMM, you may want to rebuild the original subdivision structure

These macros help automate that process.

**Workflow solution**

**1. Create UVs for all subtools**
Create quick UVs for all subtools before inserting IMM parts.

One simple quick and dirty method is:
In the SubTool menu, select all low subdivision subtools
In ZPlugin > UV Master, use Unwrap All
Enable Polygroups and Symmetry if needed
This gives every target subtool a UV set, which allows inserted IMM parts to retain their UVs.

**2. Delete lower subdivision levels**
Run the DelLowerVisibleSubtools macro.
This will:
move each visible subtool to its highest subdivision level
delete all lower subdivision levels

**3. Insert the IMM mesh**

Insert the IMM mesh part onto the chosen subtool.
After placing it, use:
Tool > SubTool > Split > Split Masked Points
This separates the new IMM mesh from the original subtool.

This is useful because:
the new IMM part remains a separate subtool
the UVs of the inserted IMM are retained
the original mesh stays easier to manage

**4. Rebuild subdivision levels**

Run the ReconstructVisibleSubtools macro.
This cycles through each visible subtool and repeatedly uses Reconstruct Subdiv until no more subdivision levels can be rebuilt.
The current loop limit is set to 7 passes per subtool, which should be more than enough for most practical cases.

**Result**

This workflow gives you:
inserted IMM parts as separate subtools
retained UVs on those IMM parts
restored subdivision levels on the original visible subtools

Extra tip for conforming IMM parts
For straps, belts, and similar surface details, you can also use:
Brush > Modifiers > Projection Strength = 100
This helps the IMM conform more closely to the surface underneath it.

**Installation**

To use these macros in ZBrush:
Save each macro as a .txt file
Place the files in:
ZBrush/ZStartup/Macros/Misc

Restart ZBrush
ZBrush should load the macros automatically and add them to the Macro menu.

Tested in ZBrush 2024.
It may also work in other versions, but that has not been fully tested.

**Notes**
These macros are intended as workflow helpers, not replacements for clean asset prep
Reconstruct Subdiv depends on topology and may not always succeed on every mesh
Use on duplicated tools first if you want a safer test pass
