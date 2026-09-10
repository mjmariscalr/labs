# Network Based Attacks CTF 1

## Task 1: Get the perimeter host to release its diagnostic token

> An ordinary scan of the perimeter host reveals little of use. A diagnostic service is listening, but it only responds to connections that present themselves as low-numbered, well-known traffic (like DNS) rather than a random high-numbered source port, anything else is turned away. Work out what source port the service expects your connection to come from, present your connection accordingly, and read the token it returns.

nc -p 53 target1.ine.local 13337

## Task 2: Interrogate the host's management layer

> The perimeter host is monitored. Its management layer will answer questions once you address it correctly - but it will not respond to the obvious defaults. Recover the value it expects, then pull everything the management layer is willing to disclose. One of those disclosures is a token; another is the name of an account you will want later.

snmpwalk -v1 -c mngt -On target1.ine.local 1.3.6.1.4.1 | grep -i "flag"

## Task 3: Enumerate the host's file services without credentials

> The perimeter host shares files. Some of what it shares is available to anyone who asks, with no authentication at all. Enumerate the file services, identify which of them will talk to an unauthenticated client, and read what was left in the open.

usuario anonimo habilitado

## Task 4: Authenticate to the restricted share

> Not everything on the host is public. One share is reserved for a specific account. Between what the management layer told you and what the file services confirm, you know who that account is - now find a way to authenticate as them and read the restricted material. It also tells you where to go next.

se encuentra el usuario con nmap --scirpt snmp-* -p 161 y con enum4linux. contraseña con hydra y valido para obtener el resto de flags en ssh

## Task 5: Reach the internal file server

> There is a second server that you cannot reach from where you are standing. Your foothold on the perimeter host, however, is trusted by it. Use that foothold to route into the internal server, enumerate what it offers, and read the token held on the share that needs no credentials.


## Task 6: Break into the restricted database share

> The internal server keeps its database exports behind a credentialed share. The credentials for it are closer than you think - you passed them on the way in. Authenticate to the restricted share and recover the final token.
