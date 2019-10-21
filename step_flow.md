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

### Send Job order to Worker(s)

<div class="mermaid">
graph LR
backend(fa:fa-cogs Backend) --> |Send message| exchange_1[fa:fa-exchange-alt Exchange]

subgraph rmq[Rabbit MQ]
  exchange_1-->|job type 1| q_worker_1[fa:fa-list-ul Queue Job Type 1]
  exchange_1 -->|job type 2| q_worker_2[fa:fa-list-ul Queue Job Type 2]
  exchange_1 -->|job type n| q_worker_n[fa:fa-list-ul Queue Job Type N]
end

q_worker_1 --- w1(fa:fa-cog Worker 1)
q_worker_2 --- w2(fa:fa-cog Worker 2)
q_worker_2 --- w3(fa:fa-cog Worker 3)
q_worker_n --- wn(fa:fa-cog Worker n)

classDef blue fill:#155799,stroke: none,color: #fff;
classDef green fill:#159957,stroke: none,color: #fff;

class backend green
class backend2 green
class backend3 green
class w1 green
class w2 green
class w3 green
class wn green
class q_worker_1 blue
class q_worker_2 blue
class q_worker_n blue
class q_completed blue
class q_error blue
class exchange_1 blue
class exchange_2 blue

style rmq fill:#15579930,stroke:#155799,stroke-width:2px,color:#155799
</div>

### Return Job status from Worker(s) to the Backend

<div class="mermaid">
graph LR

w1(fa:fa-cog Worker 1) --> exchange_2[fa:fa-exchange-alt Exchange]
w2(fa:fa-cog Worker 2) --> exchange_2
w3(fa:fa-cog Worker 3) --> exchange_2
wn(fa:fa-cog Worker n) --> exchange_2

subgraph rmq[Rabbit MQ]
  exchange_2 --> |completed| q_completed[fa:fa-list-ul Queue Completed]
  exchange_2 --> |error| q_error[fa:fa-list-ul  Queue Error]
end

q_completed --> |Consume queue Job Completed|backend2(fa:fa-cogs Backend)
q_error --> |Consume queue Job Error|backend2

classDef blue fill:#155799,stroke: none,color: #fff;
classDef green fill:#159957,stroke: none,color: #fff;

class backend green
class backend2 green
class backend3 green
class w1 green
class w2 green
class w3 green
class wn green
class q_worker_1 blue
class q_worker_2 blue
class q_worker_n blue
class q_completed blue
class q_error blue
class exchange_1 blue
class exchange_2 blue

style rmq fill:#15579930,stroke:#155799,stroke-width:2px,color:#155799
</div>

<style type="text/css">
	.edgeLabel {
		background-color: #ffff !important;
	}
</style>
