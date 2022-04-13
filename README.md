This repo mirrors loki binaries before they get mirrored by magic
mirror. This is necessary because MM requires files to be named with a
certain pattern in order to succefully mirror. Loki upstream doesn't
conform to this. We also use this repo to mirror
incremental(per-change) builds as tarballs. Upstream, these are
published as docker images

### Mirroring a change build

This requires a working docker install, which your devbox should have.

Anywhere `loki` is used in these instructions, you can replace it with `loki-canary` and `promtail`

Available tags can be found in https://hub.docker.com/r/grafana/loki/tags

```
$ docker create grafana/loki:<tag>
....
<container id>
$ docker cp <container id>:/usr/bin/loki ./
$ tar -cvzf loki-<tag>-amd64.tar.gz ./loki
```

will create a tarball that has the appropriate executable. This
tarball should be committed to the repo and imported into MM
