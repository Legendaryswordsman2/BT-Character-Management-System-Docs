# Character Type Base

The **`CharacterTypeBaseSO`** class defines a base configuration asset for all character types.

---

## Fields

### `CharacterTypeID`
- **Type:** `string`
- **Attributes:** `[SerializeField]`, `[Tooltip]`, `[BoxGroup("Settings")]`
- **Description:**  
  A **unique identifier** used to reference this character type. *Must be unique* across all character types.

---

### `BaseSpritesheet`
- **Type:** `Sprite`
- **Attributes:** `[SerializeField]`, `[Tooltip]`, `[BoxGroup("Settings")]`
- **Description:**  
  Defines the **required base sprite sheet** for the character type.  
  Set this spritesheets **`Sprite Mode`** to **`Multiple`** and slice it. Whenever this character is used the sprites in the `BaseSpritesheet` will be used and a shader will then  override them with the finalized character.  
  Character spritesheets with mismatched dimensions will be rejected when validated.

---

### `CharacterController`
- **Type:** `RuntimeAnimatorController`
- **Attributes:** `[SerializeField]`, `[BoxGroup("Settings")]`
- **Description:**  
  The animator controller asset assigned to characters of this type.  
  Animations inside this controller should use sprites in the `BaseSpritesheet`.

---

## Methods

### `IsValidCharacterSpriteSheet(Sprite sprite) → bool`
Checks if a given sprite matches the **width and height** of the `BaseSpritesheet`.  
- **Returns:** `true` if the sprite size matches; otherwise `false`.