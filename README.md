# Patchbay-builder

repo also here : ``

## Setup

```shell
$ npm clone https://github.com/ssbc/patchbay-builder
$ cd patchbay-builder
$ npm install
$ git clone https://github.com/ssbc/patchbay app
```

The latest app source should be in `./app`

### Dependencies

You'll need some more dependencies to create builds.

See the `electron-builder` wiki page: [Multi Platform Build](https://github.com/electron-userland/electron-builder/wiki/Multi-Platform-Build)

On linux you'll need a few more deps:

```
sudo apt-get install icnsutils graphicsmagick xz-utils
```

```
npm install 7zip-bin-linux
```

(**WARNING - looks like `7zip-bin` is being fancy** .. the package-lock Matt uploaded has `7zip-bin-mac` in in)

## Stamp Release

```shell
$ cd patchbay-builder
$ npm run update
$ npm run release
```

Output to `./dist`

## Apple signing

1. buy a developer license D:
2. go to https://developer.apple.com/account/mac/certificate/ and change the view to be macOS (not iOS)
3. hit `[+]` to create a new certificate (I think you want both installer + application certs)
  - Production: Developer ID > Developer ID Installer (and later Developer ID Application)
  - follow the steps for making a certificate signing request (CSR)
  - download your certificates (.cer files)
4. double click on each .cer file. You should now see them under "My Certificates"
5. Run `npm run release` and the builder should auto-find the certificates. (it will let you know if it doesn't!)

NOTE: you might have to install `7zip-bin-mac` for the release to work on mac
