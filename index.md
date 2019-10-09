---
layout: default
---

## The Media-Cloud-AI project

Media-Cloud-AI intend to build an open-source platform to process media content with some Artificial Inteligence processes.
It provide also some generic tools to manipulate media.

### Architecture

The platform is splitted into micro-services, each one provide a specific function.

<div class="mermaid">
graph LR
ui[fa:fa-user User interface] --> backend(Backend)
backend[fa:fa-cogs Backend] --> rmq(fa:fa-bars Message broker)
backend --> DB(fa:fa-database Database)
rmq --> W1[fa:fa-cog Worker 1]
rmq --> W2[fa:fa-cog Worker 2]
rmq --> W3[fa:fa-cog Worker 3]

classDef blue fill:#155799,stroke: none,color: #fff;
classDef green fill:#159957,stroke: none,color: #fff;

class ui green
class backend blue
class rmq blue
class DB blue
class W1 green
class W2 green
class W3 green
</div>

### Backend and User interface

The core component is the backend, which provide user managment, workflow engine and monitoring.

### Available workers in Open-Source

- Transfer: across S3, FTP, HTTP, local storages
- File System: list, remove, copy files
- Manifest: DASH and ISM manifest manipulations
- Command line: to execute any command line available
- FFmpeg: to manipulate any video and audio formats
- Loudness: measure loudness on audio content
- ADM Engine: manipulate Audio Oriented objets

### Deployment

The entire project is currently deployed using [Kubernetes](https://kubernetes.io){:target="_blank"}.  
Every part of the platform is builded into Docker images and can be deployed easilly with the [startup](https://github.com/media-cloud-ai/startup){:target="_blank"} project.  

### Developement stack

The frontend is designed using [Angular.io](https://angular.io){:target="_blank"}  
![Angular.io](/assets/images/angular-icon.svg)

The backend use the power of [Elixir](https://elixir-lang.org/){:target="_blank"}, based on [ERLang](https://www.erlang.org/){:target="_blank"} to provide a resilient and efficient backend.
![Elixir](/assets/images/elixir.png)

Most of workers are using [Rust](https://www.rust-lang.org/){:target="_blank"}, high-typed language and with performances similar to C/C++ applications.
Using FFI (Foreign Function Interface), it allows to call any library which provide a C API.
![Rust](/assets/images/rust.svg)
