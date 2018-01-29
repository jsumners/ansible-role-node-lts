# `node-lts` Ansible Role

A simple role for deploying the latest [LTS release][lts] of
[Node.js](https://nodejs.org) to Linux (x64) systems. This negates having to
use something like [`n`][n] or [`nvm`][nvm] to maintain a Node installation
when not using distribution packages.

This role installs releases to `/usr/local`.

**Requirement:** this role uses the [`json_query`][jq] filter. Thus, a local
installation of `jmespath` is necessary.

**Note:** a task is delegated to localhost that will retrieve the `index.json`
from the remote Node mirror.

[lts]: https://github.com/nodejs/Release#release-schedule
[n]: https://github.com/tj/n
[nvm]: https://github.com/creationix/nvm
[jq]: http://docs.ansible.com/ansible/latest/playbooks_filters.html#json-query-filter

## Variables:

+ `node_lts_url_scheme` (Default: `https`): defines the URL scheme for accessing
the install tarball.
+ `node_lts_dist` (Default: `nodejs.org/dist`): domain and path for the main
distribution directory on a Node mirror. Note that the value does not include
a trailing `/`.
+ `node_lts_base_url`: a combination of `node_lts_url_scheme` and `node_lts_dist`.
This variable should not need to be modified.
+ `node_lts_update_npm` (Default: `yes`): indicates if the `npm` installation
should be updated as well.
+ `node_lts_npm_env` (Default: `{}`): a hash of environment variables to use
when running `npm` to update `npm`. This can be used to specify proxy servers.

## License

[MIT License](http://jsumners.mit-license.org/)
