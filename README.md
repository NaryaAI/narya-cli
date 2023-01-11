# PNM CLI

## Introduction

The pnm command line tool is a utility for building and testing your smart contract project,
and interacting with PNM services.

## Installation

To install the latest version of pnm, open your terminal and type in the following command:

```bash
curl -L https://raw.githubusercontent.com/PwnedNoMore/pnm-cli/main/script/install | bash
```

This will download PNM CLI to `~/.pnm` and add it to your $path.

If everything goes well, you will now have a binaries at your disposal: pnm.

### Upgrade
To update PNM CLI after installation, simply run:
```shell
$ pnm upgrade
pnm is already installed, version 0.0.1
Latest pnm version is 0.1.0
pnm: Installing pnm...
pnm: downloading latest pnm
######################################################################## 100.0%
pnm: installed - pnm 0.1.0 (f9e4d2e 2022-01-02T05:24:17.307483Z)
```

It will update to the latest PNM release.

## Usage

### pnm init

Use the `pnm init` subcommand to initialize your PNM project.

This command will install the dependencies and PNM SDK, create test/pnm directory, and setup remapping to use the PNM SDK.

#### Example
To initialize your PNM project, run:
```shell
$ pnm init
Installing dependencies...
Installing PNM SDK...
Creating test/pnm folder...
Setting up remappings...

Your project has been successfully initialized.

**If you have git submodules other than pnm-contract, make sure they are also installed**

You can add invariants in the 'test/pnm' directory, and then run `pnm test` to test your invariants.

For more information about invariant writing, please see the following links:
PNM Engine Developer Documentation: https://pwned-no-more.notion.site/PNM-Engine-Developer-Documentation-a73b9c46d24b481eb0fd06ea8fa57f69
Invariant example: https://github.com/PwnedNoMore/pnm-examples

We are constantly studying and adding past hacks into reusable Templates.
You can also use `pnm template` to check and install available templates.
```


### pnm test

Use the `pnm test` subcommand to run [PNM invariant and property tests](https://pwned-no-more.notion.site/Property-test-and-invariant-test-c6b80f6b6136408ba41247c0be561fe2) for your project.

It will compile your project and run the tests, so you don't have to compile it manually.

#### Example
To initialize your PNM project, run:
```shell
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
• DepositWithdrawalFailureTest
• UnboundedProfitTest
• UnprotectedOwnershipTest

To install a template, run `pnm template --install <template-name>`
```

To install the `FundLossTest` template, run:

```shell
$ pnm template --install FundLossTest
Installing template: [FundLossTest]
Installed template: [FundLossTest] to [test/pnm/FundLossTest_1671118266.sol].
```

### CLI Data Collection and Metrics
PNM collects usage data and metrics to help improve PNM CLI. 
We collect anonymous information related to the use of the CLI and plug-ins, such as which commands and parameters were run, and performance and error data. 
If you would prefer to opt out of metrics upload, you can run: 
```shell
touch ~/.pnm/.metrics_disabled
``` 
or 
set the environment variable `PNM_METRICS_DISABLED` to `true` by run:
```shell
export PNM_METRICS_DISABLED=true
```


### Support

If you encounter any issues, have questions about using PNM CLI, or any feedback,
please contact us in our Discord server. We will be happy to assist you.
