# Image Parser
## This is a simple component to parse images from html page.
This component was developed to demonstrate  developing approaches only!!! 

# Installation

```ssh
% composer create-project sipsystemgm/sip-symfony-framework
```

# Configuration

```ssh
% cp .env .env.local
# uncomment MESSENGER_TRANSPORT_DSN=redis://localhost:6379/messages, #MEMCACHED_HOST, #MEMCACHED_PORT=11211
# set your parameters if need it
```

## Migrations

```ssh
% php bin/console doctrine:migrations:migrate
```

# Frontend install

```ssh
% yarn install
```
or
```ssh
% npm install
```

# Frontend build

```ssh
% yarn run build
```
or
```ssh
% npm run install
```

# Run
```ssh
# run php bin/console sip:parser --help for more details
% php bin/console sip:parser https://some-host 4 20
% php bin/console messenger:consume parser
``` 

# Run web reports

* run symfony webserver (install https://symfony.com/download)
```ssh
% symfony serve -d
```
* go to the url printed bellow after run server
```ssh
[OK] Web server listening                                                                                              
The Web server is using PHP FPM 8.0.11                                                                            
http://127.0.0.1:8000
```

# Testing
## Configurations
```ssh
% cp .env.test .env.test.local
% cp phpunit.xml.dist phpunit.xml
```

insert memcached block in file .env.test.local and set your parameters
if they are different

```env
#.env.test.local
##> memcached ###
MEMCACHED_HOST=localhost
MEMCACHED_PORT=11211
##> memcached ##
```

# Testing
## Configuration

insert test path directory in file  phpunit.xml
```xml
<testsuite name="Project Test Suite">
    <directory>tests</directory>
    ...
    <directory>vendor/sipsystemgm/parser-command-bundle/tests</directory>
 </testsuite>
```

# Run test
```ssh
% composer exec phpunit
```