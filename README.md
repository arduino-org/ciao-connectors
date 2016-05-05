# Ciao Connectors
Linino feed of Connectors for Arduino Ciao.
Here are stored all the **Makefile** used to build each connector. Please fill the following fields if you want to provide us the **Makefile** for your custom connector :
```
PKG_CONNECTOR:=<NAME>
PKG_REVISION:=<HASH>
PKG_VERSION:=<x.y.z>
PKG_RELEASE:=1
```
* **PKG_CONNECTOR** : replace the entry **<NAME>** with the very name of your connector
* **PKG_REVISION** : replace **<HASH>** with the git long hash of your desired commit
* **PKG_VERSION** : replace **<x.y.z>** with a three-digit number, each separated by a dot. Please also make a release matching the same version and commit hash.
* **PKG_RELEASE** : replace **1** with an higher number for slight modifications of your Makefile (optional)

The source residing on your repository should follow this similar folder tree (this is the **XMPP** one):
```
ciao-connector-xmpp/
├── examples
│   └── XMPPHelloBot
├── README.md
├── xmpp
│   ├── sleekxmpp
│   ├── xmppciao.py
│   ├── xmppclient.py
│   ├── xmpp.json.conf
│   └── xmpp.py
└── xmpp.ciao.json.conf
```
So, we make it a general purpose use like this :
```
ciao-connector-<NAME>/
├── examples
│   └── myexample
├── README.md
├── <NAME>
│   ├── additional-python-module-1
│   ├── additional-python-module-2
│   ├── additional-python-module-N
│   ├── my-python-module-1.py
│   ├── my-python-module-2.py
│   ├── my-python-module-N.py
│   ├── <NAME>.json.conf
│   └── <NAME>.py
└── <NAME>.ciao.json.conf
```
Let's take a look at it :

- **ciao-connector-\<NAME\>** is the name on your connector github repo. 
- Inside the root folder you have to write the main connector configuration file **\<NAME\>.ciao.json.conf** (the one relating with the ciao core)
- **\<NAME\>** is the source main folder of your connector code.
 - You can distribute inside it one or more **additional-python-module-N/** or custom libraries such as **my-python-module-N.py**
 - **\<NAME\>.py** is the main library of your connector, the one that will be invoked by ciao
 - **\<NAME\>.json.conf** is where you store additional settings for your connector applications.

## How to Integrate a third part Ciao Connector
To push your Ciao connector written from scratch, please follow this steps :

* Fork this feed
* Add the `Makefile` according the following filesystem tree
```
ciao-<connector-name>/
└── Makefile
```
* Make a pull request, we will be very happy to accept your connector into our main feed after running all the necessary tests
