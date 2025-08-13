# LayeredCharacterTypeSO

`LayeredCharacterTypeSO` is a Unity `ScriptableObject` that defines a layered character type for the **BlazerTech Character Management System**.  
It extends [`CharacterTypeBaseSO`](./CharacterTypeBaseSO.cs) and implements the `IValidatable` interface.

This asset stores configuration for a layered character's appearance, creation settings, material, and associated piece collections.

---

## Overview

- **Inherits:** `CharacterTypeBaseSO`
- **Implements:** `IValidatable`
- **Menu Path:** `BlazerTech Character Management System/Layered Character Type`
- **Purpose:**  
  Manages layered character definitions, including initialization, validation, asset loading/unloading, and editor utilities.

---

## Serialized Fields

### From `CharacterTypeBaseSO`
- **CharacterTypeID** (`string`, read-only)  
  Unique identifier for this character type.

- **BaseSpritesheet** (`Sprite`, read-only)  
  Reference sprite used for validation and sizing checks.

- **CharacterController** (`RuntimeAnimatorController`, read-only)  
  Animator controller for the character.

---

### From `LayeredCharacterTypeSO`

#### Main Settings
- **CharacterPreviewSettings** (`CharacterPreviewsSettings`, read-only)  
  Controls how character previews are generated.

- **characterCreationSettings** (`CharacterCreationSettings`)  
  Settings used during character creation (e.g., name formatting).

- **CharacterPieceCollections** (`List<CharacterPieceCollectionSO>`, read-only)  
  Collections of character pieces that make up the layered character.

---

## Runtime Properties

- **CharacterMaterial** (`Material`, read-only)  
  The material assigned during initialization.

---

## Public Methods

### Initialization & Validation
- **`bool Initialize(Material characterMaterial)`**  
  Initializes the layered character type with the provided material.  
  Returns `true` if already initialized or if successful; `false` if any collection fails to initialize.

- **`bool IsValid()`**  
  Validates the character type:  
  - `CharacterTypeID` must not be empty.  
  - `BaseSpritesheet` must be set.  
  - All `CharacterPieceCollections` must be valid.

- **`bool IsInitialized()`**  
  Checks if the object is initialized for the current session.

---

### Asset Management
- **`Task AcquireAllCharacterPiecesAsync(Action<float> onProgress = null)`**  
  Asynchronously loads all character pieces from the collections, reporting progress as a value between `0.0` and `1.0`.

- **`void ReleaseAllCharacterPieces()`**  
  Releases all loaded character pieces from memory.

---

### Editor Utilities
*(Editor-only methods; wrapped in `#if UNITY_EDITOR`)*
- **`void GetCharacterPiecesForCollections_EditMode()`**  
  Retrieves character pieces for each collection in edit mode.

- **`bool IsInResourcesFolder_EditMode()`**  
  Checks if this asset resides in a `Resources/` folder.

---

## Nested Classes

### `CharacterCreationSettings`
- **UseCleanCharacterPieceNames** (`bool`)  
  If `true`, underscores in character piece names are replaced with spaces.

---

### `CharacterPreviewsSettings`
- **CharacterPreviewController** (`RuntimeAnimatorController`)  
  Animator used for character preview rendering.

- **CharacterPlaceholderSprite** (`Sprite`)  
  Placeholder image when a preview is not available.

- **BaseCharacterPieceCollection** (`CharacterPieceCollectionSO`, read-only)  
  The base character piece used in previews.

- **BaseCharacterPieceLoadedSpriteIndex** (`int`, read-only)  
  Index of the base sprite within the base collection.

- **PreviewFrameWidth** (`int`)  
  Width (in pixels) of a preview frame.

- **PreviewFrameHeight** (`int`)  
  Height (in pixels) of a preview frame.

- **CharacterPreviewFrameIndex** (`int`)  
  Index of the preview frame to use.

---

## Usage Example

```csharp
[SerializeField] private LayeredCharacterTypeSO myLayeredCharacterType;
[SerializeField] private Material myCharacterMaterial;

private async void Start()
{
    if (myLayeredCharacterType.Initialize(myCharacterMaterial))
    {
        await myLayeredCharacterType.AcquireAllCharacterPiecesAsync(progress =>
        {
            Debug.Log($"Loading progress: {progress * 100}%");
        });
    }
}
