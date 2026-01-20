# javapro-github



# apt install docker.io
# groupadd docker
groupadd: group 'docker' already exists
# usermod -aG docker ubuntu
# systemctl enable docker
# systemctl start docker
# docker -v
Docker version 28.2.2, build 28.2.2-0ubuntu1~24.04.1




local ubuntu

jenkins pipeline
Go to
Jenkins Dashboard → Manage Jenkins → Credentials → Global → Add Credentials

DockerHub Credentials
Credential ID Type Value

dockerhub-username Secret Text Your DockerHub username
dockerhub-password Secret Text DockerHub Access Token

 Create DockerHub Token
DockerHub → Account Settings → Security → New Access Token

Jenkins Tool Configuration (One-time)

Go to
Manage Jenkins → Global Tool Configuration

 Java

Name: Java17
Version: JDK 17


 Maven

Name: Maven3
Version: Maven 3.x




DOCKERHUB_USERNAME   sharmila6201
DOCKERHUB_TOKEN		dckr_pat_QCTAtMbzyvchwLPfY1rSGcyJ-mM
EC2_HOST  13.233.92.77
EC2_USER  ubuntu
EC2_SSH_KEY  welcome pemkey copy and paste
