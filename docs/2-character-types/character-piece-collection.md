# Character Piece Colletion


A [Scriptable Object](https://docs.unity3d.com/6000.0/Documentation/Manual/class-ScriptableObject.html) that acts as a layer for a Layered Character Type. It contains a list of all valid sprites that can be used for that layer of the character.

!!! Warning
    A `Character Piece Collection` with an empty `Character Pieces` list will be invalid!

---

## Fields

| Field                          | Description|
|---------------------------------|-----------:|
| Attached Character Type         | The Character Type the Collection is meant for
| Collection Name                 | A name for the collection used when displaying collection
| Character Piece Asset Label     | The label used to finds sprites for the collection
| Include NA Option               | Include a blank option at the start of the `Character Pieces` list

!!! Note
    `Character Pieces` list must be refreshed after toggling `Include NA Option`

---

## Buttons

| Button                      | Description|
|-----------------------------|-----------:|
| Get Character Pieces        | Finds all sprites using the assigned label
| Clear Character Piece       | Clears the `Character Pieces` list
