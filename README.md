# OTRv3 Sequence Diagrams

This repository intends to be the place to share the OTRv3[\[1\]](#references)
diagrams in order to fully understand the protocol.

## Authenticated Key Exchange (AKE)[\[2\]](#references) Diagram

![Authenticated Key exchange diagrama][ake]

## Data Exchange Diagram

![otrv3 data exchange diagram][data-exchange]

## Socialist Millionaires' Protocol (SMP)[\[3\]](#references) Diagram

![socialist millionaires protocol diagram][]

## Generating the diagrams

To generate the diagrams I have used [js-sequence-diagrams][jsdd] tool. The
source code to regenerate the diagrams is store at `jssd` folder, and the
compiled SVGs are kept on `img` folder.

## References

[1] - https://otr.cypherpunks.ca/Protocol-v3-4.1.1.html

[2] - https://en.wikipedia.org/wiki/Key_exchange

[3] - https://en.wikipedia.org/wiki/Socialist_millionaires


[ake]: ./img/otrv3-authenticated-key-exchange.svg
[data-exchange]: ./img/otrv3-data-exchange.svg

[jsdd]: https://bramp.github.io/js-sequence-diagrams/
