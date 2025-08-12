# Character Types

Character Types are [Scriptable Objects](https://docs.unity3d.com/6000.0/Documentation/Manual/class-ScriptableObject.html) that define core aspects of a character.

---

## Character Type Variants

### 1. Unified Character Type
Each character is a single spritesheet containing the fully assembled character and cannot be changed:  
- **Use Case:** Characters with fixed, pre-rendered appearances.  
- **Example:** Simplistic characters where their appearance is pre-determined and won't need to be changed.

[Read More → Unified Character Type](unified-character-type.md)

---

### 2. Layered Character Type
A set of separate spritesheets, each containing one visual layer of the character:  
- **Example:** Body, Outfit, Hairstyle, Accessory  
- **Use Case:** Modular characters where new characters can be created/edited at runtime.

[Read More → Layered Character Type](layered-character-type.md)