# Hyper SDK Custom VM

## Overview

This project guides you through the process of setting up and operating a HyperChain on the Avalanche network. It offers a clear and efficient method to initialize, configure, and engage with your own HyperChain environment.

## Getting Started

### Normalize Dependencies

Execute the following command within your project directory to synchronize all dependencies:

```bash
go mod tidy
```

### Configure Project Constants

Modify the `consts/consts.go` file by completing the necessary constants:

```go
const (
    HRP    = "mandhartoken"
    Name   = "mandharchain"
    Symbol = "MDH"
)
```

### Register Actions

Navigate to `registry/registry.go` and register the `CreateAsset` and `MintAsset` actions as shown below:

```go
consts.ActionRegistry.Register(&actions.CreateAsset{}, actions.UnmarshalCreateAsset, false)
consts.ActionRegistry.Register(&actions.MintAsset{}, actions.UnmarshalMintAsset, false)
```

### Run the VM Locally

Ensure that Go is included in your system's PATH. If it isn't, add it by running one of the following commands:

```bash
export PATH=$PATH:$(go env GOPATH)/bin
# OR
export PATH=$PATH:/usr/local/go/bin
```

After setting up the PATH, execute these commands to run the VM:

```bash
MODE="run-single" ./scripts/run.sh
./scripts/build.sh
```

### Load Demo Private Key

Import the demo private key provided in the project with the following commands:

```bash
./build/token-cli key import demo.pk
./build/token-cli chain import-anr
```

### Interact with Your HyperChain

#### Mint and Trade

##### Create Your Asset

Run the command below to create a new asset on your HyperChain:

```bash
./build/token-cli action create-asset
```

##### Mint Your Asset

Use the following command to mint your newly created asset:

```bash
./build/token-cli action mint-asset
```

##### View Your Balance

Check your token balance with this command:

```bash
./build/token-cli key balance
```

### Close Your Local Avalanche Network

To terminate the local Avalanche network, execute:

```bash
killall avalanche-network-runner
```

## Help

Should you encounter any problems, consult the README file or execute the relevant helper command for assistance.

## License

This project is distributed under the MIT License. For more details, refer to the [LICENSE](LICENSE) file.
