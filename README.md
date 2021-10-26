# Image Parser
## This is a simple component to parse images from html page.
This component was developed to demonstrate  developing approaches only!!! 

# Installation

```ssh
% composer require sipsystemgm/parser-command-bundle
```

# Configuration

```env
# config/packeges/messager.yaml
framework:
    messenger:
        transports:
             # insert parameter
             parser: '%env(MESSENGER_TRANSPORT_DSN)%'
        routing:
            # insert parameter
            'Sip\ParserCommand\Message\ParserQueueMessage': parser

```

```env
# .env
###> symfony/messenger ###
# Choose one of the transports below
...
# uncomment this page and set you parameters
# MESSENGER_TRANSPORT_DSN=redis://localhost:6379/messages
###< symfony/messenger ###

# insert this block and set your parameters
##> memcached ###
MEMCACHED_HOST=localhost
MEMCACHED_PORT=11211
##> memcached ###
```

```ssh
% php bin/console doctrine:migrations:diff
% php bin/console doctrine:migrations:migrate
```

# Run
```ssh
# run php bin/console parser --help for more details

% php bin/console parser https://some-host 4 20
% php bin/console messenger:consume parser
```

# Testing
## Configurations
```ssh
% composer require --dev phpunit/phpunit symfony/test-pack
% cp .env.test .env.test.local
% cp phpunit.xml.dist phpunit.xml
```

insert memcached block in file .env.test.local and set your parameters
if they are different

```env
##> memcached ###
MEMCACHED_HOST=localhost
MEMCACHED_PORT=11211
##> memcached ##
```

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