# PNM CLI

## Introduction

The pnm command line tool is a utility for building and testing your smart contract project,
and interacting with PNM services.

## Installation

To install pnm, download the latest release from our [GitHub releases page](https://github.com/PwnedNoMore/pnm-cli/releases) and extract the binary to a directory in your `$PATH`.

## Usage

### pnm init

Use the `pnm init` subcommand to initialize your PNM project.

This command will install the dependencies and PNM SDK, create test/pnm directory, and setup remapping to use the PNM SDK.

### pnm build

Use the `pnm build` subcommand to build your project.

It will compile your project and output the result to the build directory.
You can use it for a quick test see if your project satisfies the compiler.

### pnm test

Use the `pnm test` subcommand to run [PNM invariant and property tests](https://pwned-no-more.notion.site/Property-test-and-invariant-test-c6b80f6b6136408ba41247c0be561fe2) for your project.

It will compile your project and run the tests, so you don't have to compile it manually.

### pnm template

Use the `pnm template` subcommand to work with PNM templates.
PNM templates are a set of pre-written invariant tests that you can use to test your smart contract.
You have to fill in the preprepared getter functions to make it work for your project.
It is a good starting point for writing your own tests.

#### Examples

To list available templates, run:

```shell
$ pnm template
Templates available:
	FundLossTest
	OwnerNotChangedTest
	WithdrawWhatDepositTest
```

To install the `FundLossTest` template, run:

```shell
$ pnm template --install FundLossTest
Installing template: [FundLossTest]
Installed template: [FundLossTest] to [test/pnm/FundLossTest_1671118266.sol].
```

### Support

If you encounter any issues, have questions about using PNM CLI, or any feedback,
please contact us in our Discord server. We will be happy to assist you.
