---
layout: default
---

### Architecture

The platform is split into micro-services, each one providing specific function.

{% include mermaid_schemas/main_architecture.html %}

### Backend and User interface

The core component is the backend, which provides user management, workflow engine and monitoring.

### Workflows

The backend manage workflows structured like that:
- **Workflow**: a description including a list of steps
  - **Step**: static declaration of a process
    - **Job**: instance of a step, many jobs can be generated at the runtime for 1 step (1 per file for example)

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


Complete workflow documentation of the schema is described [here](/workflow-definition).

### Messaging protocol

A communication standard is required to match messages between backend and workers.
To ensure the quality of integration, it's recommended to use everywhere [rs_amqp_worker](https://github.com/media-cloud-ai/rs_amqp_worker/) which provide a worker SDK.

All details about communication between the backend and workers is detailed [here](/messaging_protocol.html).

### Deployment

The entire project is currently deployed using [Kubernetes](https://kubernetes.io){:target="_blank"}.  
Every part of the platform is built into Docker images and can be deployed easily with the [startup](https://github.com/media-cloud-ai/startup){:target="_blank"} project.  

### Developement stack

#### User interface

The frontend is designed using [Angular.io](https://angular.io){:target="_blank"}  
{:refdef: class="language"}
![Angular](/assets/images/angular-icon.svg)
{: refdef}

#### Backend
The backend uses the power of [Elixir](https://elixir-lang.org/){:target="_blank"}, based on [Erlang](https://www.erlang.org/){:target="_blank"} to provide a resilient and efficient backend.
{:refdef: class="language"}
![Elixir](/assets/images/elixir.png)
{: refdef}

#### Workers
Most of workers are using [Rust](https://www.rust-lang.org/){:target="_blank"}, high-typed language with performances similar to C/C++ applications.
{:refdef: class="language"}
![Rust](/assets/images/rust.svg)
{: refdef}

Some other workers can use C/C++ using the [c_amqp_worker](https://github.com/media-cloud-ai/c_amqp_worker) project