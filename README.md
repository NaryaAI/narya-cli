# PNM CLI

## Introduction

Welcome to PNM CLI, the command line tool that helps you build and test your smart contract project,
and interact with PNM services.

## Installation

To install PNM CLI, open your terminal and type in the following command:

```bash
curl -L https://raw.githubusercontent.com/PwnedNoMore/pnm-cli/main/script/install | bash
```

This command will download PNM CLI to `~/.pnm` and add it to your `$PATH`.

If the installation is successful, you can run the pnm command from your shell.

### Upgrading

To update PNM CLI after installation, run the following command:

```bash
pnm upgrade
```

This command will upgrade PNM CLI to the latest version.

## Usage

### Initializing your PNM project

To initialize your PNM project, use the `pnm init` subcommand.
This command installs the dependencies and PNM SDK, creates a test/pnm directory,
and sets up remapping to use the PNM SDK.

Example:

```bash
pnm init
```

Once you've initialized your project, add invariants in the `test/pnm` directory,
and then run `pnm test` to test your invariants.

For more information about invariant writing, please see the following links:

* [PNM Engine Developer Documentation](https://pwned-no-more.notion.site/PNM-Engine-Developer-Documentation-a73b9c46d24b481eb0fd06ea8fa57f69)
* Invariant example: https://github.com/PwnedNoMore/pnm-examples

You can also use `pnm template` to check and install available templates.

### Running invariant/property/Foundry tests

To run invariant and property tests for your project, use the `pnm test` subcommand.
This command compiles your project and runs the tests, so you don't have to compile it manually.

For more information about invariant and property tests, please see
[PNM invariant and property tests](https://pwned-no-more.notion.site/Property-test-and-invariant-test-c6b80f6b6136408ba41247c0be561fe2).

Example:
```bash
pnm test
```

The output looks like this:

```log
$ pnm test
Building project...
Testing...

Tests (4)
[√] test/pnm/FundLossTest_1671121896.sol:FundLossTest:invariantCheckFund()
[√] test/pnm/FundLossTest_1671156195.sol:FundLossTest:invariantCheckFund()
[√] test/pnm/FundLossTest_1671181213.sol:FundLossTest:invariantCheckFund()

[✕] test/pnm/OwnerNotChangedTest_1672380141.sol:OwnerNotChangedTest:invariantOwnerNotChanged()
  [3057] OwnerNotChangedTest::invariantOwnerNotChanged()
    ├─ [194] OwnerNotChangedTest::getOwner()
    │   └─ ← 0x0000000000000000000000000000000000000000
    └─ ← "Ownership changes!"


Total: 4, Success: 3, Fail: 1
Time: 26s

The following invariant(s) reverted, it's likely the PNM engine will also fail if push as-is.
• File: test/pnm/OwnerNotChangedTest_1672380141.sol, Contract: OwnerNotChangedTest, Function: invariantOwnerNotChanged()

A Test report generated at ./reports/report_1672973405.zip. To view the report, visit the following URL and upload the report zip file:

https://app.pwnednomore.org/debugger

Please refer to the call trace for more information and try running the test again after fixing the issue.
```

### Working with PNM templates

To work with PNM templates, use the `pnm template` subcommand.
PNM templates are a set of pre-written invariant tests that you can use to test your smart contract.
You have to fill in the pre-prepared getter functions to make it work for your project.
It is a good starting point for writing your own tests.

Examples:

To list available templates, run:

```bash
pnm template
```

To install the `DepositWithdrawalFailureTest` template, run:

```bash
pnm template --install DepositWithdrawalFailureTest
```

Then open the newly created file and finish the TODOs.

### Data collection and metrics

PNM collects anonymous usage data and metrics to help improve PNM CLI.
We collect information related to how you use PNM CLI,
such as which commands you run and how long they take to complete.

If you would prefer to opt out of metrics upload, you can run:

```bash
touch ~/.pnm/.metrics_disabled
```

or set the environment variable `PNM_METRICS_DISABLED` to `true`:

```bash
export PNM_METRICS_DISABLED=true
```


### Support

If you encounter any issues, have questions about using PNM CLI, or any feedback,
please contact us in our Discord server. We will be happy to assist you.
