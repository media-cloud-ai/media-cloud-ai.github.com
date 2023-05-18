---
layout: default
---
<h1 style="text-align: center;">Use case</h1>

![bla.st](/assets/images/blast_title.jpg)


## An open-source workflow to generate live automatic subtitling

bla.st is an open-source workflow which operates on the media-cloud.ai platform.
It can create subtitles for files and live streams.
The delivered output depends on the targeted use-case: subtitle file or subtitle stream, either for broadcast and web streaming.

bla.st has been developed and strongly experimented by DaIA, the Artificial Intelligence team of France Televisions, on both French and English languages, using the [Speechmatics](https://www.speechmatics.com/) transcription engine.
The workflow stays open to any other engine.

## Screen capture of a live automatic subtitled stream using bla.st

![Screen capture of a live automatic subtitled stream using bla.st](/assets/images/franceinfo_demo.jpg)

### Architecture

bla.st is using at least 3 **workers** to produce subtitles:
1. the **transcript worker**, which generates raw text from audio
2. the **subtitle factory worker**, responsible for creating subtitles blocks from raw text
3. the delivery worker, either the **HLS playlist worker** for a HLS web player or the **newforerver worker** to address a broadcast inserter with a teletext live stream.

Other workers could be added, i.e. if an automatic translation or a better speaker change detector are needed.
All these workers are open to collaborative improvements under the AGPL license.

## use-case example

The schema below describes the infrastructure deployed to connect AWS media services, Media-Cloud.AI and bla.st in order to generate a live stream

![Global architecture of bla.st project](/assets/images/blast_aws_use-case.jpg)
