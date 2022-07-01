# Docker Environment for Wordpress Development
## Prerequisites
- You must have docker installed on your system:  [macOS Installer](https://docs.docker.com/desktop/mac/install/) *(required)*
- For a better performance on macOS docker-wordpress use [docker-sync](http://docker-sync.io/) *(optional)*
-- `sudo gem install docker-sync`
## Installation
1. Clone the website file repository into your working directory
2. Add `dw` to your aliases file
`alias dw=".dw/bin/dw"`  
3. Clone docker-wordpress into a `.dw` directory in the root of your project
`git clone git@github.com:danhort/docker-wordpress.git .dw`   
4. Initialize the environment with available PHP versions (7.4 or 8.1)
`dw --init-sync <PHP version>` or `dw --init <PHP version>`  
5. Create the new container
`dw start`
6. Copy files to container (not needed with docker-sync)
`dw copytocontainer --all` 
## Usage  
Full list of available options can be found by running: `dw --help`
 
|Command|Description|
|--|--|
|`bash`|SSH into PHP container|
|`build`|Build containers|
|`start`|Start containers|
|`status`|Get containers status|
|`stop`|Stop containers|
|`xdebug`|Enable/Disable xdebug|
|`composer`|Run composer commands|

## Links
Wordpress: https://wordpress.localhost   
phpMyAdmin: http://localhost:8080   
MailHog: http://localhost:8025    
