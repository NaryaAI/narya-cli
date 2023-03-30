# Narya CLI

## Introduction

Welcome to Narya CLI, the command line tool that helps you build and test your smart contract project,
and interact with Narya services.

## Installation

To install Narya CLI, open your terminal and type in the following command:

```bash
curl -L https://raw.githubusercontent.com/NaryaAi/Narya-cli/main/script/install | bash
```

This command will download Narya CLI to `~/.narya` and add it to your `$PATH`.

If the installation is successful, you can run the Narya command from your shell.

### Upgrading

To update Narya CLI after installation, run the following command:

```bash
narya upgrade
```

This command will upgrade Narya CLI to the latest version.

## Usage

### Initializing your Narya project

To initialize your Narya project, use the `narya init` subcommand.
This command installs the dependencies and Narya SDK, creates a test/invariants directory,
and sets up remapping to use the Narya SDK.

Example:

```bash
narya init
```

Once you've initialized your project, add invariants in the `test/invariants` directory,
and then run `narya test` to test your invariants.

For more information about invariant writing, please see the following links:

* [Narya Documentation](https://docs.narya.ai)
* Invariant examples: https://github.com/NaryaAi/Narya-examples

You can also use `narya template` to check and install available templates.

### Running invariant/property/Foundry tests

To run invariant and property tests for your project, use the `narya test` subcommand.
This command compiles your project and runs the tests, so you don't have to compile it manually.

For more information about invariant and property tests, please see
[Narya test types](https://docs.narya.ai/test_types).

Example:
```bash
narya test
```

The output looks like this:

```log
$ narya test
Building project...
Testing...

Tests (4)
[√] test/invariants/FundLossTest_1671121896.sol:FundLossTest:invariantCheckFund()
[√] test/invariants/FundLossTest_1671156195.sol:FundLossTest:invariantCheckFund()
[√] test/invariants/FundLossTest_1671181213.sol:FundLossTest:invariantCheckFund()

[✕] test/invariants/OwnerNotChangedTest_1672380141.sol:OwnerNotChangedTest:invariantOwnerNotChanged()
  [3057] OwnerNotChangedTest::invariantOwnerNotChanged()
    ├─ [194] OwnerNotChangedTest::getOwner()
    │   └─ ← 0x0000000000000000000000000000000000000000
    └─ ← "Ownership changes!"


Total: 4, Success: 3, Fail: 1
Time: 26s

The following invariant(s) reverted, it's likely the Narya engine will also fail if push as-is.
• File: test/invariants/OwnerNotChangedTest_1672380141.sol, Contract: OwnerNotChangedTest, Function: invariantOwnerNotChanged()

A Test report generated at ./reports/report_1672973405.zip. To view the report, visit the following URL and upload the report zip file:

https://app.narya.ai/debugger

Please refer to the call trace for more information and try running the test again after fixing the issue.
```

### Working with Narya templates

To work with Narya templates, use the `narya template` subcommand.
Narya templates are a set of pre-written invariant tests that you can use to test your smart contract.
You have to fill in the pre-prepared getter functions to make it work for your project.
It is a good starting point for writing your own tests.

Examples:

To list available templates, run:

```bash
narya template
```

To install the `DepositWithdrawalFailureTest` template, run:

```bash
narya template --install DepositWithdrawalFailureTest
```

Then open the newly created file and finish the TODOs.

### Data collection and metrics

Narya collects anonymous usage data and metrics to help improve Narya CLI.
We collect information related to how you use Narya CLI,
such as which commands you run and how long they take to complete.

If you would prefer to opt out of metrics upload, you can run:

```bash
touch ~/.narya/.metrics_disabled
```

or set the environment variable `NARYA_DISABLE_METRICS` to `true`:

```bash
export NARYA_DISABLE_METRICS=true
```


### Support

If you encounter any issues, have questions about using Narya CLI, or any feedback,
please contact us in our Discord server. We will be happy to assist you.
