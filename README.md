# Aurora SAIL Starter Template

A Kiro IDE template for building Appian SAIL interfaces with Aurora Design System and AI-powered code generation.

## Quick Start

### 1. Use This Template

Click "Use this template" on GitHub or clone this repository.

### 2. Run Setup Power

Open this workspace in Kiro IDE and activate the **Aurora Setup Power**:

```
Set up Aurora MCP for me
```

The Power will automatically:
- Check Node.js installation
- Clone and build Aurora MCP server
- Create `.env` file with the installation path
- Configure Kiro settings
- Validate the connection

### 3. Start Building

Once setup is complete, describe what you need:

```
Create a dashboard with KPI cards showing application metrics
```

That's it! The Aurora Design System and SAIL syntax guidance are automatically available.

## Manual Setup (Optional)

If you prefer to set up manually:

1. **Install Aurora MCP** - Clone and build from [aurora-mcp](https://github.com/appian-design/aurora-mcp)
2. **Create .env file** - Copy `.env.example` to `.env` and set `AURORA_MCP_PATH`
3. **Restart Kiro** - Reload the workspace to pick up the environment variable

## What's Included

### Automatic SAIL Guidance
- **SAIL Syntax Reference** - Always loaded for correct syntax patterns
- **Aurora Design System** - Layouts, patterns, and components via MCP
- **SAIL Coding Guide** - Best practices and error prevention
- **Validation Hook** - Automatic SAIL syntax checking on save

### Aurora Setup Power
Handles the complete setup process automatically:
- Prerequisites checking
- Aurora MCP installation
- Build and configuration
- Connection validation

### Pre-configured Settings
- MCP server configuration
- Auto-approved design system tools
- SAIL validation hook
- Steering files for consistent generation

## Example Usage

**Dashboard:**
```
Create an award cycle time dashboard with:
- Line chart showing monthly trends
- KPI cards for key metrics
- Donut chart for phase breakdown
- Filterable data grid
- Performance insights sidebar
```

**Form:**
```
Create a multi-step customer onboarding form with:
- Personal information section
- Address fields with validation
- Document upload
- Review and submit step
```

**Work Queue:**
```
Create a work queue with status tags and action buttons
```

See the `examples/` directory for a complete dashboard example with detailed generation prompts.

## How It Works

When you describe an interface:

1. **SAIL Syntax Reference** provides correct syntax patterns (always loaded)
2. **Aurora MCP** supplies design system components and layouts
3. **SAIL Coding Guide** prevents common errors
4. **Validation Hook** checks syntax when you save

Result: Professional, syntactically correct SAIL code.

## Template Structure

```
aurora-starter/
├── .env.example                        # Environment variable template
├── .gitignore                          # Git ignore rules
├── .kiro/
│   ├── hooks/
│   │   └── sail-validator.kiro.hook    # Auto-validates SAIL on save
│   ├── powers/
│   │   └── aurora-setup/               # Setup automation
│   ├── settings/
│   │   └── mcp.json                    # MCP configuration (uses $AURORA_MCP_PATH)
│   └── steering/
│       ├── SAIL_INTERFACE_GENERATION.md  # Generation guidelines
│       └── SAIL_SYNTAX_REFERENCE.md      # Syntax patterns
├── examples/
│   └── README.md                       # Example interfaces
├── CONTRIBUTING.md                     # Contribution guide
└── README.md                           # This file
```

## Customization

### Add Team Patterns

Edit `.kiro/steering/SAIL_SYNTAX_REFERENCE.md`:
```sail
/* Your team's custom pattern */
a!myTeamPattern(
  /* parameters */
)
```

### Modify MCP Configuration

The MCP path is configured via environment variable:
- Edit `.env` to update `AURORA_MCP_PATH`
- Restart Kiro to pick up changes
- Or edit `.kiro/settings/mcp.json` directly for other settings:
  - Add additional MCP servers
  - Configure timeouts
  - Adjust auto-approvals

### Add Examples

Place example SAIL files in `examples/` directory for reference.

## Troubleshooting

### Setup Issues

**Node.js not found:**
- Install from [nodejs.org](https://nodejs.org)
- Or use package manager: `brew install node` (macOS)

**Aurora MCP build fails:**
- Check Node.js version: `node --version` (needs 16+)
- Try: `cd aurora-mcp && npm install && npm run build`

**MCP not connecting:**
- Verify `.env` file exists with correct `AURORA_MCP_PATH`
- Ensure path is absolute, not relative
- Restart Kiro after changing `.env`
- Check MCP server status in Kiro UI
- Test directly: `node $AURORA_MCP_PATH/build/index.js`

### Generation Issues

**Syntax errors:**
- Check `.kiro/steering/SAIL_SYNTAX_REFERENCE.md` for correct patterns
- Ask to validate against SAIL Coding Guide
- Use the validation hook to catch errors early

**Missing components:**
- Ask to list available categories first
- Request specific Aurora patterns
- Check Aurora Design System documentation

## Tips for Best Results

1. **Be specific** - Describe the interface type and data clearly
2. **Start simple** - Build incrementally, add complexity as needed
3. **Use validation** - Save files to trigger the validation hook
4. **Iterate** - Refine with follow-up requests
5. **Reference examples** - Check the `examples/` directory

## Learn More

- [Aurora Design System](https://github.com/appian/aurora) - Components and patterns
- [Aurora MCP Server](https://github.com/appian/aurora-mcp) - MCP server details
- [Appian Documentation](https://docs.appian.com) - SAIL language reference
- [Kiro IDE](https://kiro.dev) - IDE documentation

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on:
- Adding examples
- Improving documentation
- Sharing patterns
- Reporting issues

---

**Ready to build?** Run the Aurora Setup Power and start creating professional SAIL interfaces!
