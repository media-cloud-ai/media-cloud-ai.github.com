---
layout: default
---

## The Media-Cloud-AI project

Media-Cloud-AI intend to build an open-source platform to process media content with some Artificial Intelligence processes.  
It will also provide some generic tools to manipulate media.

### Architecture

This micro-services platform provides a fully <b>distributed processing</b> for media content accross <b>multi-cloud</b> provider (public & private).  
The <b>backend is the main orchestrator</b>, combining steps after step a complex workflow.  
Each worker is connected to the message broken to enable the <b>horizontal scalability</b>.


{% include mermaid_schemas/main_architecture.html %}

[Read more details about the architecture](/architecture.html)
