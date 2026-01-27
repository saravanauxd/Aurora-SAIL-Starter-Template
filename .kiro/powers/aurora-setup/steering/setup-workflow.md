# Aurora MCP Setup Workflow

This workflow guides the automated setup of Aurora MCP for less technical users.

## Setup Steps

### 1. Check Node.js Installation

```bash
node --version
```

**If not installed:**
- Provide clear instructions for their OS
- macOS: `brew install node` or download from nodejs.org
- Windows: Download installer from nodejs.org
- Linux: Use package manager (apt, yum, etc.)

### 2. Determine Installation Location

Ask user where they want to install Aurora MCP, or suggest:
- macOS/Linux: `~/Documents/GitHub/aurora-mcp`
- Windows: `C:\Users\[username]\Documents\GitHub\aurora-mcp`

Store this path for later use.

### 3. Clone Aurora MCP Repository

```bash
git clone https://github.com/appian/aurora-mcp.git [installation-path]
```

**If git not installed:**
- Provide download link: https://github.com/appian/aurora-mcp/archive/refs/heads/main.zip
- Guide user to extract to chosen location

### 4. Install Dependencies

```bash
cd [installation-path]
npm install
```

Monitor output for errors. Common issues:
- Network problems: Suggest retry
- Permission errors: Suggest using sudo (macOS/Linux) or running as admin (Windows)

### 5. Build the Server

```bash
npm run build
```

Verify `build/index.js` exists after completion.

### 6. Update Kiro Configuration

Create `.env` file with the Aurora MCP path:

```bash
echo "AURORA_MCP_PATH=[installation-path]" > .env
```

The `.kiro/settings/mcp.json` file is already configured to use `${AURORA_MCP_PATH}` environment variable:

```json
{
  "mcpServers": {
    "design-system": {
      "command": "node",
      "args": [
        "${AURORA_MCP_PATH}/build/index.js"
      ],
      ...
    }
  }
}
```

**Important:** 
- Use absolute path in `.env`, not relative
- The `.env` file is gitignored for security
- Restart Kiro after creating `.env` to load the variable

### 7. Test the Connection

Try listing design system categories to verify the connection works:
```
List available Aurora design system categories
```

If successful, setup is complete!

## Error Handling

### Node.js Not Found
- Provide installation instructions
- Wait for user to install
- Retry check

### Git Clone Fails
- Check internet connection
- Verify GitHub is accessible
- Offer manual download option

### npm install Fails
- Check error message
- Common fixes:
  - Clear npm cache: `npm cache clean --force`
  - Delete node_modules and retry
  - Check npm registry access

### Build Fails
- Check Node.js version (needs 16+)
- Review build errors
- Suggest checking Aurora MCP repository issues

### MCP Connection Fails
- Verify `.env` file exists in workspace root
- Check `AURORA_MCP_PATH` is set correctly in `.env`
- Ensure path is absolute, not relative
- Verify build/index.js exists at that path
- Restart Kiro to reload environment variables
- Test running server directly: `node $AURORA_MCP_PATH/build/index.js`
- Check Kiro MCP server status in UI

## Success Criteria

Setup is successful when:
1. ✅ Node.js is installed and accessible
2. ✅ Aurora MCP is cloned/downloaded
3. ✅ Dependencies are installed
4. ✅ Server is built (build/index.js exists)
5. ✅ `.env` file is created with `AURORA_MCP_PATH`
6. ✅ Kiro is restarted to load environment variable
7. ✅ MCP server responds to test query

## Post-Setup Message

Once complete, inform the user:

"✅ Aurora MCP is set up and ready! 

**Important:** Please restart Kiro to load the environment variable, then you can start generating SAIL interfaces.

After restart, try asking:
- 'Create a dashboard with KPI cards'
- 'Generate a form for customer data entry'
- 'Build a work queue interface'

The Aurora Design System and SAIL syntax guidance will be available to help you build professional Appian interfaces."
