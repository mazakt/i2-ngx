Ansible playbooks
=================

This directory contains the custom Ansible playbooks for the TLA. The structure of this directory
is arbitrary.

Common task snippets
--------------------

The common task snippets provided by framework can be used by custom playbooks. They can be included
using `common/` as a prefix (this directory doesn't need to exist in the repo - symbolic link will
automatically be created during the pipeline run). The available common snippets can be looked up
in the framework repo: https://gitlab.app.betfair/devops/framework/tree/master/playbooks/tasks

Example:

```
- include: common/start_application.yml
```

Shared roles
------------

Roles from ansible-roles gitlab group (https://gitlab.app.betfair/ansible-roles/) can be used in 
the playbooks. If a role's CI job is added as a dependency in Jenkins Job Builder config, the role
will automatically be fetched by the pipeline (in `get_prerequisites` stage) and can be referenced
from a playbook. 

Example:
```
- hosts: new_hosts
  gather_facts: False
  roles:
    - sensu # shared role
    - bf-nginx
    - rsyslog-client # shared role
```

See the documentation for details:

https://confluence.app.betfair/display/i2Program/i2+Configuration+Repos
