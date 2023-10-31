# WikiJS Theme for Kaspa Wiki
A theme for the [Kaspa Wiki](https://wiki.kaspa.org).

## Installation

You can use the theme directly by copying the [compiled theme](https://github.com/thuun/wiki-js-kaspa/blob/master/theme/publish/wiki.css) into your WikiJS instance. 

1. Login with an administrator account and navigate to Administration (top right gear), then "Themes".
2. Paste [this CSS](https://github.com/thuun/wiki-js-kaspa/blob/master/theme/publish/wiki.css) into the "CSS Override" textbox.
3. Then click Apply.

![install](install.jpg)

> :bulb: This is not a theme "package", instead it is provided as simple CSS overrides to the standard WikiJS theme.

-----

## Development

To build the theme, you'll need sass:
```sh
apt install sass
```

Then to build the `theme/`:
```sh
sass --style=nested --sourcemap=none --watch kaspa-wiki.scss:publish/wiki.css
```

Create a peristent data folder for the docker wikiJS database:
```sh
mkdir data && chmod 777 data
```

For daemon mode:
```sh
docker run -d -p 8080:3000 --name wikijs --restart unless-stopped -e DB_TYPE=sqlite -e DB_FILEPATH=/srv/db.sqlite -v "$(pwd)/data:/srv:rw" requarks/wiki
```

In terminal:
```sh
docker run -p 8080:3000 --name wikijs --restart unless-stopped -e DB_TYPE=sqlite -e DB_FILEPATH=/srv/db.sqlite -v "$(pwd)/data:/srv:rw" requarks/wiki
```
