# Introduction

This is documentation that provides you a step-by-step guide on how to generate Contract Address.

# Step by step

## Step-1 Build Plutus Script / UPLC

First, you must build or compile the Validator Script into Plutus Script or UPLC. The following is the [documentation](https://github.com/ValdryanIvandito/cardano-script-compiling-guide). There are PlutusTx and Aiken Validator Scripts; you can choose one of them. After you build or compile the script, then go to the output directory.

## Step-2 Initiate Cardano Network (Optional)

**_Hint: If you have choosen the network, you can skip this step_**

```bash
network="testnet-magic 1"
```

_or_

```bash
network="testnet-magic 2"
```

_or_

```bash
network="mainnet"
```

**The following is a table regarding the network on Cardano**
| cli Parameter | Network Name |
|---------|---------|
| testnet-magic 1 | Preprod |
| testnet-magic 2 | Preview |
| mainnet | Mainnet |

## Step-3 Create Contract Address

```bash
cardano-cli address build \
--payment-script-file always-succeeds.plutus \
--out-file contract.addr \
--$network
```

**_Note: In this example, we use 'always-succeeds.plutus' script in accordance with this [documentation](https://github.com/ValdryanIvandito/cardano-script-compiling-guide). However, the script file name can be anything._**

### Display The Contract Address

```bash
contractAddress=$(cat contract.addr)
echo $contractAddress
```

### Display Information About the Contract Address UTxO (Check Balance)

```bash
cardano-cli query utxo \
--address $contractAddress \
--$network
```

# Demo

The following is a video recorded by the Indonesian Cardano Developers Community where I demonstrated the steps above. Watch the recorded video at timestamp **_1:27:27_**, here is the [link](https://youtu.be/03hXLZ_07N0?list=PLUj8499OocHiL8gXPv8wMlLW-zIcyYdrQ)

# References

[Gimbalabs PPBL2023 Module 102.2: Build an Address](https://plutuspbl.io/modules/102/1022)
