Jenkins Agent
=========

This role sets up a Jenkins agent

Requirements
------------

Running this on Windows requires Server 2012+ due to use of the win_scheduled_task module.

Role Variables
--------------

| Variable Name                | Default                                      |
|------------------------------|----------------------------------------------|
| jenkins_agent_master         |                                              |
| jenkins_agent_master_port    | 80                                           |
| jenkins_agent_username       | sa_jenkins_swarm                             |
| jenkins_agent_password       | TR73Vp4r8                                    |
| jenkins_agent_name           | Machine name from the inventory              |
| jenkins_agent_num_executors  | Machine cores * 4                            |
| jenkins_agent_labels         | (RedHat or Windows) swarm                    |

Dependencies
------------

* [Release Engineering - Base](https://github.concur.com/ansible-re/base)

Example Playbook
----------------

```
- hosts: jenkins_agents
  roles:
    - {
        role: jenkins-agent,
        jenkins_agent_master: "{{ hostvars.example_master.ansible_host }}",
        jenkins_agent_num_executors: 8,
        jenkins_agent_labels: "Windows dotnet swarm msbuild"
      }
```
