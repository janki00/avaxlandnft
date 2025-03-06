# avaxlandnftnpm install --save-dev hardhat @nomicfoundation/hardhat-toolbox @nomiclabs/hardhat-verify dotenv
import { HardhatUserConfig } from "hardhat/config";
import "@nomicfoundation/hardhat-toolbox";
import "@nomiclabs/hardhat-verify";
import dotenv from "dotenv";

dotenv.config();

const config: HardhatUserConfig = {
  etherscan: {
    apiKey: {
      snowtrace: "verifyContract", // Placeholder, API key might not be needed for Snowtrace
    },
    customChains: [
      {
        network: "snowtrace",
        chainId: 43114,
        urls: {
          apiURL: "https://api.routescan.io/v2/network/mainnet/evm/43114/etherscan",
          browserURL: "https://avalanche.routescan.io",
        },
      },
    ],
  },
  networks: {
    snowtrace: {
      url: "https://api.avax.network/ext/bc/C/rpc",
      accounts: [process.env.PRIVATE_KEY],
    },
  },
};

export default config;
