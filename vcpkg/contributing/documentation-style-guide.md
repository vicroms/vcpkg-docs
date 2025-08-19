---
title: vcpkg Documentation Style Guide
description: Writing style guidelines for vcpkg documentation contributors and AI assistants.
author: vicroms
ms.author: viromer
ms.date: 08/19/2025
ms.topic: concept-article
---

# Documentation Style Guide

This guide establishes consistent writing standards for vcpkg documentation. These guidelines ensure
clarity, accessibility, and maintainability across all documentation, whether written by human
contributors or AI assistants.

## Writing Principles

### Voice and Tone

- **Authoritative but approachable**: Be confident and knowledgeable while remaining accessible
- **Concise and direct**: Favor clarity over cleverness
- **User-focused**: Write from the user's perspective and address their needs
- **Consistent**: Maintain uniformity in terminology and style across all documentation

### Language Standards

- Use American English spelling and conventions
- Write in active voice when possible
- Use present tense for current functionality
- Use second person ("you") to address the reader
- Avoid jargon without explanation

## Content Structure

### Document Organization

1. **Front matter**: Always include proper YAML metadata
2. **Title and description**: Clear, descriptive H1 heading
3. **Introduction**: Brief overview of the topic (1-2 paragraphs)
4. **Main content**: Logically organized sections with clear headings
5. **Examples**: Practical, working code samples
6. **Related links**: Cross-references to relevant documentation

### Headings

- Use sentence case for all headings
- Follow hierarchical structure (H1 → H2 → H3)
- Make headings descriptive and scannable
- Avoid skipping heading levels

### Code Examples

- Provide complete, working examples
- Include necessary context and setup
- Use appropriate syntax highlighting
- Test all code samples before publication
- Prefer PowerShell for Windows commands (repository uses `pwsh.exe`)

## Technical Writing Standards

### Terminology

- **vcpkg**: Always lowercase, never "Vcpkg" or "VCPKG" in prose
- **CMake**: Always this capitalization
- **Visual Studio**: Full name on first reference, "VS" acceptable in subsequent references
- **port**: Lowercase when referring to vcpkg ports
- **package**: Use consistently with "port" - prefer "port" for vcpkg-specific contexts

### Command Line Examples

```powershell
# Use PowerShell syntax for Windows examples
vcpkg install boost

# Use appropriate shell for cross-platform examples
./vcpkg install boost
```

### File Paths

- Use forward slashes in documentation examples
- Use `${VCPKG_ROOT}` for vcpkg installation directory references
- Use absolute paths in configuration examples

## Formatting Guidelines

### Links

- Use descriptive link text (not "click here" or "here")
- Link to official documentation when referencing external tools
- Use relative links for internal documentation
- Verify all links are functional

### Lists

- Use parallel structure in list items
- Start each item with a capital letter
- Use periods only if items are complete sentences
- Prefer numbered lists for sequential steps
- Use bullet points for non-sequential items

### Code Formatting

- Use `inline code` for:
  - Commands and command-line options
  - File names and paths
  - API names and function names
  - Configuration values
- Use code blocks for:
  - Multi-line examples
  - Configuration files
  - Scripts

### Tables

- Include header rows
- Keep content concise
- Align content appropriately
- Use tables sparingly - prefer lists when possible

## Microsoft Documentation Standards

### Accessibility

- Use alt text for images
- Ensure sufficient color contrast
- Write descriptive link text
- Structure content with proper headings

### Inclusive Language

- Use gender-neutral language
- Avoid ableist language
- Choose inclusive technical terms
- Follow Microsoft's inclusive language guidelines

## Content-Specific Guidelines

### Tutorials and Guides

- Start with prerequisites
- Provide step-by-step instructions
- Include expected outcomes
- Test all procedures thoroughly

### Reference Documentation

- Be comprehensive and accurate
- Use consistent parameter descriptions
- Include all required and optional parameters
- Provide examples for complex parameters

### Troubleshooting Content

- Lead with the most common solutions
- Provide specific error messages when possible
- Include diagnostic steps
- Link to related troubleshooting resources

## AI Assistant Guidelines

When AI assistants (like GitHub Copilot) contribute to vcpkg documentation:

1. **Follow these style guidelines** exactly
2. **Verify technical accuracy** - test all code examples
3. **Maintain consistency** with existing documentation
4. **Use appropriate metadata** in YAML front matter
5. **Cross-reference** related documentation appropriately
6. **Consider the user journey** and skill level

## Quality Checklist

Before publishing documentation:

- [ ] Follows the voice and tone guidelines
- [ ] Uses consistent terminology
- [ ] Includes proper metadata
- [ ] Has clear, descriptive headings
- [ ] Contains working code examples
- [ ] Links are functional and descriptive
- [ ] Grammar and spelling are correct
- [ ] Content is accessible and inclusive
- [ ] Follows Microsoft documentation standards

## Resources

- [Microsoft Writing Style Guide](/style-guide/welcome)
- [vcpkg Maintainer Guide](./maintainer-guide.md)
- [vcpkg CMake Style Guide](./cmake-guidelines.md)
