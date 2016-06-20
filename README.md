# HTTPAuthentificationOverXMPP

Provide an HTTP anthentification over XMPP. Implementation of [XEP-0070](https://xmpp.org/extensions/xep-0070.html).


## Compilation
### Dependencies

 * [go-xmpp](https://git.kingpenguin.tk/chteufleur/go-xmpp) for the XMPP part.
 * [cfg](https://github.com/jimlawless/cfg) for the configuration file.


Download the CA at [https://kingpenguin.tk/ressources/cacert.pem](https://kingpenguin.tk/ressources/cacert.pem), then install it on your operating system.
Once installed, go into your $GOPATH directory and go get the source code.
```sh
go get git.kingpenguin.tk/chteufleur/go-xmpp4steam.git
```

### Configure
Configure the gateway by editing the ``httpAuth.cfg`` file in order to give all XMPP component and HTTP server informations.

### Utilization
To ask authorization, just send an HTTP request to the path ``/auth`` with parameters:
 * jid: JID of the user (<user@host/resource> or <user@host>)
 * domain: Domain you want to access
 * method: Method you access the domain
 * transaction_id: Transaction identifier

Example:
```
GET /auth?jid=user@host/resource&domain=example.org&method=POST&transaction_id=WhatEverYouWant HTTP/1.1
```

This will send a request to the given JID. If the user accept, the server will return HTTP code 200, otherwise it will return HTTP code 401.
