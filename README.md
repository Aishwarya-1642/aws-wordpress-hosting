# aws-wordpress-hosting
Deployment of a WordPress CMS website on AWS EC2 instance using LAMP Stack (Linux, Apache, MySQL, PHP)
# AWS WordPress Hosting

##  Project Overview
This project demonstrates how to deploy and host a WordPress website on an AWS EC2 instance using the LAMP stack (Linux, Apache, MySQL, PHP). The goal is to provide a basic yet powerful setup to manage a WordPress site on a cloud server, showcasing cloud infrastructure and server management skills.

##  Tech Stack
- **AWS EC2**: Cloud computing platform for hosting the server.
- **Ubuntu 22.04 LTS**: Operating system for the EC2 instance.
- **Apache**: Web server software for serving HTTP requests.
- **MySQL**: Relational database to store WordPress content.
- **PHP**: Server-side scripting language to run WordPress.
- **WordPress**: Open-source CMS (Content Management System) for building and managing the website.

##  Features
- **Easy Deployment**: Setup of LAMP stack on an EC2 instance to run WordPress.
- **Scalable Architecture**: Ability to scale as traffic grows.
- **Security**: Basic server hardening and access control.
- **WordPress**: Fully functional WordPress website with admin panel access.

##  Deployment Instructions

