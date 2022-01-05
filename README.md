# Chat

This is a minimal example of using the [buf.build](https://buf.build) *Buf Schema Registry* (BSR) to maintain a protobuffer and/or gRPC API.  This
example is going to evolve a bit as I learn more about how to use *buf.build*, but we are going to try to keep it minimal.

You can find this on <https://buf.build/borud/chat>

## Prerequisites

If you have Go installed and set up correctly on your system.  If you have Go installed you can execute the command:

```shell
make dep
```

which will install the latest version of the `buf` command in your `$GOPATH/bin` directory.

If you do not have Go installed you can check out [the installation instructions on](https://docs.buf.build/installation)

## Makefile

In this project we use `make` to automate the various steps (since make is the lowest common denominator of build systems).  You can also consider the `Makefile` as a piece of compact documentation if you want to use something else in your project.  

## Linting and building

If you just want to run both linting and code generation you can just use the default target in the makefile by running:

```shell
make
```

You can run linting and generation separately by using their own targets:

```shell
make lint
make gen
```

## Check for breakage

To ensure that you do not make changes that break backward compatibility you can use the `breaking` target to check for breakage.  This compares the current state of your repository against the main branch on github.

```shell
make breaking
```

## Publishing

In order to publish updates to the BSR you can run

```shell
make publish
```

This runs the breakage check and if this is okay, publishes the result to <https://buf.build/borud/chat>.  Having a breakage check before you publish is a really good idea.

The other build targets are:

## Cleaning up

The code generated in this project (and placed in the `pkg` directory) isn't really used for anything and doesn't get checked in.  You want to get this code from the BSR when you use it in a project anyway.  This is more to enable you to inspect the result of the code generation.
