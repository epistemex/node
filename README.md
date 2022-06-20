# Node.js

Node.js is an open-source, cross-platform, JavaScript runtime environment.

For information on using Node.js, see the [Node.js website][].

## Table of contents

* [Support](#support)
* [Release types](#release-types)
  * [Download](#download)
    * [Current and LTS releases](#current-and-lts-releases)
    * [API documentation](#api-documentation)
  * [Verifying binaries](#verifying-binaries)
* [Building Node.js](#building-nodejs)
* [Security](#security)
* [License](#license)

## Support

Looking for help? Check out the
[instructions for getting support](.github/SUPPORT.md).

## Release types

* **Current**: Under active development. Code for the Current release is in the
  branch for its major version number (for example,
  [v15.x](https://github.com/nodejs/node/tree/v15.x)). Node.js releases a new
  major version every 6 months, allowing for breaking changes. This happens in
  April and October every year. Releases appearing each October have a support
  life of 8 months. Releases appearing each April convert to LTS (see below)
  each October.
* **LTS**: Releases that receive Long Term Support, with a focus on stability
  and security. Every even-numbered major version will become an LTS release.
  LTS releases receive 12 months of _Active LTS_ support and a further 18 months
  of _Maintenance_. LTS release lines have alphabetically-ordered code names,
  beginning with v4 Argon. There are no breaking changes or feature additions,
  except in some special circumstances.

Current and LTS releases follow [semantic versioning](https://semver.org). A
member of the Release Team [signs](#release-keys) each Current and LTS release.
For more information, see the
[Release README](https://github.com/nodejs/Release#readme).

### Download

Binaries, installers, and source tarballs are available at
<https://nodejs.org/en/download/>.

#### Current and LTS releases

<https://nodejs.org/download/release/>

The [latest](https://nodejs.org/download/release/latest/) directory is an
alias for the latest Current release. The latest-_codename_ directory is an
alias for the latest release from an LTS line. For example, the
[latest-fermium](https://nodejs.org/download/release/latest-fermium/) directory
contains the latest Fermium (Node.js 14) release.

#### API documentation

Documentation for the latest Current release is at <https://nodejs.org/api/>.
Version-specific documentation is available in each release directory in the
_docs_ subdirectory. Version-specific documentation is also at
<https://nodejs.org/download/docs/>.

### Verifying binaries

Download directories contain a `SHASUMS256.txt` file with SHA checksums for the
files.

To download `SHASUMS256.txt` using `curl`:

```console
$ curl -O https://nodejs.org/dist/vx.y.z/SHASUMS256.txt
```

To check that a downloaded file matches the checksum, run
it through `sha256sum` with a command such as:

```console
$ grep node-vx.y.z.tar.gz SHASUMS256.txt | sha256sum -c -
```

For Current and LTS, the GPG detached signature of `SHASUMS256.txt` is in
`SHASUMS256.txt.sig`. You can use it with `gpg` to verify the integrity of
`SHASUMS256.txt`. You will first need to import
[the GPG keys of individuals authorized to create releases](#release-keys). To
import the keys:

```console
$ gpg --keyserver hkps://keys.openpgp.org --recv-keys DD8F2338BAE7501E3DD5AC78C273792F7D83545D
```

See [Release keys](#release-keys) for a script to import active release keys.

Next, download the `SHASUMS256.txt.sig` for the release:

```console
$ curl -O https://nodejs.org/dist/vx.y.z/SHASUMS256.txt.sig
```

Then use `gpg --verify SHASUMS256.txt.sig SHASUMS256.txt` to verify
the file's signature.

## Building Node.js

See [BUILDING.md](BUILDING.md) for instructions on how to build Node.js from
source and a list of supported platforms.

## Security

For information on reporting security vulnerabilities in Node.js, see
[SECURITY.md](./SECURITY.md).

### Release keys

Primary GPG keys for Node.js Releasers (some Releasers sign with subkeys):

* **Beth Griggs** <<bgriggs@redhat.com>>
  `4ED778F539E3634C779C87C6D7062848A1AB005C`
* **Bryan English** <<bryan@bryanenglish.com>>
  `141F07595B7B3FFE74309A937405533BE57C7D57`
* **Colin Ihrig** <<cjihrig@gmail.com>>
  `94AE36675C464D64BAFA68DD7434390BDBE9B9C5`
* **Danielle Adams** <<adamzdanielle@gmail.com>>
  `74F12602B6F1C4E913FAA37AD3A89613643B6201`
* **James M Snell** <<jasnell@keybase.io>>
  `71DCFD284A79C3B38668286BC97EC7A07EDE3FC1`
* **Juan José Arboleda** <<soyjuanarbol@gmail.com>>
  `61FC681DFB92A079F1685E77973F295594EC4689`
* **Michaël Zasso** <<targos@protonmail.com>>
  `8FCCA13FEF1D0C2E91008E09770F7A9A5AE15600`
* **Myles Borins** <<myles.borins@gmail.com>>
  `C4F0DFFF4E8C1A8236409D08E73BC641CC11F4C8`
* **Richard Lau** <<rlau@redhat.com>>
  `C82FA3AE1CBEDC6BE46B9360C43CEC45C17AB93C`
* **Rod Vagg** <<rod@vagg.org>>
  `DD8F2338BAE7501E3DD5AC78C273792F7D83545D`
* **Ruben Bridgewater** <<ruben@bridgewater.de>>
  `A48C2BEE680E841632CD4E44F07496B3EB3C1762`
* **Ruy Adorno** <<ruyadorno@hotmail.com>>
  `108F52B48DB57BB0CC439B2997B01419BD92F80A`
* **Shelley Vohr** <<shelley.vohr@gmail.com>>
  `B9E2F5981AA6E0CD28160D9FF13993A75599653C`

To import the full set of trusted release keys (including subkeys possibly used
to sign releases):

```bash
gpg --keyserver hkps://keys.openpgp.org --recv-keys 4ED778F539E3634C779C87C6D7062848A1AB005C
gpg --keyserver hkps://keys.openpgp.org --recv-keys 141F07595B7B3FFE74309A937405533BE57C7D57
gpg --keyserver hkps://keys.openpgp.org --recv-keys 94AE36675C464D64BAFA68DD7434390BDBE9B9C5
gpg --keyserver hkps://keys.openpgp.org --recv-keys 74F12602B6F1C4E913FAA37AD3A89613643B6201
gpg --keyserver hkps://keys.openpgp.org --recv-keys 71DCFD284A79C3B38668286BC97EC7A07EDE3FC1
gpg --keyserver hkps://keys.openpgp.org --recv-keys 61FC681DFB92A079F1685E77973F295594EC4689
gpg --keyserver hkps://keys.openpgp.org --recv-keys 8FCCA13FEF1D0C2E91008E09770F7A9A5AE15600
gpg --keyserver hkps://keys.openpgp.org --recv-keys C4F0DFFF4E8C1A8236409D08E73BC641CC11F4C8
gpg --keyserver hkps://keys.openpgp.org --recv-keys C82FA3AE1CBEDC6BE46B9360C43CEC45C17AB93C
gpg --keyserver hkps://keys.openpgp.org --recv-keys DD8F2338BAE7501E3DD5AC78C273792F7D83545D
gpg --keyserver hkps://keys.openpgp.org --recv-keys A48C2BEE680E841632CD4E44F07496B3EB3C1762
gpg --keyserver hkps://keys.openpgp.org --recv-keys 108F52B48DB57BB0CC439B2997B01419BD92F80A
gpg --keyserver hkps://keys.openpgp.org --recv-keys B9E2F5981AA6E0CD28160D9FF13993A75599653C
```

See [Verifying binaries](#verifying-binaries) for how to use these keys to
verify a downloaded file.

<details>

<summary>Other keys used to sign some previous releases</summary>

* **Chris Dickinson** <<christopher.s.dickinson@gmail.com>>
  `9554F04D7259F04124DE6B476D5A82AC7E37093B`
* **Danielle Adams** <<adamzdanielle@gmail.com>>
  `1C050899334244A8AF75E53792EF661D867B9DFA`
* **Evan Lucas** <<evanlucas@me.com>>
  `B9AE9905FFD7803F25714661B63B535A4C206CA9`
* **Gibson Fahnestock** <<gibfahn@gmail.com>>
  `77984A986EBC2AA786BC0F66B01FBB92821C587A`
* **Isaac Z. Schlueter** <<i@izs.me>>
  `93C7E9E91B49E432C2F75674B0A78B0A6C481CF6`
* **Italo A. Casas** <<me@italoacasas.com>>
  `56730D5401028683275BD23C23EFEFE93C4CFFFE`
* **Jeremiah Senkpiel** <<fishrock@keybase.io>>
  `FD3A5288F042B6850C66B31F09FE44734EB7990E`
* **Julien Gilli** <<jgilli@fastmail.fm>>
  `114F43EE0176B71C7BC219DD50A3051F888C628D`
* **Timothy J Fontaine** <<tjfontaine@gmail.com>>
  `7937DFD2AB06298B2293C3187D33FF9D0246406D`

</details>

## License

Node.js is available under the
[MIT license](https://opensource.org/licenses/MIT). Node.js also includes
external libraries that are available under a variety of licenses.  See
[LICENSE](https://github.com/nodejs/node/blob/HEAD/LICENSE) for the full
license text.
