# Overview
This repository contains everything needed to build RPM's for zookeeper, including libzookeeper and the devel packages. Different pieces are taken from places around the internet; the init script is quite close to Cassandra's. Individual packages will be built for zookeeper, libzookeeper, and zookeeper-devel.

The spec has been tested on EL6 & EL7 with the EPEL repo enabled.
It should also work on recent Fedoras, too.

# Prepare
Ensure packages are installed that provide tools to build the srpm and mock build the binary rpms.
- `sudo yum install -y rpm-build rpmdevtools mock`

# Building
1. `git clone https://github.com/skottler/zookeeper-rpms`
2. `cd zookeeper-rpms`
3. `rpmdev-setuptree`
4. `spectool -g zookeeper.spec`
5. `rpmbuild -bs --nodeps --define "_sourcedir $(pwd)" --define "_srcrpmdir $(pwd)" zookeeper.spec` 
6. `sudo mock <the srpm from step 5>`

# License
All files in this repository are licensed under the Apache 2 license. Any
redistribution of these files must include the original license as well as
attribution to this repository.
