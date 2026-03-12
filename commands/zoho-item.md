---
description: "Displays details of a Zoho Projects item. Usage: /zoho-item <project_id> <item_id> <type: task|issue|bug>"
agent: zoho
subtask: true
---

Retrieves and displays the full details of item ID $2 in project ID $1.
The item type is: **$3** (accepted values: `task`, `issue`, `bug`).

- If type is `task`: use the task retrieval tool.
- If type is `issue`: use the issue retrieval tool.
- If type is `bug`: use the bug retrieval tool.

Do not implement, just display.
Once the data is retrieved, output ONLY the following report — nothing else:

---

# [#<id>] <title>

| Champ          | Valeur                            |
|----------------|-----------------------------------|
| **Type**       | $3                                |
| **Statut**     | <status>                          |
| **Priorité**   | <priority, or "None">             |
| **Assigné**    | <assignee name, or "Unassigned">  |

**Description**

> <description, or "*No description provided.*">
