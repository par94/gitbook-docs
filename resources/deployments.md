# Deployments

## Contract Deployments

A full list of deployed contracts can be found in the [deployments.json](https://github.com/connext/monorepo/blob/main/packages/deployments/contracts/deployments.json) file. This contains deployments for all environments and is difficult to parse through manually. You should only need to reference it for automation or as a source of truth. For convenience, we extracted the important contract addresses and listed them here.

## Mainnet Contracts

### Ethereum

> Domain ID: 6648936

> Chain ID: 1

| Core Contract                                                                                    | Address                                    |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------ |
| [Connext](https://louper.dev/diamond/0x8898B472C54c31894e3B9bb83cEA802a5d0e63C6?network=mainnet) | 0x8898B472C54c31894e3B9bb83cEA802a5d0e63C6 |

| Asset Contract                                                                  | Address                                    | Flavor    |
| ------------------------------------------------------------------------------- | ------------------------------------------ | --------- |
| [NEXT](https://etherscan.io/token/0xFE67A4450907459c3e1FFf623aA927dD4e28c67a)   | 0xFE67A4450907459c3e1FFf623aA927dD4e28c67a | Canonical |
| [USDC](https://etherscan.io/address/0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48) | 0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48 | Canonical |
| [WETH](https://etherscan.io/address/0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2) | 0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2 | Canonical |
| [DAI](https://etherscan.io/address/0x6b175474e89094c44da98b954eedeac495271d0f)  | 0x6B175474E89094C44Da98b954EedeAC495271d0F | Canonical |
| [USDT](https://etherscan.io/address/0xdac17f958d2ee523a2206206994597c13d831ec7) | 0xdAC17F958D2ee523a2206206994597C13D831ec7 | Canonical |

| Peripheral Contract                                                                  | Address                                    | Description    |
| ------------------------------------------------------------------------------------ | ------------------------------------------ | -------------- |
| [Unwrapper](https://etherscan.io/address/0x268682b7D9992aE7e2ca4A8bCc9D9655FB06056F) | 0x268682b7D9992aE7e2ca4A8bCc9D9655FB06056F | WETH Unwrapper |

### Optimism

> Domain ID: 1869640809

> Chain ID: 10

| Core Contract                                                                                     | Address                                    |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| [Connext](https://louper.dev/diamond/0x8f7492DE823025b4CfaAB1D34c58963F2af5DEDA?network=optimism) | 0x8f7492DE823025b4CfaAB1D34c58963F2af5DEDA |

| Asset Contract                                                                                  | Address                                    | Flavor        |
| ----------------------------------------------------------------------------------------------- | ------------------------------------------ | ------------- |
| [NEXT](https://optimistic.etherscan.io/address/0x58b9cB810A68a7f3e1E4f8Cb45D1B9B3c79705E8#code) | 0x58b9cB810A68a7f3e1E4f8Cb45D1B9B3c79705E8 | Local/Adopted |
| [nextUSDC](https://optimistic.etherscan.io/address/0x67E51f46e8e14D4E4cab9dF48c59ad8F512486DD)  | 0x67E51f46e8e14D4E4cab9dF48c59ad8F512486DD | Local         |
| [USDC](https://optimistic.etherscan.io/address/0x7F5c764cBc14f9669B88837ca1490cCa17c31607)      | 0x7F5c764cBc14f9669B88837ca1490cCa17c31607 | Adopted       |
| [nextWETH](https://optimistic.etherscan.io/address/0xbAD5B3c68F855EaEcE68203312Fd88AD3D365e50)  | 0xbAD5B3c68F855EaEcE68203312Fd88AD3D365e50 | Local         |
| [WETH](https://optimistic.etherscan.io/address/0x4200000000000000000000000000000000000006)      | 0x4200000000000000000000000000000000000006 | Adopted       |
| [nextDAI](https://optimistic.etherscan.io/address/0xd64Bd028b560bbFc732eA18f282c64B86F3468e0)   | 0xd64Bd028b560bbFc732eA18f282c64B86F3468e0 | Local         |
| [DAI](https://optimistic.etherscan.io/address/0xDA10009cBd5D07dd0CeCc66161FC93D7c9000da1)       | 0xDA10009cBd5D07dd0CeCc66161FC93D7c9000da1 | Adopted       |
| [nextUSDT](https://optimistic.etherscan.io/address/0x4cBB28FA12264cD8E87C62F4E1d9f5955Ce67D20)  | 0x4cBB28FA12264cD8E87C62F4E1d9f5955Ce67D20 | Local         |
| [USDT](https://optimistic.etherscan.io/address/0x94b008aA00579c1307B0EF2c499aD98a8ce58e58)      | 0x94b008aA00579c1307B0EF2c499aD98a8ce58e58 | Adopted       |

| Peripheral Contract                                                                             | Address                                    | Description    |
| ----------------------------------------------------------------------------------------------- | ------------------------------------------ | -------------- |
| [Unwrapper](https://optimistic.etherscan.io/address/0x7Fe09d217d646a6213e51b237670Bc326188cB93) | 0x7Fe09d217d646a6213e51b237670Bc326188cB93 | WETH Unwrapper |

### Polygon

> Domain ID: 1886350457

> Chain ID: 137

| Core Contract                                                                                    | Address                                    |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------ |
| [Connext](https://louper.dev/diamond/0x11984dc4465481512eb5b777E44061C158CF2259?network=polygon) | 0x11984dc4465481512eb5b777E44061C158CF2259 |

| Asset Contract                                                                         | Address                                    | Flavor        |
| -------------------------------------------------------------------------------------- | ------------------------------------------ | ------------- |
| [NEXT](https://polygonscan.com/address/0x58b9cB810A68a7f3e1E4f8Cb45D1B9B3c79705E8)     | 0x58b9cB810A68a7f3e1E4f8Cb45D1B9B3c79705E8 | Local/Adopted |
| [nextUSDC](https://polygonscan.com/address/0xF96C6d2537e1af1a9503852eB2A4AF264272a5B6) | 0xF96C6d2537e1af1a9503852eB2A4AF264272a5B6 | Local         |
| [USDC](https://polygonscan.com/address/0x2791Bca1f2de4661ED88A30C99A7a9449Aa84174)     | 0x2791Bca1f2de4661ED88A30C99A7a9449Aa84174 | Adopted       |
| [nextWETH](https://polygonscan.com/address/0x4b8BaC8Dd1CAA52E32C07755c17eFadeD6A0bbD0) | 0x4b8BaC8Dd1CAA52E32C07755c17eFadeD6A0bbD0 | Local         |
| [WETH](https://polygonscan.com/address/0x7ceB23fD6bC0adD59E62ac25578270cFf1b9f619)     | 0x7ceB23fD6bC0adD59E62ac25578270cFf1b9f619 | Adopted       |
| [nextDAI](https://polygonscan.com/address/0xaDCe87b14d570665222C1172D18a221BF7690d5a)  | 0xaDCe87b14d570665222C1172D18a221BF7690d5a | Local         |
| [DAI](https://polygonscan.com/address/0x8f3Cf7ad23Cd3CaDbD9735AFf958023239c6A063)      | 0x8f3Cf7ad23Cd3CaDbD9735AFf958023239c6A063 | Adopted       |
| [nextUSDT](https://polygonscan.com/address/0xE221C5A2a8348f12dcb2b0e88693522EbAD2690f) | 0xE221C5A2a8348f12dcb2b0e88693522EbAD2690f | Local         |
| [USDT](https://polygonscan.com/address/0xc2132D05D31c914a87C6611C10748AEb04B58e8F)     | 0xc2132D05D31c914a87C6611C10748AEb04B58e8F | Adopted       |

| Peripheral Contract                                                                     | Address                                    | Description    |
| --------------------------------------------------------------------------------------- | ------------------------------------------ | -------------- |
| [Unwrapper](https://polygonscan.com/address/0x7E8F8B2dA3dc5Ad9c9Dfd1A832331A039d4f3f74) | 0x7E8F8B2dA3dc5Ad9c9Dfd1A832331A039d4f3f74 | WETH Unwrapper |

### Arbitrum One

> Domain ID: 1634886255

> Chain ID: 42161

| Core Contract                                                                                     | Address                                    |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| [Connext](https://louper.dev/diamond/0xEE9deC2712cCE65174B561151701Bf54b99C24C8?network=arbitrum) | 0xEE9deC2712cCE65174B561151701Bf54b99C24C8 |

| Asset Contract                                                                     | Address                                    | Flavor        |
| ---------------------------------------------------------------------------------- | ------------------------------------------ | ------------- |
| [NEXT](https://arbiscan.io/address/0x58b9cB810A68a7f3e1E4f8Cb45D1B9B3c79705E8)     | 0x58b9cB810A68a7f3e1E4f8Cb45D1B9B3c79705E8 | Local/Adopted |
| [nextUSDC](https://arbiscan.io/address/0x8c556cF37faa0eeDAC7aE665f1Bb0FbD4b2eae36) | 0x8c556cF37faa0eeDAC7aE665f1Bb0FbD4b2eae36 | Local         |
| [USDC](https://arbiscan.io/address/0xFF970A61A04b1cA14834A43f5dE4533eBDDB5CC8)     | 0xFF970A61A04b1cA14834A43f5dE4533eBDDB5CC8 | Adopted       |
| [nextWETH](https://arbiscan.io/address/0x2983bf5c334743Aa6657AD70A55041d720d225dB) | 0x2983bf5c334743Aa6657AD70A55041d720d225dB | Local         |
| [WETH](https://arbiscan.io/address/0x82aF49447D8a07e3bd95BD0d56f35241523fBab1)     | 0x82aF49447D8a07e3bd95BD0d56f35241523fBab1 | Adopted       |
| [nextDAI](https://arbiscan.io/address/0xfDe99b3B3fbB69553D7DaE105EF34Ba4FE971190)  | 0xfDe99b3B3fbB69553D7DaE105EF34Ba4FE971190 | Local         |
| [DAI](https://arbiscan.io/address/0xDA10009cBd5D07dd0CeCc66161FC93D7c9000da1)      | 0xDA10009cBd5D07dd0CeCc66161FC93D7c9000da1 | Adopted       |
| [nextUSDT](https://arbiscan.io/address/0x2fD7E61033b3904c65AA9A9B83DCd344Fa19Ffd2) | 0x2fD7E61033b3904c65AA9A9B83DCd344Fa19Ffd2 | Local         |
| [USDT](https://arbiscan.io/address/0xFd086bC7CD5C481DCC9C85ebE478A1C0b69FCbb9)     | 0xFd086bC7CD5C481DCC9C85ebE478A1C0b69FCbb9 | Adopted       |

| Peripheral Contract                                                                 | Address                                    | Description    |
| ----------------------------------------------------------------------------------- | ------------------------------------------ | -------------- |
| [Unwrapper](https://arbiscan.io/address/0x429b9eb01362b2799131EfCC44319689b662999D) | 0x429b9eb01362b2799131EfCC44319689b662999D | WETH Unwrapper |

### Binance Smart Chain

> Domain ID: 6450786

> Chain ID: 56

| Core Contract                                                                                    | Address                                    |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------ |
| [Connext](https://louper.dev/diamond/0xCd401c10afa37d641d2F594852DA94C700e4F2CE?network=binance) | 0xCd401c10afa37d641d2F594852DA94C700e4F2CE |

| Asset Contract                                                                     | Address                                    | Flavor        |
| ---------------------------------------------------------------------------------- | ------------------------------------------ | ------------- |
| [NEXT](https://bscscan.com/address/0x58b9cB810A68a7f3e1E4f8Cb45D1B9B3c79705E8)     | 0x58b9cB810A68a7f3e1E4f8Cb45D1B9B3c79705E8 | Local/Adopted |
| [nextUSDC](https://bscscan.com/address/0x5e7D83dA751F4C9694b13aF351B30aC108f32C38) | 0x5e7D83dA751F4C9694b13aF351B30aC108f32C38 | Local         |
| [USDC](https://bscscan.com/address/0x8AC76a51cc950d9822D68b83fE1Ad97B32Cd580d)     | 0x8AC76a51cc950d9822D68b83fE1Ad97B32Cd580d | Adopted       |
| [nextWETH](https://bscscan.com/address/0xA9CB51C666D2AF451d87442Be50747B31BB7d805) | 0xA9CB51C666D2AF451d87442Be50747B31BB7d805 | Local         |
| [WETH](https://bscscan.com/address/0x2170Ed0880ac9A755fd29B2688956BD959F933F8)     | 0x2170Ed0880ac9A755fd29B2688956BD959F933F8 | Adopted       |
| [nextDAI](https://bscscan.com/address/0x86a343BCF17D79C475d300eed35F0145F137D0c9)  | 0x86a343BCF17D79C475d300eed35F0145F137D0c9 | Local         |
| [DAI](https://bscscan.com/address/0x1AF3F329e8BE154074D8769D1FFa4eE058B1DBc3)      | 0x1AF3F329e8BE154074D8769D1FFa4eE058B1DBc3 | Adopted       |
| [nextUSDT](https://bscscan.com/address/0xD609f26B5547d5E31562B29150769Cb7c774B97a) | 0xD609f26B5547d5E31562B29150769Cb7c774B97a | Local         |
| [USDT](https://bscscan.com/address/0x55d398326f99059fF775485246999027B3197955)     | 0x55d398326f99059fF775485246999027B3197955 | Adopted       |

| Peripheral Contract                                                                 | Address                                    | Description    |
| ----------------------------------------------------------------------------------- | ------------------------------------------ | -------------- |
| [Unwrapper](https://bscscan.com/address/0x2c7B8c1a13F2a7854B9299E4d22809A8B1E05De5) | 0x2c7B8c1a13F2a7854B9299E4d22809A8B1E05De5 | WETH Unwrapper |

### Gnosis

> Domain ID: 6778479

> Chain ID: 100

| Core Contract                                                                                 | Address                                    |
| --------------------------------------------------------------------------------------------- | ------------------------------------------ |
| [Connext](https://louper.dev/diamond/0x5bB83e95f63217CDa6aE3D181BA580Ef377D2109?network=xdai) | 0x5bB83e95f63217CDa6aE3D181BA580Ef377D2109 |

| Asset Contract                                                                       | Address                                    | Flavor        |
| ------------------------------------------------------------------------------------ | ------------------------------------------ | ------------- |
| [NEXT](https://gnosisscan.io/address/0x58b9cb810a68a7f3e1e4f8cb45d1b9b3c79705e8)     | 0x58b9cB810A68a7f3e1E4f8Cb45D1B9B3c79705E8 | Local/Adopted |
| [nextUSDC](https://gnosisscan.io/address/0x44CF74238d840a5fEBB0eAa089D05b763B73faB8) | 0x44CF74238d840a5fEBB0eAa089D05b763B73faB8 | Local         |
| [USDC](https://gnosisscan.io/address/0xDDAfbb505ad214D7b80b1f830fcCc89B60fb7A83)     | 0xDDAfbb505ad214D7b80b1f830fcCc89B60fb7A83 | Adopted       |
| [nextWETH](https://gnosisscan.io/address/0x538E2dDbfDf476D24cCb1477A518A82C9EA81326) | 0x538E2dDbfDf476D24cCb1477A518A82C9EA81326 | Local         |
| [WETH](https://gnosisscan.io/address/0x6A023CCd1ff6F2045C3309768eAd9E68F978f6e1)     | 0x6A023CCd1ff6F2045C3309768eAd9E68F978f6e1 | Adopted       |
| [nextDAI](https://gnosisscan.io/address/0x0e1D5Bcd2Ac5CF2f71841A9667afC1E995CaAf4F)  | 0x0e1D5Bcd2Ac5CF2f71841A9667afC1E995CaAf4F | Local         |
| [DAI](https://gnosisscan.io/address/0xe91D153E0b41518A2Ce8Dd3D7944Fa863463a97d)      | 0xe91D153E0b41518A2Ce8Dd3D7944Fa863463a97d | Adopted       |
| [nextUSDT](https://gnosisscan.io/address/0xF4d944883D6FddC56d3534986feF82105CaDbfA1) | 0xF4d944883D6FddC56d3534986feF82105CaDbfA1 | Local         |
| [USDT](https://gnosisscan.io/address/0x4ECaBa5870353805a9F068101A40E0f32ed605C6)     | 0x4ECaBa5870353805a9F068101A40E0f32ed605C6 | Adopted       |

| Peripheral Contract                                                                   | Address                                    | Description    |
| ------------------------------------------------------------------------------------- | ------------------------------------------ | -------------- |
| [Unwrapper](https://gnosisscan.io/address/0x642c27a96dFFB6f21443A89b789a3194Ff8399fa) | 0x642c27a96dFFB6f21443A89b789a3194Ff8399fa | WETH Unwrapper |

## Testnet Contracts

Note that the Test Token is a mintable ERC20. The open `mint` function has the signature `mint(address account, uint256 amount)` and can be freely called.

### Goerli

> Domain ID: 1735353714

> Chain ID: 5

| Core Contract                                                                                   | Address                                    |
| ----------------------------------------------------------------------------------------------- | ------------------------------------------ |
| [Connext](https://louper.dev/diamond/0xFCa08024A6D4bCc87275b1E4A1E22B71fAD7f649?network=goerli) | 0xFCa08024A6D4bCc87275b1E4A1E22B71fAD7f649 |

| Asset Contract                                                                         | Address                                    | Flavor    |
| -------------------------------------------------------------------------------------- | ------------------------------------------ | --------- |
| [TEST](https://goerli.etherscan.io/address/0x7ea6eA49B0b0Ae9c5db7907d139D9Cd3439862a1) | 0x7ea6eA49B0b0Ae9c5db7907d139D9Cd3439862a1 | Canonical |
| [WETH](https://goerli.etherscan.io/address/0xB4FBF271143F4FBf7B91A5ded31805e42b2208d6) | 0xB4FBF271143F4FBf7B91A5ded31805e42b2208d6 | Canonical |

| Peripheral Contract                                                                         | Address                                    | Description    |
| ------------------------------------------------------------------------------------------- | ------------------------------------------ | -------------- |
| [Unwrapper](https://goerli.etherscan.io/address/0xa6633d369A9C4C8A442ef104E8e293DA7b352Acd) | 0xa6633d369A9C4C8A442ef104E8e293DA7b352Acd | WETH Unwrapper |

### Optimism-Goerli

> Domain ID: 1735356532

> Chain ID: 420

| Core Contract                                                                                             | Address                                    |
| --------------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| [Connext](https://louper.dev/diamond/0x5Ea1bb242326044699C3d81341c5f535d5Af1504?network=optimism\_goerli) | 0x5Ea1bb242326044699C3d81341c5f535d5Af1504 |

| Asset Contract                                                                                      | Address                                    | Flavor        |
| --------------------------------------------------------------------------------------------------- | ------------------------------------------ | ------------- |
| [TEST](https://goerli-optimism.etherscan.io/address/0x68db1c8d85c09d546097c65ec7dcbff4d6497cbf)     | 0x68Db1c8d85C09d546097C65ec7DCBFF4D6497CbF | Local/Adopted |
| [nextWETH](https://goerli-optimism.etherscan.io/address/0x39b061b7e41de8b721f9aeceb6b3f17ecb7ba63e) | 0x39B061B7e41DE8B721f9aEcEB6b3f17ECB7ba63E | Local         |
| [WETH](https://goerli-optimism.etherscan.io/address/0x74c6FD7D2Bc6a8F0Ebd7D78321A95471b8C2B806)     | 0x74c6FD7D2Bc6a8F0Ebd7D78321A95471b8C2B806 | Adopted       |

| Peripheral Contract                                                                                  | Address                                    | Description    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------ | -------------- |
| [Unwrapper](https://goerli-optimism.etherscan.io/address/0x08bDeFD0e4878A814Cb2fd11C033F3947251689f) | 0x08bDeFD0e4878A814Cb2fd11C033F3947251689f | WETH Unwrapper |

### Mumbai

> Domain ID: 9991

> Chain ID: 80001

| Core Contract                                                                                   | Address                                    |
| ----------------------------------------------------------------------------------------------- | ------------------------------------------ |
| [Connext](https://louper.dev/diamond/0x2334937846Ab2A3FCE747b32587e1A1A2f6EEC5a?network=mumbai) | 0x2334937846Ab2A3FCE747b32587e1A1A2f6EEC5a |

| Asset Contract                                                                                | Address                                    | Flavor        |
| --------------------------------------------------------------------------------------------- | ------------------------------------------ | ------------- |
| [TEST](https://mumbai.polygonscan.com/address/0xeDb95D8037f769B72AAab41deeC92903A98C9E16)     | 0xeDb95D8037f769B72AAab41deeC92903A98C9E16 | Local/Adopted |
| [nextWETH](https://mumbai.polygonscan.com/address/0x1E5341E4b7ed5D0680d9066aac0396F0b1bD1E69) | 0x1E5341E4b7ed5D0680d9066aac0396F0b1bD1E69 | Local         |
| [WETH](https://mumbai.polygonscan.com/address/0xFD2AB41e083c75085807c4A65C0A14FDD93d55A9)     | 0xFD2AB41e083c75085807c4A65C0A14FDD93d55A9 | Adopted       |

| Peripheral Contract                                                                            | Address                                    | Description    |
| ---------------------------------------------------------------------------------------------- | ------------------------------------------ | -------------- |
| [Unwrapper](https://mumbai.polygonscan.com/address/0x1e0Db00EB08ceC7FFdA03c0Dbf224193E1563844) | 0x1e0Db00EB08ceC7FFdA03c0Dbf224193E1563844 | WETH Unwrapper |

### Arbitrum-Goerli

> Domain ID: 1734439522

> Chain ID: 421613

| Core Contract                                                                                             | Address                                    |
| --------------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| [Connext](https://louper.dev/diamond/0x2075c9E31f973bb53CAE5BAC36a8eeB4B082ADC2?network=arbitrum\_goerli) | 0x2075c9E31f973bb53CAE5BAC36a8eeB4B082ADC2 |

| Asset Contract                                                                        | Address                                    | Flavor        |
| ------------------------------------------------------------------------------------- | ------------------------------------------ | ------------- |
| [TEST](https://goerli.arbiscan.io/address/0xDC805eAaaBd6F68904cA706C221c72F8a8a68F9f) | 0xDC805eAaaBd6F68904cA706C221c72F8a8a68F9f | Local/Adopted |
| [WETH](https://goerli.arbiscan.io/address/0x1346786E6A5e07b90184a1Ba58E55444b99DC4A2) | 0x1346786E6A5e07b90184a1Ba58E55444b99DC4A2 | Local/Adopted |

| Peripheral Contract                                                                        | Address                                    | Description    |
| ------------------------------------------------------------------------------------------ | ------------------------------------------ | -------------- |
| [Unwrapper](https://goerli.arbiscan.io/address/0x18BBF96BC8014aA93cbf1A5Bce005a485b5C2C4a) | 0x18BBF96BC8014aA93cbf1A5Bce005a485b5C2C4a | WETH Unwrapper |

### zkSync Era Testnet

> Domain ID: 2053862260

> Chain ID: 280

| Core Contract                                                                                   | Address                                    |
| ----------------------------------------------------------------------------------------------- | ------------------------------------------ |
| [Connext](https://goerli.explorer.zksync.io/address/0xB0694fEcEdd88e5590A563aDb5f194d2dE30F0b6) | 0xB0694fEcEdd88e5590A563aDb5f194d2dE30F0b6 |

| Asset Contract                                                                               | Address                                    | Flavor        |
| -------------------------------------------------------------------------------------------- | ------------------------------------------ | ------------- |
| [TEST](https://goerli.explorer.zksync.io/address/0x7C1412e456ad60B8ee458c4eb3A9852C3e389353) | 0x7C1412e456ad60B8ee458c4eb3A9852C3e389353 | Local/Adopted |

| Peripheral Contract | Address | Description |
| ------------------- | ------- | ----------- |
| Unwrapper           | TBD     | TBD         |

### Linea Testnet

> Domain ID: 1668247156

> Chain ID: 59140

| Core Contract                                                                                             | Address                                    |
| --------------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| [Connext](https://explorer.goerli.zkevm.consensys.net/address/0xfdb6B853C1945Dbffe78A3091BeBB9A928234fA3) | 0xfdb6B853C1945Dbffe78A3091BeBB9A928234fA3 |

| Asset Contract                                                                                         | Address                                    | Flavor        |
| ------------------------------------------------------------------------------------------------------ | ------------------------------------------ | ------------- |
| [TEST](https://explorer.goerli.zkevm.consensys.net/address/0xB706319D37b945727E71ae0d4353699d19112576) | 0xB706319D37b945727E71ae0d4353699d19112576 | Local/Adopted |

| Peripheral Contract | Address | Description |
| ------------------- | ------- | ----------- |
| Unwrapper           | TBD     | TBD         |

### Polygon zkEVM Testnet

> Domain ID: 1887071092

> Chain ID: 1442

| Core Contract                                                                                       | Address                                    |
| --------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| [Connext](https://testnet-zkevm.polygonscan.com/address/0x20b4789065DE09c71848b9A4FcAABB2c10006FA2) | 0x20b4789065DE09c71848b9A4FcAABB2c10006FA2 |

| Asset Contract                                                                                   | Address                                    | Flavor        |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------ | ------------- |
| [TEST](https://testnet-zkevm.polygonscan.com/address/0x5f921E4DE609472632CEFc72a3846eCcfbed4ed8) | 0x5f921E4DE609472632CEFc72a3846eCcfbed4ed8 | Local/Adopted |

| Peripheral Contract | Address | Description |
| ------------------- | ------- | ----------- |
| Unwrapper           | TBD     | TBD         |

## Offchain Agents

### Sequencer

Example endpoints can be found [here](https://github.com/connext/monorepo/blob/c694958e51b9f81cc100260d0776788276303087/packages/agents/sequencer/example.http#L15). For instance, you can check for queued transactions:

[https://sequencer.testnet.connext.ninja/queued](https://sequencer.testnet.connext.ninja/queued)

### Cartographer

The Cartographer is a Connext-hosted service that stores transfer data to a persistent datastore. The data schema is bespoke for Connext cross-chain transfers and a REST API is available for retrieving details like transfer status, transfer history by user, and more.

Example endpoints can be found [here](https://github.com/connext/monorepo/blob/c694958e51b9f81cc100260d0776788276303087/packages/agents/cartographer/api/example.http). For instance, you can query for all transfers:

[https://postgrest.testnet.connext.ninja/transfers](https://postgrest.testnet.connext.ninja/transfers)

## User Interfaces

### Bridge UI

A bridge UI where users can transfer assets across domains. Here you can also mint `TEST` tokens with the faucet.

[https://amarok-testnet.coinhippo.io](https://amarok-testnet.coinhippo.io)

### Connextscan

This is the testnet scanner site where you can track the status of transfers by `transferId`.

[https://testnet.amarok.connextscan.io](https://testnet.amarok.connextscan.io)
