# The Interactive Shell Command

There are two types of shell interactive command applications to use for user choices, but they are similar in terms of the functions they provide to each other:

* A Java-based shell command application
* A native shell command implemented in C/C++

## A Java based Shell Command&#x20;

Here is a serial of commands to build the shell command application for the Carrier Java repository. This process is the same as building a carrier super node service:

```bash
$ git clone git@github.com:elastos/Elastos.Carrier.Java carrier-java
$ cd carrier-java
$ ./mvnw -Dmaven.test.skip=true
$ cd shell/target
```

Under the directory **shell/target**, a binary named `carrier-shell` is generated, and the user can run this executable with the command to enter the interactive console:

```bash
carrier $ ./carrier-shell -c your-config-path/default.conf
Carrier node started
Carrier Id: BCmAbJXmp4ehiShXqQfghEXdq3H1wQVX6syTxT1N7Z56
```

IIf the program is running with the carrier shell without the config file, then the current shell acts as an isolated node detached from the main carrier network. We recommend using the `bootstrap` command to connect to the carrier network next.

* **help**

This is the main command for users to request help with all the commands supported in this shell command application. Users need to learn the commands from the `PicocliCommands` section to delve into the details of the current running carrier node.

```bash
Carrier $ help
  System:
    exit         exit from app/script
    help         command help
  Builtins:
    colors       view 256-color table and ANSI-styles
    history      list history of commands
    keymap       manipulate keymaps
    less         file pager
    nano         edit files
    setopt       set options
    setvar       set lineReader variable value
    ttop         display and update sorted information about threads
    unsetopt     unset options
    widget       manipulate widgets
  PicocliCommands:
    announcepeer Announce a service peer.
    bootstrap    Bootstrap from the node.
    displaycache Display the cached routing table.
    findnode     Find node and show the node info if exists.
    findpeer     Find peer and show the candidate peers if exists.
    findvalue    Find value and show the value if exists.
    id           Display the ID of current Carrier node.
    keygen       Create keypair.
    routingtable Display the routing tables.
    stop         Display the ID of current Carrier node.
    storage      Show the local data storage.
    storevalue   Store a value to the DHT.
```

* **id**

The **`id`** command is used to display a node Id of current shell application running as a carrier node.

```bash
Carrier $ id
Carrier id: BCmAbJXmp4ehiShXqQfghEXdq3H1wQVX6syTxT1N7Z56
Carrier $
```

* **bootstrap**

The **`bootstrap`** command is used to bootstrap this shell application to connect to the carrier network. It would be possibly used on the first that have run it:

```bash
Carrier $ bootstrap HZXXs9LTfNQjrDKvvexRhuMk8TTJhYCfrHwaj3jUzuhZ 155.138.245.211 39001
DHT/IPv4 connected
DHT/IPv4 profound connected
```

* **routingtable**

The **`routingtable`** is used to display information about the routing table, which helps check the health of the current carrier node.

