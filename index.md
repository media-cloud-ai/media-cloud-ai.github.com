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
- Loudness: loudness measurements of audio content ([ITU-R BS.1770-4](https://www.itu.int/rec/R-REC-BS.1770/recommendation.asp?lang=fr&parent=R-REC-BS.1770-4-201510-I){:target="_blank"})
- ADM Engine: renderer for Object-Based Audio ([ITU-R BS.2076-1](https://www.itu.int/rec/R-REC-BS.2076-1-201706-I/fr){:target="_blank"})

### Available workers under license

#### Co-property of Telecom SudParis & France Televisions:
- Automatic Content Synchronisation: Synchronise asynchronous transcripted subtitles with the related audio (actually in French)
- Automatic Content Positionning: Place subtitles out of pre-existing texts/graphics zones on screen

### Deployment

The entire project is currently deployed using [Kubernetes](https://kubernetes.io){:target="_blank"}.  
Every part of the platform is builded into Docker images and can be deployed easilly with the [startup](https://github.com/media-cloud-ai/startup){:target="_blank"} project.  

### Developement stack

The frontend is designed using [Angular.io](https://angular.io){:target="_blank"}  
<p align="center">
  <img height="100px" src="/assets/images/angular-icon.svg">
</p>

The backend use the power of [Elixir](https://elixir-lang.org/){:target="_blank"}, based on [Erlang](https://www.erlang.org/){:target="_blank"} to provide a resilient and efficient backend.
<p align="center">
  <img height="100px" src="/assets/images/elixir.png">
</p>

Most of workers are using [Rust](https://www.rust-lang.org/){:target="_blank"}, high-typed language with performances similar to C/C++ applications.
Using FFI (Foreign Function Interface), it allows to call any library which provide a C API.
<p align="center">
  <img height="100px" src="/assets/images/rust.svg">
</p>

