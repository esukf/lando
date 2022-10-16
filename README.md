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