```bash
arrier $ routingtable
Node: BCmAbJXmp4ehiShXqQfghEXdq3H1wQVX6syTxT1N7Z56
DHT: IPv4
Address: 192.168.1.107:39001
buckets: 2 / entries: 13
Prefix: 00/0
  entries[8]:
    0x16a99dce44998bcb8771fe1d0b83d17dc757d9bca6e5b0f63b6c9a96ee40b162/2XTynHmLAWnZtLJsst3dQGd3W5ZpWthyeCS2ToLxk4ws@149.28.250.37:39001;seen:PT0.312S;age:PT19M43.997S;sent:PT2M57.66S;reachable;rtt:181.65;ver:Orca/1
    0x2ee778e5369eb771e5810b3a746bb2653384f0c84118e9d30b6a293aa6c3c6a2/4A6UDpARbKBJZmW5s6CmGDgeNmTxWFoGUi2Z5C4z7E41@107.191.62.45:39001;seen:PT47.865S;age:PT19M43.911S;sent:PT2M37.662S;fail:2;reachable;rtt:268.02;ver:Orca/1
    0x561930b8ce233dc540d74484d2bc88fabd237f169699ccca17b2ec456e9a233d/6o6LkHgLyD5sYyW9iN5LNRYnUoX29jiYauQ5cDjhCpWQ@45.32.138.246:39001;seen:PT2M9.663S;age:PT19M43.85S;sent:PT3M30.585S;fail:2;reachable;rtt:158.48;ver:Orca/1
    0x723726556c69b781445b37679830c86e4225bc52d88559bf65832ca678fb4907/8grFdb2f6LLJajHwARvXC95y73WXEanNS1rbBAZYbC5L@140.82.57.197:39001;seen:PT47.378S;age:PT19M43.765S;sent:PT47.621S;fail:1;reachable;rtt:249.85;ver:Orca/1
    0x71c860442f674cc04a0cdd92c636484bb1a8e43a69b83f85f4585959970360d7/8fAHSUAtKmVycxQK2VRDnhcSL1XX9ciweULt4dHx6Yfg@140.82.34.87:39001;seen:PT7.12S;age:PT19M43.74S;sent:PT2M27.657S;fail:4;reachable;rtt:265.47;ver:Orca/1
    0x3e11ec3d7e6711c283104d54775e528adecb33add29f449d90b61b4069658c64/5BJ8SZZQ4z4izhw82W2ksyuTCQz3GwWUWBSaza4qzVT9@207.148.82.19:39001;seen:PT8.919S;age:PT19M33.952S;sent:PT1M7.627S;fail:6;reachable;rtt:214.05;ver:Orca/1
    0x03e7fd2356197edf9bf022ec1a90a3f6464e0b507f0beda36ca2333398364c4c/GFPvPmt1zhobdgXhQDphdqKtmZdB73ZcgeWSh747pi7@47.101.142.224:39001;seen:PT10.83S;age:PT19M28.865S;sent:PT3M30.586S;reachable;rtt:13.06;ver:Orca/1
    0x7bd74696f31da5b06b84de3ff7f09a2b28cfb367ee01525718f358ddd7ee0d33/9LRYC6YtcRSkwVAdBBLEgszGM6WEEhvjMyGzfgH6sN2e@114.92.191.12:56895;seen:PT3.909S;age:PT16M18.578S;sent:PT17.609S;fail:16;reachable;rtt:14;ver:Meerkat/1
  cache[1]:
    0x455c56bf55cc3035948f50e01aaf63db84eada4c847592fd6b10ceffc6f1a2b4/5fkoB5RqMJj8xkFgkBPqb6e2uFuHJ3W5CjM5vBkMYzy9@114.92.191.12:56896;seen:PT5.2S;age:PT16M6.439S;sent:PT14M17.915S;fail:9;reachable;rtt:28.22;ver:Meerkat/1

Prefix: 80/0 [Home]
  entries[5]:
    0xf610197a374dfc3801cb00ad1acda6f7a52bb8e0bff10a3e0db2aacdcea41ed8/HZXXs9LTfNQjrDKvvexRhuMk8TTJhYCfrHwaj3jUzuhZ@155.138.245.211:39001;seen:PT37.424S;age:PT19M44.186S;sent:PT37.616S;reachable;rtt:179.81;ver:Orca/1
    0xf146bfa0857fbdd9980a4d7f1472b01d171f70fb903b8b183002a4ea90003d29/HEqpt5wCnNyGdtq1tmhyXvM9szEp8xGDfH7FELMoDqkk@66.42.79.198:39001;seen:PT12.095S;age:PT19M44.001S;sent:PT1M47.643S;reachable;rtt:171.38;ver:Orca/1
    0xfd5f8031437a851656230497a1498276275dc9e31db1e00139d4c98dec5fd65d/J44cKHHjJzpJJhM4tqwZxYhv9Cynozx38xeR2WcvfFRN@139.84.232.184:39001;seen:PT27.191S;age:PT19M43.756S;sent:PT27.611S;reachable;rtt:425.05;ver:Orca/1
    0xf61eaebb0d2ccfe72c2aa878283044eaaf4c770518f8f4afddc263d755285797/HZkRueotBBsuV47ohpWAKbTgC1PnaAbJFhwNdeqsy9dp@101.88.96.240:13865;seen:PT1M14.115S;age:PT17M46.853S;sent:PT1M17.632S;reachable;rtt:9.53;ver:Meerkat/1
    0xd303870430fe88c1920a7ac80772b3c8b68a0d4b4ce1102108706c1ec16eee75/FCi9M2ffhNZESnsqNisXN1wjEamKv2T5xeESijupiPVn@93.44.141.3:39001;seen:PT12.485S;age:PT16M52.899S;sent:PT57.622S;fail:28;reachable;rtt:208.6;ver:Orca/1
```

* **keygen**

The **`keygen`** command is used to generate private/public key pairs for encryption or signature purposes. The private key for signing can be used to announce a service peer when deploying an Active Proxy service on a super node or a personal service to utilize the Active Proxy service on a native client application.

```bash
Carrier $ keygen
Signature:
  Private(Hex): 58bb783307742a0e3158642a88f133332cac5a3ac440a87bcaa5382d4e3245ec3b28dd37661fe4f631f7602fd4d6644402c9da3585841e2746054eff33a296cf
   Public(Hex): 3b28dd37661fe4f631f7602fd4d6644402c9da3585841e2746054eff33a296cf
   Public(B58): 4ywCHfUYDevE78jcTSDD6yo1CnJzSeKsxR1nvY25g5gr
Encryption:
  Private(Hex): d83b4c4626b6709b8df0fbc35b10fa5a101f465e439f0e2970d0d563881d6760
   Public(Hex): e43c6b4fcb4157f38c2fc3076c20d40375477040f4cf73a1afc3f8e1887d841b
   Public(B58): GMwPdNvE1UstAKCDo1BWqZqsYdc8mkDGdFuArY6Fwb3p
Carrier $ 

```

* **findnode**

The **`findnode`** command is used to retrieve other or neighboring carrier nodes with a given node ID over the carrier network. This command internally utilizes the carrier protocol `find-node` to look up the specific carrier node across the entire carrier network.

