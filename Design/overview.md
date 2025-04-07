## Specification Document

### Project Overview
TG 263 Validator is a single-page Blazor WebAssembly application designed to validate structure labels according to TG 263 standards.

### Purpose
The tool allows users to input potential structure labels and receive immediate validation feedback based on the Tg263.Toolkit library rules.

### Technical Specifications
- **Framework**: Blazor WebAssembly
- **Validation Engine**: TG263.Toolkit C# library
- **UI Design**: See `Design/wireframe.png` for visual reference

### Functional Requirements
1. **Input Field**: Single text box for structure label entry
2. **Validation Display**:
    - Green checkmark for valid structure labels
    - Error message display for invalid inputs
3. **Metadata Display**: Key-value pair listing of structure components when valid
    - Note: These pairs are dynamic and vary based on the input string

### Integration Example
```csharp
var targetId = "PTV1_A_Aorta";
var parseResult = StructureParser.Parse(targetId);
Console.WriteLine($"IsValid: {parseResult.IsValid}");
if (!parseResult.IsValid)
{
     Console.WriteLine($"Validation Message: {parseResult.ValidationMessage}");
}
else
{
     foreach (var part in parseResult.StructureParts)
     {
          Console.WriteLine($"{part.Key}: {part.Value}");
     }
}
```

### Implementation Notes
- Validation occurs in real-time as the user types
- The application must handle various validation scenarios gracefully
- The UI should be clean and intuitive, following the wireframe design