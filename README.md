# k8s-bldr

Enable execution of docker in docker builds and executions in a
kubernetes cluster. Experimenting with an executor that accepts yaml
formatted exec definition.

---
### cfg

Setup a shared cfg scripts or clone github.com/davidwalter0/k8s-cfg to
a directory level with the current directory.

link or copy a version of k8s-cfg scripts to .k8s-cfg
and update .cfg/{usage,make-yaml,mycfg,overrides}.

At a minimum .cfg/mycfg is required to point to the clusters address
and naming convention. 

    ln -s /path/to/k8s-cfg/.k8s-cfg .k8s-cfg

If you need to send a build script to the cluster via the service you
can proxy the location or curl to the address


If you need to use json, you might use yaml2json2yaml's

    yaml2json --compress < json > yaml . . .

As a preference the current version of the spec is derived from
k8s-bldr-api v0.1, while the actual path for the api is api/v1 for now
and will remain so, v0.1 up to v0.9 as this is considered alpha
software.

```
#!/bin/bash
dir=$(dirname $(readlink -f ${0}))
. ${dir}/.cfg/functions
main ${@}

```