```bash
Carrier $ findnode 2XTynHmLAWnZtLJsst3dQGd3W5ZpWthyeCS2ToLxk4ws
IPv4: <2XTynHmLAWnZtLJsst3dQGd3W5ZpWthyeCS2ToLxk4ws,/149.28.250.37,39001>
IPv6: <2XTynHmLAWnZtLJsst3dQGd3W5ZpWthyeCS2ToLxk4ws,/149.28.250.37,39001>
```

* **storevalue**

The **`storevalue`** is used to store a specific value over the carrier network. The value can be retrieved later by using the command findvalue. This command internally utilizes the carrier protocol store-value to propagate the value to be stored across the entire carrier network.

```
Carrier $ storevalue -m "hello-world"
Value 8mL3KYWP3xaqJpo7ECeB7C2kv1KCij4sdRfWRPbvRzaq stored.
```

* **findvalue**

The **`findvalue`** command is used to retrieve the specific value information by a give value ID. This command internally utilizes the carrier protocol `find-value` to lookup the value item across the entire carrier.

```bash
Carrier $ findvalue 8mL3KYWP3xaqJpo7ECeB7C2kv1KCij4sdRfWRPbvRzaq
id:8mL3KYWP3xaqJpo7ECeB7C2kv1KCij4sdRfWRPbvRzaq,publicKey:BsNxi3gyXytHCQGuB457zm2n3VKyfZWzPyBk5EVDiNPo,nonce: 4079d0990affccc590ce61c8dbd61dcacaa64263bdde6965,seq:0,sig:09c6771869f3e737a05491839c497b121d9a2bce74e86c7eee0d7b1f20d6900be91bfe56dfe52c14c86e13e6dad3644efc213e3f28fdc5008367c95b1e4ae804,data:68656c6c6f2d776f726c64
```

* **announcepeer**

The `announcepeer` command is used to announce a peer information, such as a personal web service of your own. This command internally utilizes the carrier protocol `announce-peer` to propagate the peer information across the entire carrier network.

```bash
Carrier $ announcepeer -k 58bb783307742a0e3158642a88f133332cac5a3ac440a87bcaa5382d4e3245ec3b28dd37661fe4f631f7602fd4d6644402c9da3585841e2746054eff33a296cf 12345
Peer 4ywCHfUYDevE78jcTSDD6yo1CnJzSeKsxR1nvY25g5gr announced with private key 58bb783307742a0e3158642a88f133332cac5a3ac440a87bcaa5382d4e3245ec3b28dd37661fe4f631f7602fd4d6644402c9da3585841e2746054eff33a296cf
```

* **findpeer**

The **`findpeer`** command is used to retrieve a list of peer information with a given peer ID. This command internally utilizes the carrier protocol find-peer to lookup all peers across the entire carrier network as much as possible. Here is an example to retrieve all carrier nodes that provides the Active Proxy service with a given peer ID.

```bash
Carrier $ findpeer 5vVM1nrCwFh3QqAgbvF3bRgYQL5a2vpFjngwxkiS8Ja6
<5vVM1nrCwFh3QqAgbvF3bRgYQL5a2vpFjngwxkiS8Ja6,6o6LkHgLyD5sYyW9iN5LNRYnUoX29jiYauQ5cDjhCpWQ,8090>
<5vVM1nrCwFh3QqAgbvF3bRgYQL5a2vpFjngwxkiS8Ja6,4A6UDpARbKBJZmW5s6CmGDgeNmTxWFoGUi2Z5C4z7E41,8090>
<5vVM1nrCwFh3QqAgbvF3bRgYQL5a2vpFjngwxkiS8Ja6,8grFdb2f6LLJajHwARvXC95y73WXEanNS1rbBAZYbC5L,8090>
<5vVM1nrCwFh3QqAgbvF3bRgYQL5a2vpFjngwxkiS8Ja6,HZXXs9LTfNQjrDKvvexRhuMk8TTJhYCfrHwaj3jUzuhZ,8090>
```

There are more commands not mentioned above that would be helpful for retrieving additional internal state or information of the current shell as a carrier node.

* **stop**

The `stop` command is used to exit from this carrier shell command application.

```bash
Carrier $ stop
Carrier node stopped
```

## A native shell command implemented in C/C++

Below is a serial of commands to build the shell command application for the Carrier Native repository. This process is the same as building a native carrier launcher running as the Active Proxy client:

```bash
$ git clone git@github.com:elastos/Elastos.Carrier.Native carrier-native
$ cd carrier-native/build && mkdir prod
$ cmake -DCMAKE_INSTALL_PREFIX=dist ../..
$ make -jN
$ make install
$ ./dist/bin/carrier-shell -c YOUR-CONFIG-PATH/default.conf

```

Under the directory `dist/bin` of your building environment, a binary named `carrier-shell` is generated, and the user can run this executable with the command to enter the interactive console:

```bash
carrier $ ./carrier-shell -c your-config-path/default.conf
Carrier node started
Carrier Id: BCmAbJXmp4ehiShXqQfghEXdq3H1wQVX6syTxT1N7Z56
```

The commands supported on the native carrier shell are very similar to the shell of the Java implementation. We encourage users to also experience this shell application to get more internal state or information for the native carrier node.
