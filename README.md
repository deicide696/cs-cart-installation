# CS-Cart installation about Amazon WebServices AWS EC2 (ALB) Docker, Certificate Manager (HTTPS) and Route 53
CS-Cart installation about AWS EC2 (ALB) Docker, Certificate Manager (HTTPS) and Route 53

1. Deploy EC2 instance - Amazon Linux 2 with 30 GB in ELB, open ports: 22, 80, 443
3. Prepare EC2 instance with git, docker and docker-compose
- Connect to SSH and run:
  - sudo yum update -y
  - sudo amazon-linux-extras install docker -y
  - sudo service docker start
  - sudo usermod -a -G docker ec2-user
  - Log out
  - docker info
  - sudo chkconfig docker on
  - sudo yum install git -y
  - sudo reboot
  - sudo curl -L https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose (Ref: https://gist.github.com/npearce/6f3c7826c7499587f00957fee62f8ee9)
  - sudo chmod +x /usr/local/bin/docker-compose
  - docker-compose version
4. In local folder in EC2 instance (cd ~), clone repo: git clone https://github.com/cscart/development-docker.git && cd development-docker
5. mkdir -p app/www
6. cd app/www
7. Upload multivendor files into the app/www directory
8. chmod 666 config.local.php
9. chmod -R 777 design images var
10. find design -type f -print0 | xargs -0 chmod 666
11. find images -type f -print0 | xargs -0 chmod 666
12. find var -type f -print0 | xargs -0 chmod 666
13. chmod 644 design/.htaccess images/.htaccess var/.htaccess var/themes_repository/.htaccess
14. chmod 644 design/index.php images/index.php var/index.php var/themes_repository/index.php
15. cd .. && cd ..
16. cp config/nginx/app.conf.example config/nginx/app.conf
17. make -f Makefile run


MySQL connection (info for installation)

DB host: mysql5.7
User: root
Password: root

## References:

- https://docs.cs-cart.com/latest/install/linux/index.html
