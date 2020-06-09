---
layout: default
---

## The Media-Cloud-AI project

Media-Cloud-AI is an open-source platform to process media contents with multiple Artificial Intelligence processes.  
It will also provides some generic tools to manipulate media.

### Architecture

This micro-services platform provides a fully <b>distributed processing</b> for media contents accross <b>multi-cloud</b> provider (public & private).  
The <b>backend is the main orchestrator</b>, combining step after step within potential complex workflows.  
Each worker is connected to the message broker to enable the <b>horizontal scalability</b>.


{% include mermaid_schemas/main_architecture.html %}

[Read more details about the architecture](/architecture.html)
