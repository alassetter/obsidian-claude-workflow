
---
type: prompt
category: <% tp.system.prompt("Category (analysis | business | coding | writing | meta)") %>
audience: <% tp.system.prompt("Audience (client | internal | ai)") %>
reuse: high
created: <% tp.date.now("YYYY-MM-DD") %>
---
# <% tp.file.title %>

## Prompt
