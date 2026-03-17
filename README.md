# ZBrush Multi-SubTool Subdivision Macros

A small set of ZBrush macros for editing subdivision levels across multiple subtools.

These macros are designed to support workflows where subdivision levels need to be temporarily removed — particularly when inserting **IMM brush parts** that require the target subtool to have no subdivisions.

They are especially useful for preserving **UVs when working with IMM brushes**.

---

## 📦 Included Macros

- **DelLowerVisibleSubtools**  
  Moves all *visible* subtools to their highest subdivision level, then deletes all lower subdivision levels.

- **ReconstructVisibleSubtools**  
  Reconstructs subdivision levels for all *visible* subtools.

- **DelLowerAllSubtools**  
  Deletes lower subdivision levels for *all* subtools (including hidden ones).

---

## ❗ The Problem

When inserting an **IMM mesh part** in ZBrush:

- The target subtool must have **no subdivision levels**
- The target subtool must already have **UVs** (if you want the IMM UVs to be preserved)

If the target has no UVs, the IMM UVs are lost.  
If the target has subdivisions, the IMM cannot be inserted.

This creates a frustrating workflow conflict.

---

## ✅ Workflow Solution

### 1. Create UVs for all subtools

Before inserting IMM parts, give all relevant subtools basic UVs.

**Quick method:**
- Go to **ZPlugin → UV Master**
- Use **Unwrap All**
- Enable **Polygroups** and **Symmetry** if needed

This ensures IMM inserts will retain their UVs.

---

### 2. Delete lower subdivision levels

Run:
This will:
- Move each visible subtool to its highest subdivision level
- Delete all lower subdivision levels

---

### 3. Insert IMM mesh

- Insert your IMM mesh onto the desired subtool
- Then use:


This separates the IMM into its own subtool.

**Benefits:**
- The IMM retains its UVs
- It becomes a separate, manageable mesh
- The original mesh remains intact

---

### 4. Rebuild subdivision levels

Run:

This will:
- Cycle through visible subtools
- Rebuild subdivision levels until no more can be reconstructed

The loop is capped at **7 passes per subtool**, which is sufficient for most use cases.

---

## 🎯 Result

- IMM parts remain as separate subtools  
- UVs are preserved on inserted IMM meshes  
- Original subdivision levels are restored  

---

## 💡 Extra Tip

For straps, belts, or surface-conforming details:

This helps the IMM conform to the surface underneath.

---

## ⚙️ Installation

1. Save each macro as a `.txt` file  
2. Place them in:

3. Restart ZBrush

The macros will appear in the **Macro** menu.

---

## 🧪 Compatibility

- Tested in **ZBrush 2024**
- May work in other versions, but not fully tested

---

## ⚠️ Notes

- `Reconstruct Subdiv` depends on topology and may not always succeed
- Use on duplicated tools if you want a safe test pass
- These macros are workflow helpers, not a replacement for clean topology or UV workflows

---

## 🚀 Future Improvements

- ZPlugin version with a dedicated UI panel
- Additional batch tools for subtool workflows
- Expanded automation for game-ready asset prep

