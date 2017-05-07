# Brightray

Brightray is a static library that makes
[libchromiumcontent](https://github.com/electron/libchromiumcontent) easier to
use in applications.

## Using it in your app

See [electron](https://github.com/electron/electron) for example of an
application written using Brightray.

## Development

### Prerequisites

* Python 2.7
* Linux:
    * Clang 3.0
* Mac:
    * Xcode
* Windows:
    * Visual Studio 2010 SP1
* \*BSD:
    * libchromiumcontent and everything to build libchromiumcontent
    * libnotify
    * clang 3.9

### One-time setup

You must previously have built and uploaded libchromiumcontent using its
`script/upload` script.

    $ script/bootstrap http://base.url.com/used/by/script/upload

### Building

    $ script/build

Building Brightray on its own isn’t all that interesting, since it’s just a
static library. Building it into an application is the only way to test it.

### Building on \*BSD

There's no prebuild binary for \*BSD, So you need build from scratch.

Before all, you should build [libchromiumcontent] first. If libchromiumcontent official repo
is still in porting, use this [alternative repo].

* Install dependency

    # # you should build libchromiumcontent first, that will contains the most dependencies.
    # pkg install libnotify

* Configure

    $ LIBCC=/path/to/libchromiumcontent/src
    $ ./script/bootstrap --commit HEAD \
        --target_arch x64 \
        https://s3.amazonaws.com/github-janky-artifacts/libchromiumcontent \
        --libcc_source_path $LIBCC \
        --libcc_shared_library_path $LIBCC/out-x64/shared_library \
        --libcc_static_library_path $LIBCC/out-x64/static_library

* Build

    $ ./script/build

## License

In general, everything is covered by the [`LICENSE`](LICENSE) file. Some files
specify at the top that they are covered by the
[`LICENSE-CHROMIUM`](LICENSE-CHROMIUM) file instead.

[libchromiumcontent]: https://github.com/electron/libchromiumcontent
[alternative repo]: https://github.com/jinchizhong/libchromiumcontent
