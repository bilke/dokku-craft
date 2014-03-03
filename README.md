## About

Setting up a Craft site on [dokku](https://github.com/progrium/dokku) and [DigitalOcean](https://www.digitalocean.com).

## Instructions

Follow [this tutorial](https://www.andrewmunsell.com/blog/dokku-tutorial-digital-ocean) until the section "Deploying Code". Then ...

On dokku server:

```bash
$ cd /var/lib/dokku/plugins
$ git clone https://github.com/Kloadut/dokku-md-plugin mariadb
$ git clone https://github.com/musicglue/dokku-user-env-compile.git user-env-compile
$ dokku plugins-install
```

On your pc:

```bash
$ git clone https://github.com/bilke/dokku-craft.git
```

Check for the [current Craft](http://buildwithcraft.com/updates) version number. Download latest craft inside your repository directory:

```bash
$ wget http://download.buildwithcraft.com/craft/1.3/1.3.2496/Craft-1.3.2496.zip
$ unzip Craft-1.3.2496.zip
...
replace craft/config/db.php? [y]es, [n]o, [A]ll, [N]one, [r]ename: no
$ rm Craft-1.3.2496.zip
```

Now add all files to git:

```bash
$ git add .
$ git commit -m "Craft files."
```

Add the dokku remote and push to it:

```bash
$ git remote add dokku dokku@apps.domain_name.com:app_name
$ git push dokku master
```

On dokku server:

```bash
$ dokku mariadb:create app_name
```

Hit `app_name.apps.domain_name.com/admin` in your browser and follow Craft's instructions to finish the installation.

## TODO

- Remove `index.php` from URLs
- Figure out how to use this with a custom domain
