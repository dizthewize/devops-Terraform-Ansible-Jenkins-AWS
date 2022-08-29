
`Add Agent container after initial Jenkins wizard setup`
```
agent:
  image: jenkins/ssh-agent:jdk11
  privileged: true
  user: root
  container_name: agent
  expose:
    - 22
  environment:
    - JENKINS_AGENT_SSH_PUBKEY=
```
