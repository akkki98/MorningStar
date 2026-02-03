# MCP Servers Lab – GitHub, Jira & Azure DevOps

## Lab Title

**Testing GitHub, Jira, and Azure DevOps MCP Servers using GitHub Copilot Chat**

## Target Audience

Developers, QA/SDETs, DevOps Engineers, Platform & Tooling Teams



## Prerequisites

* VS Code with **GitHub Copilot Chat** enabled
* MCP-compatible setup (local or remote MCP servers configured)
* Access to:

  * GitHub repository
  * Jira project
  * Azure DevOps organization & project
* Read-only access is sufficient for most prompts

---

## Learning Objectives

By the end of this lab, participants will be able to:

* Understand the role of **MCP (Model Context Protocol) servers**
* Interact with GitHub, Jira, and Azure DevOps via Copilot Chat
* Validate MCP server connectivity and permissions
* Use structured prompts to extract insights and automate workflows
* Compare outputs across DevOps platforms

---

## What Is an MCP Server?

MCP (Model Context Protocol) servers expose **enterprise tools and data sources** (GitHub, Jira, Azure DevOps, Wikis, etc.) to AI assistants like GitHub Copilot in a **controlled and auditable manner**.

Copilot Chat can:

* Query live project data
* Summarize work items, PRs, issues
* Generate insights and automation steps

---

# LAB 1: MCP Connectivity Validation

## Objective

Ensure Copilot can access each MCP server.

### Prompt – Connectivity Check

```
List all MCP servers currently available to you and their capabilities
```

### Expected Outcome

* GitHub MCP
* Jira MCP
* Azure DevOps MCP
* Supported operations listed

---

# LAB 2: GitHub MCP Server – Hands-on Prompts

## Use Case Categories

* Repository insights
* Pull Requests
* Issues
* Code & activity analysis

---

## GitHub MCP – Basic Prompts

```
List all repositories I have access to
```

```
Show recent activity for the repository <repo-name>
```

```
List open pull requests in <repo-name>
```

```
List open issues with labels and assignees in <repo-name>
```

---

## GitHub MCP – PR & Code Review Prompts

```
Summarize the changes in PR #<id> and identify risk areas
```

```
Check if PR #<id> violates repository coding standards
```

```
List PRs pending review for more than 3 days
```

---

## GitHub MCP – Automation-Oriented Prompts

```
Identify repositories with no commits in the last 60 days
```

```
List issues that are open but have no recent comments
```

```
Suggest CI improvements based on recent PR failures
```

---

# LAB 3: Jira MCP Server – Hands-on Prompts

## Use Case Categories

* Project tracking
* Sprint insights
* Defect analysis
* Workflow bottlenecks

---

## Jira MCP – Basic Prompts

```
List all Jira projects I have access to
```

```
Show all open issues in project <PROJECT_KEY>
```

```
List issues assigned to me and their current status
```

---

## Jira MCP – Sprint & Planning Prompts

```
Show active sprint details for project <PROJECT_KEY>
```

```
List stories not started in the current sprint
```

```
Identify stories likely to spill over based on past velocity
```

---

## Jira MCP – Defect & Quality Prompts

```
List high-priority bugs open for more than 14 days
```

```
Analyze defect trends for the last 3 sprints
```

```
Identify components with the highest defect density
```

---

## Jira MCP – Workflow Analysis Prompts

```
Identify issues stuck in "In Progress" for more than 5 days
```

```
Analyze workflow bottlenecks for project <PROJECT_KEY>
```

```
Suggest process improvements based on issue transition times
```

---

# LAB 4: Azure DevOps MCP Server – Hands-on Prompts

## Use Case Categories

* Boards & work items
* Repos & PRs
* Pipelines
* Test Plans

---

## Azure DevOps MCP – Basic Prompts

```
List all Azure DevOps projects I have access to
```

```
Show active work items in project <PROJECT_NAME>
```

```
List work items assigned to me
```

---

## Azure DevOps MCP – Boards & Planning Prompts

```
Show current sprint backlog for team <TEAM_NAME>
```

```
List user stories not yet started in current sprint
```

```
Identify blocked work items and their dependencies
```

---

## Azure DevOps MCP – Repo & PR Prompts

```
List open pull requests in Azure Repos for project <PROJECT_NAME>
```

```
Summarize PR #<id> and highlight potential risks
```

```
Identify PRs waiting for approval for more than 2 days
```

---

## Azure DevOps MCP – Pipeline & Quality Prompts

```
List recent pipeline failures and their root causes
```

```
Analyze pipeline flakiness over the last 10 runs
```

```
Suggest optimizations to reduce pipeline execution time
```

---

## Azure DevOps MCP – Testing Prompts

```
List failed test cases from the last test run
```

```
Identify test cases with highest failure rate
```

```
Suggest areas where test automation coverage is missing
```

---

# LAB 5: Cross-Tool MCP Prompts (Advanced)

## Objective

Use Copilot to correlate data across tools.

```
Correlate Jira stories in sprint <SPRINT_NAME> with GitHub pull requests
```

```
Map Azure DevOps work items to GitHub PRs and deployment pipelines
```

```
Identify Jira bugs linked to recent production deployments
```

---



# Lab Completion Checklist

* [ ] MCP servers detected
* [ ] GitHub MCP prompts executed
* [ ] Jira MCP prompts executed
* [ ] Azure DevOps MCP prompts executed


---

## Key Takeaways

* MCP servers turn Copilot into an **enterprise-aware assistant**
* One chat interface, multiple DevOps tools
* Enables insights, not just code generation
* Foundation for AI-driven DevOps automation

---

**End of Lab**
