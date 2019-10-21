---
layout: default
---

## Step Flow

The library manage all workflow, a chain of steps which can have many related jobs.

### Workflow/Step/Job relation

<div class="mermaid">
graph LR
wf[fa:fa-list-ul Workflow] --> |0..*| step[Step] 
step -->  |0..*| job[fa:fa-cogs Job]

classDef blue fill:#155799,stroke: none,color: #fff;
classDef green fill:#159957,stroke: none,color: #fff;

class wf green
class step green
class job blue
</div>
