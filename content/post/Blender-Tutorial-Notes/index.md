---
title: "Blender Tutorial Notes"
description: "Tutorial Link: https://www.youtube.com/watch?v=1jHUY3qoBu8"
date: 2021-03-03T16:48:34+08:00
categories:
    - Blender
tags:
    - Blender
---


View: Numpad 1 / 3 / 7, or `ctrl` + Numpad 1 / 3 / 7



`E` to extrude

> `alt` + `E ` face normal

`I` to insert

> double lick `I`
>
> `B` while doing insert (if `B` does not work, press `I` again to disable **individual faces**) (e.g. car window)



`G`

`S`

`R`



`O` proportional editing (when modeling the tree)



`ctrl` + `B` Bevel



`alt` + `S` shrink / flatten



`shift` + `right click` place 3D curser

> `shift` + `S` > Cursor to selected
>
> `shift` + `C` re-center 3D curser 



`L` select linked (in edit mode)

> `shift` + `L` to deselect linked



## Selection Method

`L`

Loop select: `alt` + click on edge (in **face selection mode**)

circle select: `C`

> deselect: middle mouse



ring select: `alt` + `ctrl` (in **edge select mode**)

Loop select: `alt` + click on edge (in **edge selection mode**)

select shortest path: `ctrl` (in **edge select mode**)



box select: `B` (in **vertex select mode**)



`alt` + `Z` enable/disable X-ray (to select the back vertices)



Lasso select (套索): `ctrl` + right mouse button 



Grow selection (select all faces neighboring to the selected face): `ctrl` + Numpad plus `+`

> Shrink selection (opposite to **grow selection**): `ctrl` + `-` 



select random

select similar: `shift` + `G` 



checker deselect (间隔选中效果，像足球那样): `F` 

`H` hide selected objects

> `alt` + `H` unhide all



`ctrl` + `I`: Invert selection (选中所有未被当前选中的东西)

---

Loop cut: `ctrl` + `R` 



Knife tool: `K` 

> `ctrl`: snap to center with knife tool 
>
> `C`: angle constraint with knife tool 



`ctrl` + 1-5: **subdivision modifier** (remember to **apply** this modifier)

> if it make the object **not low-poly**, then use **Decimate modifier** to make it back to low-poly.
>
> (see video around 48:00)



`,`: Orientation



snap (上方的磁贴icon) (hotkey: `ctrl` when using `G`) ----> 把两个vertices连在一起 (注意：这样snap后，实际上仍然是两个vertices) ------> two solutions

> 1. use **snap** along with **Auto Merge Vertices**
> 2. after **snap**, `A` to select all, then `M` to merge `merge by distance` 

> snap along an **axis**, instead of snap two vertices, to **align**



after delete some faces, use `F` to **Fill / Create face(s)** (自动填补holes)

> 1. select the whole object and `F`
> 2. select certain edges and `F` 



after selecting 2 vertices, press `J` / `F` to add an edge between these 2 vertices (`J` will make the object more low-poly, while `F` simply add an edge without affecting the original shape)



Besides `J`, we can use `ctrl` + `T` to **Triangulate selection** to make a round face more low-poly after using `F` to **Fill a hole**



setting: enable **Backface Culling** 

`F3` search **flip normal** (or `alt` + `N`)

some faces are **flipped**, to fix it `alt` + `N` > **recalculate outside** 



`X` dissolve edges



To connect two meshes inside one object into one single mesh, select two faces which you want to connect and `F3` > **Bridge Edge Loops** 



tips: `shift` + `D` to duplicate a face, `right mouse` to put the new face exactly the same location as the original one



Separate selection to new object: `P` 

Merge into a single object: `ctrl` + `J` 



## Modifiers

Mirror modifier (use **auto mirror** add-on)



Subdivision surface modifier: `ctrl` + `5 or other` (subdivide a plane to create low-poly island)



Displace modifier (low-poly landscape) 



Skin modifier (use with **extra mesh add-on**, so that we can add **single vertex**, and then build a low-poly tree)

> `A` to select all, and then `ctrl` + `A` to scale



---

## Tips

If we scare the object outside edit mode, `ctrl` + `A` > apply scale to make the scare `1, 1, 1` again!



`Numpad .`: to make viewport rotate around selection