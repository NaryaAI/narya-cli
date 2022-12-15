# PNM CLI

## Introduction
The pnm command line interface (CLI) tool is a utility for building, testing, and managing projects. It contains four subcommands: init, build, template, and test.

## Installation
To install pnm, download the latest release from our GitHub releases page and extract the binary to a directory in your PATH.

## Usage

### pnm init
Use the `pnm init` subcommand to init your project.

This command can install the dependencies and PNM SDK for your project, initialize test/pnm directory, and setup remapping for your project.

### pnm build

Use the `pnm build` subcommand to build your project.

#### Examples
To build your project and output the result to the build directory, run:

> pnm build

### pnm template
Use the pnm template subcommand to manage templates. It accepts the following options:

- --install: Install a project template

#### Examples
To list available templates, run:

> pnm template

To install the basic template, run:

> pnm template --install basic

### pnm test
Use the pnm test subcommand to run tests for your project.

#### Examples
To run tests for your project, run:

> pnm test

### Support
If you encounter any issues or have questions about using PNM CLI, please open an issue on our GitHub page or join our Discord server,  and we will be happy to assist you.
