# OTRv3 Sequence Diagrams

This repository intends to be the place to share the OTRv3[\[1\]](#references)
diagrams in order to fully understand the protocol.

## Authenticated Key Exchange (AKE)[\[2\]](#references) Diagram

![Authenticated Key exchange diagrama][ake]

## Data Exchange Diagram

![otrv3 data exchange diagram][data-exchange]

## Socialist Millionaires' Protocol (SMP)[\[3\]](#references) Diagram

While data messages are being exchanged, either Alice or Bob may run SMP to
detect impersonation or man-in-the-middle attacks. As above, all
exponentiations are done modulo a particular 1536-bit prime, and g1 is a
generator of that group. All sent values include zero-knowledge proofs that
they were generated according to this protocol, as indicated in the detailed
description below.

Suppose Alice and Bob have secret information x and y respectively, and they
wish to know whether x = y. The Socialist Millionaires' Protocol allows them to
compare x and y without revealing any other information than the value of (x ==
y). For OTR, the secrets contain information about both parties' long-term
authentication public keys, as well as information entered by the users
themselves. If x = y, this means that Alice and Bob entered the same secret
information, and so must be the same entities who established that secret to
begin with.

Assuming that Alice begins the exchange:

![socialist millionaires protocol diagram][solialist-millionaires-protocol]

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
[solialist-millionaires-protocol]: ./img/otrv3-solialist-millionaires-protocol.svg

[jsdd]: https://bramp.github.io/js-sequence-diagrams/
