#📜 InspectorMaster Usage Examples 🚀

This is a complete guide to InspectorMaster, demonstrating layout tools, visual styling, conditional logic, data drawers and powerful inspector enhancements for Unity.
---
#📘 Integration Guide — Adding InspectorMaster to Your Unity Project

This guide explains how to integrate InspectorMaster into your scripts to create advanced custom Inspector layouts, conditionally visible fields, visual organization, and better workflow.
---

🧩 Step 1 — Import the InspectorMaster Toolkit

Before using any InspectorMaster feature, ensure the InspectorMaster package is imported into your Unity project.
It should be located under:

Assets/InspectorMaster/
---

📚 Step 2 — Add the Namespace

To access all InspectorMaster attributes and tools inside your C# scripts,
include the following namespace at the top of your file:

```csharp
using InspectorMasterTool;
```
---
🌟 LAYOUT ORGANIZATION TOOLS

| **Attribute**   | **Purpose**                                                           | **Code Example**                                            | **Notes**                                                                                    |
| --------------- | --------------------------------------------------------------------- | ----------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| `[TabGroup]`    | Groups fields into clickable tabs, ideal for complex components.      | `[TabGroup("Settings")]`                                    | Fields sharing the same string name appear in one tab.                                       |
| `[BoxGroup]`    | Displays fields within a visually distinct, labeled box.              | `[BoxGroup("Core Stats")]`                                  | Works well within tabs or standalone.                                                        |
| `[Foldout]`     | Creates an expandable/collapsible section for hiding/showing fields.  | `[Foldout("Debug Info")]`                                   | Useful for optional or advanced settings.                                                    |
| `[IndentSpace]` | Controls layout spacing (vertical) and hierarchy (horizontal indent). | `[IndentSpace(10f)]` `[IndentSpace(2)]` `[IndentSpace(-1)]` | Takes a float for vertical space (PropertySpace) or an integer for horizontal indent levels. |

---
II. VISUAL & STYLING ATTRIBUTES

Attributes for enhancing visual appeal, providing feedback, and improving data readability.
| **Attribute**      | **Purpose**                                                | **Code Example**                                                      | **Notes**                                                                               |
| ------------------ | ---------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| `[Title]`          | Displays a large, stylized header above a field or group.  | `[Title("Setup", InspectorColor.Green)]`                              | Uses an InspectorColor for the line/text color.                                         |
| `[LabelText]`      | Overrides the field's C# name with a custom label string.  | `[LabelText("Health Points")]`                                        | Useful for clearer UI terminology.                                                      |
| `[LabelColor]`     | Changes the color of the field's main label text.          | `[LabelColor(InspectorColor.Yellow)]`                                 | Uses the InspectorColor enum.                                                           |
| `[LabelAttribute]` | Adds a custom suffix/prefix label next to the field value. | `[LabelAttribute("mana/sec")]`                                        | Used for indicating units or context (Suffix Label equivalent).                         |
| `[InfoBox]`        | Displays a context-sensitive message box.                  | `[InfoBox("Error!", InfoMessageType.Error)]`                          | Uses InfoMessageType to determine the icon (Info, Warning, Error).                      |
| `[ProgressBar]`    | Shows a real-time progress bar representation.             | `[ProgressBar("CurrentPercentage", "MaxHealth", InspectorColor.Red)]` | Takes a string for the current value member (field or method) and the max value member. |
| `[PreviewField]`   | Displays a texture, sprite, or other object asset preview. | `[PreviewField(100, 100)]`                                            | Takes optional width and height parameters.                                             |
---
III. CONDITIONAL LOGIC & VALIDATION

Attributes for creating dynamic Inspectors that hide, show, disable, or validate fields based on runtime conditions.

| **Attribute**       | **Purpose**                                                                  | **Code Example**                                          | **Notes**                                                                                              |
| ------------------- | ---------------------------------------------------------------------------- | --------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| `[ShowIf]`          | Shows the field only if the specified member (field or method) is true.      | `[ShowIf("isFlying")]`                                    | Checks the member string for a value of true (default condition).                                      |
| `[DisableIf]`       | Grays out and prevents editing of the field if the specified member is true. | `[DisableIf("isReadOnly")]`                               | Ideal for protecting fields based on state.                                                            |
| `[Required]`        | Visually flags the field if it is null, empty, or zero.                      | `[Required]`                                              | Enforces minimum data integrity for objects, strings, lists, etc.                                      |
| `[ReadOnly]`        | Displays the field's value, but disables all editing functionality.          | `[ReadOnly]`                                              | Must be placed on a public or serialized field.                                                        |
| `[ShowInInspector]` | Forces a private field or property to be displayed in the Inspector.         | `[ShowInInspector]`                                       | Allows displaying internal state without making fields public.                                         |
| `[EnhancedRange]`   | An advanced slider that can take dynamic limits from other fields/members.   | `[EnhancedRange("MinLimitField", "MaxLimitField", 0.5f)]` | Takes string names of other fields/properties for dynamic Min/Max limits, plus an optional step value. |
| `[MultiLine]`       | Increases the vertical height of a string field for multi-line text editing. | `[MultiLine(5)]`                                          | Takes the minimum number of lines to display.                                                          |
---
IV. DATA MANAGEMENT & UTILITIES

Attributes to manage complex data structures (lists, arrays) and add functionality (buttons, dropdowns).
| **Attribute**          | **Purpose**                                                                        | **Code Example**                                                                    | **Notes**                                                                     |
| ---------------------- | ---------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `[TableList]`          | Renders a list of complex objects (structs/classes) as a sortable, editable table. | `[TableList(Reorderable = true, Sortable = true)]`                                  | Excellent for managing data collections like inventory items or weapon stats. |
| `[ListDrawerSettings]` | Customizes the appearance and functionality of the built-in List<T> drawer.        | `[ListDrawerSettings(draggable: true, displayRemove: true)]`                        | Allows fine control over standard lists/arrays.                               |
| `[ShowMultiDimArray]`  | Enables proper drawing of multi-dimensional arrays (e.g., int[,]).                 | `[ShowMultiDimArray("Damage Matrix")]`                                              | Takes a header string for the matrix display.                                 |
| `[ValueDropdown]`      | Populates a dropdown menu using a list generated by a method or field.             | `[ValueDropdown("GetSpellNames")]`                                                  | The string must match a method or field that returns IEnumerable<T>.          |
| `[Button]`             | Converts a method into a clickable button in the Inspector.                        | `[Button("Reset Config", InspectorColor.Red)]` `private void ResetConfig() { ... }` | Can be used on private methods and styled with color.                         |
| `[EnumToggleButtons]`  | Displays an enumeration as a horizontal row of buttons instead of a dropdown.      | `[EnumToggleButtons]`                                                               | Great for clearly visible state management.                                   |
