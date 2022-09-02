# Terraform-Ansible-Jenkins-AWS

### Terraform
*Add into Terraform providers block after first application*
```
backend "s3" {
  bucket         = "<BUCKET_NAME>"
  key            = "state/terraform.tfstate"
  region         = "us-east-1"
  encrypt        = true
  kms_key_id     = "alias/terraform-bucket-key"
  dynamodb_table = "terraform-state"
}
```
---
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
Docker compose file import: `wget -O docker-compose.yml https://raw.githubusercontent.com/dizthewize/docker_jenkins_lts_alpine_jdk8/main/docker-compose.yml`
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
