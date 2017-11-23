# OTRv3 Sequence Diagrams

This repository intends to be the place to share the OTRv3[\[1\]](#references)
diagrams in order to fully understand the protocol.

This work can be improved adding notes, better explanations and some simplistic
implementation. This will be done slowly. Feel free to help me.

## Requesting an OTR conversation

There are two ways Alice can inform Bob that she is willing to use the OTR
protocol to speak with him: by sending him the OTR Query Message, or by
including a special "tag" consisting of whitespace characters in one of her
messages to him. Each method also includes a way for Alice to communicate to
Bob which versions of the OTR protocol she is willing to speak with him.

The semantics of the OTR Query Message are that Alice is requesting that Bob
start an OTR conversation with her (if, of course, he is willing and able to do
so). On the other hand, the semantics of the whitespace tag are that Alice is
merely indicating to Bob that she is willing and able to have an OTR
conversation with him. If Bob has a policy of "only use OTR when it's
explicitly requested", for example, then he would start an OTR conversation
upon receiving an OTR Query Message, but would not upon receiving the
whitespace tag.

## Authenticated Key Exchange (AKE)[\[2\]](#references) Diagram

This section outlines the version of the SIGMA protocol[\[3\]](#references)
used as the AKE.  All exponentiations are done modulo a particular 1536-bit
prime, and g is a generator of that group, as indicated in the detailed
description below. Alice and Bob's long-term authentication public keys are
pubA and pubB, respectively.

The general idea is that Alice and Bob do an unauthenticated Diffie-Hellman
(D-H) key exchange to set up an encrypted channel, and then do mutual
authentication inside that channel.

Bob will be initiating the AKE with Alice.

![Authenticated Key exchange diagrama][ake]

## Data Exchange Diagram

This section outlines the method used to protect data being exchanged between
Alice and Bob. As above, all exponentiations are done modulo a particular
1536-bit prime, and g is a generator of that group, as indicated in the
detailed description below.

Suppose Alice has a message (msg) to send to Bob.

![otrv3 data exchange diagram][data-exchange]

## Socialist Millionaires' Protocol (SMP)[\[4\]](#references) Diagram

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

![socialist millionaires protocol diagram][socialist-millionaires-protocol]

## Generating the diagrams

To generate the diagrams I have used [js-sequence-diagrams][jsdd] tool. The
source code to regenerate the diagrams is store at `jssd` folder, and the
compiled SVGs are kept on `img` folder.

## References

[1] - https://otr.cypherpunks.ca/Protocol-v3-4.1.1.html

[2] - https://en.wikipedia.org/wiki/Key_exchange

[3] - https://eprint.iacr.org/2010/454.pdf

[4] - https://en.wikipedia.org/wiki/Socialist_millionaires


[ake]: ./img/otrv3-authenticated-key-exchange.svg
[data-exchange]: ./img/otrv3-data-exchange.svg
[socialist-millionaires-protocol]: ./img/otrv3-socialist-millionaires-protocol.svg

[jsdd]: https://bramp.github.io/js-sequence-diagrams/
