
Overview
========

Configuration is essential yet there is no decent approach that scales.

Configuration, just like other aspects must be layered. Different approaches to configuration must be combined to form a solution that is adaptable enough to accomodate the diverse requirements of a complex system.

The best way to capture configuration information is using JSON.

So we build a configuration language that uses JSON to stich together configuration readers and consolidating abstractions to end up with one final configuration object that while being dynamically generated upon change in the source inputs; it becomes a **stable system blueprint** that is versioned and acts as the backbone to any runtime logic that operates upon it.


Solution
--------

Usernames in brackets are the developers of the components I will be integrating. I am seeking to work closer with them and their communities.
If you can assist in making this happen, please do what you can.


#### Implementation

  * https://github.com/c9/vfs to read configuration files from any source [creationix](https://github.com/creationix)
  * NodeJS modules that process streams to convert native configuration formats into closely related JSON structures. [cadorn](https://github.com/cadorn)
  * NodeJS modules that process the raw JSON structures into common abstracted JSON structures that follow patterns. [cadorn](https://github.com/cadorn)
  * https://github.com/creationix/js-git/ to store polished abstracted JSON structures [creationix](https://github.com/creationix)
    * Also used to store encrypted JSON structures used to hold sensitive credentials [creationix](https://github.com/creationix)
    * Also used to sync JSON structures across nodes over a network [kriskowal](https://github.com/kriskowal)
  * A layerd filesystem that overlays JSON structures using paths [kriskowal](https://github.com/kriskowal) [cadorn](https://github.com/cadorn)
  * A merging language and schema system to process abstarcted JSON structures into the **single stable blueprint observable JavaScript object**. [cadorn](https://github.com/cadorn)
    * https://github.com/montagejs/frb to observe and replicate changes [kriskowal](https://github.com/kriskowal)
  * Various NodeJS modules to consume the blueprint object to build distributed services and applications. [cadorn](https://github.com/cadorn)
  * Various approaches to model aspects of a system through the proposed solution. [cadorn](https://github.com/cadorn)

#### User Experience

  1. User clones devcomp.io
  2. User runs one command to install devcomp.io locally and trigger the provision of an instance
  3. User is prompted on the command-line for minimum credentials as properties are needed to provision the instance
  4. Instance launches and services are deployed and finally admin system opens
  5. User authenticates and uses admin
  6. Whenever user interacts with a component that needs configuration information or sensitive credentials it promts the user and caches result based on predetermined rules

#### Automation

  * Instead of the user entering information, a service may be connected that based on some established identity fetches the relevant
    information to avoid any breaks in the realtime interaction of a user with a new component.
  * Git is great for distribution if conflicts can be avoided. Thus we will use only a subset of the capabilities of the above solution
    and describe distribution flows that can be automatically orchestrated only.

#### Abstraction

  * The above solution, if implemeneted in a light enough fashion can become a standard portable JavaScript component capable
    of described processing for all types of data streams.
