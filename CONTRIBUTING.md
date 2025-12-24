# Contributing to CNC Shield for UnoMZ

Thank you for your interest in contributing to the CNC Shield project! We welcome contributions from the community.

## How to Contribute

### Reporting Issues

If you find a bug or have a suggestion:

1. Check if the issue already exists in the [Issues](https://github.com/Davec6505/CNC-Shield-UnoMZ/issues) section
2. If not, create a new issue with:
   - Clear, descriptive title
   - Detailed description of the problem or suggestion
   - Steps to reproduce (for bugs)
   - Expected vs actual behavior
   - Hardware/software versions used
   - Photos or screenshots if applicable

### Suggesting Enhancements

We welcome ideas for improvements:

- New features
- Design improvements
- Documentation enhancements
- Better component choices
- Cost optimizations
- Performance improvements

Please open an issue to discuss major changes before starting work.

## Development Process

### Setting Up Development Environment

1. **Fork the repository** on GitHub
2. **Clone your fork** locally:
   ```bash
   git clone https://github.com/YOUR_USERNAME/CNC-Shield-UnoMZ.git
   cd CNC-Shield-UnoMZ
   ```
3. **Install KiCad** (latest version recommended):
   - Download from https://www.kicad.org/download/
   - Install according to your platform

4. **Create a branch** for your work:
   ```bash
   git checkout -b feature/your-feature-name
   ```

### Making Changes

#### Hardware Design Changes

1. Open the KiCad project files in `hardware/kicad/`
2. Make your changes to schematic or PCB layout
3. Run Design Rule Check (DRC) to verify design
4. Update documentation if needed
5. Export updated Gerber files if applicable
6. Commit your changes with clear messages

#### Documentation Changes

1. Edit relevant markdown files in `docs/` or root directory
2. Ensure formatting is consistent
3. Check links and references
4. Update table of contents if needed
5. Preview changes before committing

#### BOM Changes

1. Update `hardware/bom/BOM.md`
2. Verify part numbers and specifications
3. Update pricing if significant changes
4. Check availability of components

### Commit Guidelines

Write clear, descriptive commit messages:

```
Good:
- "Add heatsink recommendations to BOM"
- "Fix pin mapping error in pinout documentation"
- "Improve PCB trace routing for X-axis driver"

Bad:
- "Update"
- "Fix stuff"
- "Changes"
```

Use conventional commit format when possible:
```
feat: Add support for TMC2209 drivers
fix: Correct X-axis pin assignment
docs: Update assembly guide with photos
chore: Update .gitignore for KiCad backup files
```

### Pull Request Process

1. **Update your fork** with latest main branch:
   ```bash
   git fetch upstream
   git rebase upstream/main
   ```

2. **Push your changes** to your fork:
   ```bash
   git push origin feature/your-feature-name
   ```

3. **Create a Pull Request** on GitHub:
   - Use a clear, descriptive title
   - Describe what changes you made and why
   - Reference any related issues
   - Include photos/screenshots if applicable
   - List any breaking changes

4. **Wait for review**:
   - Maintainers will review your PR
   - Address any feedback or requested changes
   - Update your PR as needed

5. **Merge**:
   - Once approved, your PR will be merged
   - Delete your branch after merge

## Coding Standards

### KiCad Design Standards

- Use consistent component naming (U1, U2, C1, C2, etc.)
- Label all components clearly on silkscreen
- Maintain minimum clearances:
  - 0.2mm track spacing
  - 0.3mm minimum hole size
  - 0.5mm board edge clearance
- Use standard footprints when available
- Add mounting holes at Arduino standard positions

### Documentation Standards

- Use Markdown format
- Follow existing structure and style
- Include code blocks for examples
- Add tables for specifications
- Use proper heading hierarchy
- Check spelling and grammar
- Include safety warnings where appropriate

### File Organization

```
CNC-Shield-UnoMZ/
├── hardware/
│   ├── kicad/          # KiCad project files
│   ├── gerber/         # Manufacturing files
│   └── bom/            # Bill of materials
├── docs/
│   ├── images/         # Schematics and photos
│   ├── assembly-guide.md
│   └── pinout.md
├── firmware/           # Example configurations
├── README.md
├── LICENSE
└── CONTRIBUTING.md
```

## Testing

Before submitting:

### Hardware Changes
- [ ] Run DRC in KiCad with no errors
- [ ] Verify 3D model looks correct
- [ ] Check all connections in schematic
- [ ] Verify component footprints
- [ ] Generate and check Gerber files
- [ ] Update version numbers if needed

### Documentation Changes
- [ ] Check all links work
- [ ] Verify formatting renders correctly
- [ ] Ensure consistency with existing docs
- [ ] Spell check
- [ ] Preview in GitHub markdown renderer

### BOM Changes
- [ ] Verify all part numbers
- [ ] Check component availability
- [ ] Update quantities correctly
- [ ] Verify specifications match design

## Code of Conduct

### Our Standards

- Be respectful and inclusive
- Welcome newcomers
- Accept constructive criticism
- Focus on what's best for the project
- Show empathy towards others

### Unacceptable Behavior

- Harassment or discrimination
- Trolling or insulting comments
- Personal or political attacks
- Publishing private information
- Other unprofessional conduct

### Enforcement

Violations may result in:
1. Warning
2. Temporary ban
3. Permanent ban

Report issues to project maintainers.

## Questions?

- Open an issue for questions about the project
- Check existing documentation first
- Search closed issues for similar questions
- Be patient waiting for responses

## Recognition

Contributors will be recognized in:
- Commit history
- Release notes
- Contributors list (if implemented)

## License

By contributing, you agree that your contributions will be licensed under the MIT License.

## Additional Resources

- [KiCad Documentation](https://docs.kicad.org/)
- [GRBL Wiki](https://github.com/gnea/grbl/wiki)
- [Markdown Guide](https://www.markdownguide.org/)
- [GitHub Flow](https://guides.github.com/introduction/flow/)

## Version History

Track major contributions in release notes and changelog.

## Thank You!

Your contributions make this project better for everyone. Thank you for taking the time to contribute!

---

**Note**: This is an open-source hardware project. All contributions should respect the open-source nature and MIT License of the project.
