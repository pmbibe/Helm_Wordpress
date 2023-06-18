# Helm_Wordpress
# For creating a site WordPress simply , you can use this to deploy:  
helm install  --name "yourdomainname" ./Helm_Wordpress  
# Variable:  
- Container.Environment.MARIADB_HOST: Your MySQL Server  
- Container.Environment.MARIADB_PORT_NUMBER: Your MySQL Server Port  
- Container.Environment.MARIADB_ROOT_PASSWORD: Your MySQL Server password of user root if you want auto create database for your domain  
- Container.Environment.MARIADB_ROOT_USER: Your MySQL Server password of user root if you want auto create database for your domain     
- Container.Environment.WORDPRESS_DATABASE_NAME: Database name of your domain  
- Container.Environment.WORDPRESS_DATABASE_USER: Username for using your database  
- Container.Environment.WORDPRESS_DATABASE_PASSWORD: Password of User for using your database     
- Container.Environment.WORDPRESS_EMAIL: Your email    
- Container.Environment.WORDPRESS_FIRST_NAME: Your first name    
- Container.Environment.WORDPRESS_LAST_NAME: Your last name  
For more variable, you can reference at https://github.com/bitnami/bitnami-docker-wordpress-nginx

# Create Helm Repo  
Install cr - https://github.com/helm/chart-releaser  
Create cr.yalm (Config token for authenticating with Github API)  
# Create and Upload Helm Packages  
helm package helm_package_name --destination .deploy  
cr upload -o github_username -r repo -p .deploy  
# Create and upload index file  
helm repo index . --url ...  
