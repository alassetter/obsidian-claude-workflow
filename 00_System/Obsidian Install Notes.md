# Obsidian MCP – Recovery Notes

This vault is connected to Claude via obsidian-mcp-server.

Normal operation:
- Nothing to start manually
- launchd runs the MCP automatically
- Claude connects on launch

If it breaks:

1. Verify Obsidian REST API
   - Obsidian → Settings → Local REST API
   - Plugin enabled
   - API key exists

2. Test REST API
   curl -H "Authorization: Bearer <key>" http://127.0.0.1:27123/
   Expect: "authenticated": true

3. Restart MCP service
   launchctl unload ~/Library/LaunchAgents/obsidian.mcp.plist
   launchctl load ~/Library/LaunchAgents/obsidian.mcp.plist

4. Reset Claude MCP cache (only if needed)
   pkill -f Claude
   rm -rf ~/Library/Application\ Support/Claude/mcp
   open -a Claude

Logs:
- /tmp/obsidian-mcp.log
- /tmp/obsidian-mcp.err


• Must use obsidian-mcp-server binary
• OBSIDIAN_API_KEY must be in Claude env
• Claude does not load .env files
• Node 20.x is required