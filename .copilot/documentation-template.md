---
title: [Document Title - Use Title Case]
description: [Brief description of the document content and purpose]
author: [GitHub username]
ms.author: [Microsoft alias]
ms.date: [MM/DD/YYYY]
ms.topic: [concept-article | how-to-guide | tutorial | reference]
---

# [Document Title - Should Match YAML Title]

[Brief introduction paragraph explaining what this document covers and who the target audience is.
Keep this concise but informative - 1-2 paragraphs maximum.]

## [Main Section Heading - Use Sentence Case]

[Content for your main sections. Follow the established voice and tone guidelines:]

- [Use second person ("you") to address the reader]
- [Write in active voice when possible]
- [Be authoritative but approachable]
- [Focus on user needs and scenarios]

### [Subsection Heading - Use Sentence Case]

[Content for subsections. Include practical examples and code samples:]

```powershell
# Use PowerShell syntax for Windows command examples
vcpkg install [package-name]
```

```cmake
# Use appropriate syntax highlighting for code blocks
find_package([PackageName] CONFIG REQUIRED)
target_link_libraries(main PRIVATE [PackageName]::[target])
```

### [Another Subsection]

[When referencing vcpkg-specific concepts:]

- Use **vcpkg** (lowercase) for the tool name
- Use **port** for vcpkg packages
- Use **CMake** (exact capitalization)
- Use **Visual Studio** on first reference, "VS" afterward

## [Prerequisites/Requirements Section if Applicable]

[List any prerequisites, system requirements, or setup needed:]

- [Requirement 1]
- [Requirement 2]
- [Requirement 3]

## [Step-by-Step Instructions if Applicable]

[For how-to guides and tutorials, provide clear step-by-step instructions:]

1. **[Action 1]**: [Detailed description of what to do]

   ```powershell
   # Example command
   vcpkg install boost
   ```

2. **[Action 2]**: [Next step with explanation]

3. **[Action 3]**: [Continue with logical progression]

## [Troubleshooting Section if Applicable]

[Common issues and solutions:]

### [Common Issue 1]

[Description of the problem and solution]

### [Common Issue 2]

[Description of the problem and solution]

## [Next Steps/Related Information]

[Provide logical next steps or related information:]

- [Link to related documentation using descriptive text](./related-file.md)
- [Another helpful resource](./another-file.md)

## [See Also]

[Cross-references to related documentation:]

- [vcpkg Maintainer Guide](./maintainer-guide.md)
- [CMake Style Guide](./cmake-guidelines.md)
- [Related concept or process](./related-concept.md)