### 1. Launch EC2 Instance
![Screenshot (75)](https://github.com/user-attachments/assets/4a11a78f-1bdc-4edc-8f39-e11ebb221046)

- Log in to your AWS Management Console and navigate to EC2.
- ![Screenshot (76)](https://github.com/user-attachments/assets/bb78a44c-7a48-4ac7-912d-296365f43dc9)

- Select an **Ubuntu 22.04 LTS** AMI.
- Choose the **t2.micro** instance type (Free Tier eligible).
- ![Screenshot (77)](https://github.com/user-attachments/assets/596a0106-7064-4fc3-aa0e-012a040512c6)

- Configure **Security Groups** to allow HTTP (port 80), HTTPS (port 443), and SSH (port 22).
- ![Screenshot (78)](https://github.com/user-attachments/assets/58e34c91-2177-47ea-bbcc-fe549b204502)
- ![Screenshot (79)](https://github.com/user-attachments/assets/73c2f3da-5bbb-4759-bd62-04c9353d6309)
- ![Screenshot (81)](https://github.com/user-attachments/assets/9953e3b8-58e9-4d2f-b8cf-90c5528ad913)



- Download your **.pem** key pair file for SSH access.

### 2. Connect to Your EC2 Instance
![Screenshot (83)](https://github.com/user-attachments/assets/0aed4ade-4c3b-44e5-8463-7bbc4c9a4ef9)

![Screenshot (82)](https://github.com/user-attachments/assets/2a62a3a9-3043-4188-b39d-fb94eabf08ab)


# Update package list
![Screenshot (88)](https://github.com/user-attachments/assets/d9d5c4da-d433-4179-a471-15bb25bda461)

apt-get update

# Install Apache

![Screenshot (89)](https://github.com/user-attachments/assets/5ba613a7-5042-4998-acb5-76a5ad9fb677)

apt-get install apache2 php-curl php-gd php-mbstring php-xml php-xmlrpc mysql-server libapache2-mod-php php-mysql vim
# Install MySQL

![Screenshot (124)](https://github.com/user-attachments/assets/575e7a71-3fe0-41b0-ba34-7b2a6cb0f5e9)
apt-get install apache2 php-curl php-gd php-mbstring php-xml php-xmlrpc mysql-server libapache2-mod-php php-mysql vim

# Install PHP
apt-get install apache2 php-curl php-gd php-mbstring php-xml php-xmlrpc mysql-server libapache2-mod-php php-mysql vim
![Screenshot (124)](https://github.com/user-attachments/assets/61469471-c543-4a5c-b8a0-3478e316f325)



# Download WordPress
![Screenshot (91)](https://github.com/user-attachments/assets/f92f079d-0d67-49a9-a1db-e20866305a70)
![Screenshot (92)](https://github.com/user-attachments/assets/d3e015fd-f568-4011-ac5d-d252f38ab4d8)


wget -c https://wordpress.org/latest.tar.gz
tar xzvf latest.tar.gz

# Move files to web directory
mv wordpress /var/www/html/
![Screenshot (97)](https://github.com/user-attachments/assets/51ea729b-4278-47da-899c-afd209219a5a)


# Set permissions
chown -R www-data:www-data /var/www/html/wordpress
/etc/init.d/apache2 restart
![Screenshot (121)](https://github.com/user-attachments/assets/1bd77c03-f326-45e8-a60b-b77166ece568)



# Log into MySQL
mysql -u root

![Screenshot (119)](https://github.com/user-attachments/assets/60e7e3ec-672e-48c3-8ab3-0baf88b44bda)
![Screenshot (120)](https://github.com/user-attachments/assets/d8ac69d5-b996-40a4-a5ae-9026b00a63b8)
5. Create MySQL Database and User
create database wordpress;
CREATE USER 'aish'@'localhost' IDENTIFIED BY 'wordpress123';   



# Create WordPress database
CREATE DATABASE wordpress;
![Screenshot (102)](https://github.com/user-attachments/assets/dfc4b0e3-f339-4926-b5cc-be60afcddd78)


# Create WordPress user
CREATE USER 'wpuser'@'localhost' IDENTIFIED BY 'yourpassword';
![Screenshot (118)](https://github.com/user-attachments/assets/873a5963-d757-4bcd-9d6f-2b6afb3908fa)


# Grant privileges
GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpress'@'localhost';
FLUSH PRIVILEGES;
![Screenshot (122)](https://github.com/user-attachments/assets/5ac01166-9a24-4488-b95f-d08bef1c79a8)

FLUSH PRIVILEGES;

# Exit MySQL
![Screenshot (123)](https://github.com/user-attachments/assets/bc74ec2d-eef0-4abe-995a-d6ec452475b8)

EXIT;
6. Complete WordPress Installation
Visit your EC2 public IP in a web browser: http://13.230.220.50/wordpress/wp-admin/index.php.
![Screenshot (105)](https://github.com/user-attachments/assets/5d70c2ed-18cc-468b-afa1-e68b1ded87d6)

![Screenshot (106)](https://github.com/user-attachments/assets/985d725a-fb2a-4f28-9796-ebb5a14f2933)


Follow the on-screen instructions to set up WordPress:

![Screenshot (107)](https://github.com/user-attachments/assets/0b238ca9-ad95-4dc9-ad3c-edbc23c6921c)
![Screenshot (110)](https://github.com/user-attachments/assets/5a621d7a-e585-4863-bffc-992c63c071c5)

Enter database name: wordpress

Database username: wpuser

Database password: yourpassword

Database host: localhost
![Screenshot (108)](https://github.com/user-attachments/assets/1afbd742-57fa-498a-9445-76fb1a1ec9f6)
![Screenshot (109)](https://github.com/user-attachments/assets/022e9ea7-9707-46f7-91c9-0b70d5c8dec5)
![Screenshot (111)](https://github.com/user-attachments/assets/86134e74-ba75-479f-b48a-d4f46428fcb7)
![Screenshot (112)](https://github.com/user-attachments/assets/3498043d-4bf5-44e0-9b73-44a49cea440e)
here is our worpress website which is hosted by aws
![Screenshot (113)](https://github.com/user-attachments/assets/89164ace-87de-41b5-a051-557b8d213fc8)




Security Recommendations 
Elastic IP: Allocate and associate an Elastic IP to your EC2 instance to ensure a static IP address.
![Screenshot (83)](https://github.com/user-attachments/assets/53049828-0bb1-4b94-902e-338deef2e381)
![Screenshot (85)](https://github.com/user-attachments/assets/21c05701-6fb0-4526-bfe0-cf2e4706e72d)
![Screenshot (87)](https://github.com/user-attachments/assets/89d9ecb4-5d84-42e9-850d-6b8d81adfaab)



Firewall: Use security groups and ensure that only required ports (22, 80, 443) are open.
##  Key Learnings

- **AWS EC2 setup and configuration**: Gained experience in launching and managing EC2 instances.
- **LAMP stack deployment**: Learned how to install and configure **Apache**, **MySQL**, and **PHP** on Ubuntu.
- **WordPress configuration**: Developed an understanding of WordPress setup, including configuring wp-config and database connections.
- **Security setup**: Implemented **firewalls**, **security groups**, and **IP management**.
