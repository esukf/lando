# lando

Download and unzip lando to your project folder i.e. myproject

Replace in .lando.yml PROJECTNAME to myproject.

```
sed -i 's/PROJECTNAME/kee/g' .lando.yml
```

Edit .lando.yml to requirement.

Ensure to create the webroot directory if not already exist.
```
mkdir web
```

Start lando to build.

```
lando start
```

Xdebug.

Ensure in .lando.yml the following.

```
config:
  webroot: web
  php: '8.1'
  xdebug: 'true'
```

```
services:
 appserver:
   overrides:
     environment:
       XDEBUG_CONFIG: "discover_client_host=0 client_host=host.docker.internal"
```

Ensure in vscode debug launch configuration to set hostname to 127.0.0.1.

```
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Listen for Xdebug",
            "hostname": "127.0.0.1",
            "type": "php",
            "request": "launch",
            "port": 9003,
            "pathMappings": {
                "/app": "${workspaceRoot}",
             }
        }
    ]
}
```

For Drupal, you have to fix the sites default folder. ssh in to the appserver and chown the folder

```
lando ssh -u root
chmod ug+w /app/web/sites/default
```



