---
type: client
client: <% tp.file.title %>
status: active
industry:
primary_contact:
tech_stack: []
ai_instructions: >
  Default to professional, concise communication.
  Ask before making assumptions.
---

# <% tp.file.title %> — Client Overview

## Summary
Brief description of the client and engagement.

## Key Stakeholders
- Name — Role — Contact

## Active Projects
```dataview
LIST FROM "01_Clients/<% tp.file.title %>/Projects"
