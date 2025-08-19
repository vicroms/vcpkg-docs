# AI Assistant Instructions for vcpkg Documentation

## Purpose

This document provides specific instructions for AI assistants (including GitHub Copilot agents)
when contributing to or modifying vcpkg documentation.

## Required Reading

Before making any changes to documentation, AI assistants MUST reference:

1. **[Documentation Style Guide](../vcpkg/contributing/documentation-style-guide.md)** - Primary writing style guidelines
2. **[Maintainer Guide](../vcpkg/contributing/maintainer-guide.md)** - Technical contribution standards
3. **[CMake Style Guide](../vcpkg/contributing/cmake-guidelines.md)** - CMake-specific coding standards
4. **[.markdownlint.jsonc](../.markdownlint.jsonc)** - Markdown formatting rules

## Key Style Requirements

### Voice and Tone

- **Authoritative but approachable** - Be knowledgeable while remaining accessible
- **User-focused** - Write from the user's perspective and address their needs
- **Concise and direct** - Favor clarity over complexity

### Terminology Standards

- **vcpkg** - Always lowercase in prose (never "Vcpkg" or "VCPKG")
- **CMake** - Always use this exact capitalization
- **Visual Studio** - Full name on first reference, "VS" acceptable afterward
- **port** - Lowercase when referring to vcpkg ports
- **package** - Use consistently with "port" - prefer "port" for vcpkg-specific contexts

### Technical Requirements

- Use **PowerShell syntax** for Windows command examples (repository uses `pwsh.exe`)
- Include **proper YAML front matter** with title, description, author metadata
- Provide **working, tested code examples**
- Use **relative links** for internal documentation references
- Follow **Microsoft inclusive language guidelines**

### Content Structure

1. **Front matter** - Always include proper YAML metadata
2. **Clear H1 heading** that matches the title in metadata
3. **Brief introduction** (1-2 paragraphs) explaining the topic
4. **Logical section organization** with descriptive headings
5. **Practical examples** that users can follow
6. **Cross-references** to related documentation

## Quality Checklist

Before submitting any documentation changes, verify:

- [ ] Follows the established voice and tone guidelines
- [ ] Uses consistent vcpkg terminology
- [ ] Includes proper metadata in YAML front matter
- [ ] Has clear, descriptive headings in sentence case
- [ ] Contains working code examples (tested when possible)
- [ ] Uses descriptive link text (never "click here")
- [ ] Passes markdown linting rules (see .markdownlint.jsonc)
- [ ] Grammar and spelling are correct
- [ ] Content is accessible and inclusive
- [ ] Follows Microsoft documentation standards

## Special Instructions for AI Agents

### When Updating Existing Documentation

1. **Maintain consistency** with the existing writing style and tone
2. **Preserve working links** and verify any new links are functional
3. **Keep the same metadata structure** (author, ms.author, etc.)
4. **Follow the established heading hierarchy**

### When Creating New Documentation

1. **Start with proper YAML front matter** including all required fields
2. **Use the documentation style guide as a template** for structure
3. **Include cross-references** to related existing documentation
4. **Add entry to TOC.yml** if creating a new major document

### Code Examples

- **Test all code examples** when possible before including them
- **Use appropriate syntax highlighting** (powershell, cmake, yaml, etc.)
- **Include necessary context** and setup instructions
- **Prefer complete, working examples** over code fragments

### Error Prevention

- **Never create duplicate H2 headings** within the same document
- **Always use relative paths** for internal links (./filename.md)
- **Follow markdown formatting rules** defined in .markdownlint.jsonc
- **Maintain line length limits** (120 characters for prose)

## Repository-Specific Context

### Project Information

- **Repository**: vcpkg-docs (Microsoft's vcpkg package manager documentation)
- **Audience**: Developers using vcpkg for C++ package management
- **Platform**: Microsoft Docs publishing system
- **Primary Shell**: PowerShell (pwsh.exe) on Windows

### Common Topics

- Package installation and management
- Binary and asset caching
- Custom registries and ports
- Integration with build systems (CMake, MSBuild)
- Cross-platform development scenarios

### Links to Avoid

- External links that may break over time
- Deep links into other repositories' documentation
- Links to specific version numbers that will become outdated

## Resources for AI Assistants

- [Microsoft Writing Style Guide](https://docs.microsoft.com/style-guide/)
- [Microsoft Inclusive Language Guidelines](https://docs.microsoft.com/style-guide/bias-free-communication)
- [Markdown Best Practices](https://docs.microsoft.com/contribute/markdown-reference)
