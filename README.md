# Terraform-Ansible-Jenkins-AWS

### AWS Instance
`Jenkins Docker Startup`
```
Repo for Maven use: dizthewize/jenkins-lts-alpine-jdk8
Cmd: docker run --name jenkins-lts -p 8080:8080 -p 50000:50000 -d \
      -v jenkins_data:/var/jenkins_home \
      -v /var/run/docker.sock:/var/run/docker.sock \
      -v $(which docker):/usr/bin/docker dizthewize/jenkins-lts-alpine-jdk8
```
---
### Docker Compose setup
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
