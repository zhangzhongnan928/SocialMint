# SocialMint

🌟 Transform meme on social platforms into tradeable tokens. SocialMint is a decentralized platform that enables anyone to create, trade, and earn from social-backed meme coins.

# User Stories for SocialMint

## User Story 1: Creating a Meme Coin for Another User (Elon Musk)

*As a Twitter user (**User A**), I want to create a meme coin based on Elon Musk's tweet, designating him as the fee recipient, so that the community can trade it and both Elon and I can earn fees from its trading activity, understanding that a 50% fee will be deducted when we claim our shares.*

### Steps

1. **Discovery**:
   - User A notices that Elon Musk has posted an interesting meme on Twitter.

2. **Initiation**:
   - User A replies to or quotes Elon's tweet, mentioning our Twitter bot (`@OurTwitterBot`), and includes the following details:
     - **Name**: `[Inputted Coin Name]`
     - **Symbol**: `[Inputted Coin Symbol]`
     - **Fee Recipient Twitter ID**: `@elonmusk`
     - **Description**: `[Inputted Description]`
     - **Meme Content**: Includes the meme picture or video (can use the same as in Elon's tweet).

3. **Processing**:
   - Our server receives the tweet and initiates a transaction to the Wow.xyz/Moonshot contract to mint the meme coin.
   - During the minting transaction, the fee distribution parameters are set as follows:

     ```plaintext
     TOTAL_FEE_BPS = 100       // 1% total fee on transactions
     TOKEN_CREATOR_FEE_BPS = 5000  // 50% of TOTAL_FEE_BPS (shared by Elon and us when Elon claims)
     PROTOCOL_FEE_BPS = 2000       // 20% of TOTAL_FEE_BPS (earned by Wow.xyz)
     PLATFORM_REFERRER_FEE_BPS = 1500  // 15% of TOTAL_FEE_BPS (shared by User A and us when User A claims fees)
     ORDER_REFERRER_FEE_BPS = 1500     // 15% of TOTAL_FEE_BPS (earned by the ORDER_REFERRER set by traders)
     ```

   - The minting uses a multisignature wallet with two signers:
     - One controlled by us.
     - One controlled by a smart contract operable by any wallet with the correct Twitter ID attestation.

4. **Confirmation**:
   - The meme coin is successfully launched.
   - Our Twitter bot replies to User A's tweet with a confirmation message and a tapp link (**TLink**) to our landing page.

5. **Accessibility**:
   - User A, Elon, and the public can view the meme coin details on Twitter.
   - The coin becomes available for trading on platforms like Wow.xyz, Moonshot, and Uniswap.

6. **Engagement via TLink**:
   - When users click the TLink, they are directed to our landing page:
     - **For Elon**:
       - He can verify ownership of his Twitter ID.
       - Upon verification, he can claim his share of the fees and the Twitter ID-related meme coins, transferring them to his own wallet.
     - **For User A**:
       - User A can verify ownership of his Twitter ID.
       - Upon verification, he can claim his share of the fees (from the `PLATFORM_REFERRER_FEE_BPS`) and any associated meme coins.
     - **For Others**:
       - They can proceed to trade the meme coin on third-party platforms.

7. **Fee Claiming Process**:
   - **For Elon**:
     - When he claims his fees, a **50% fee** is deducted from his share.
     - He is required to pay an extra amount in **$SLN tokens** to process the claim.
   - **For User A**:
     - When User A claims his share of the fees, a **50% fee** is also deducted.
     - He must pay an extra amount in **$SLN tokens** to process the claim.

8. **Fee Distribution Breakdown**:
   - **Total Trading Volume Fee**: 1% of all transactions involving the meme coin.

   - **Elon's Share**:
     - Before deduction: `1% * 50% = 0.5%` of total trading volume.
     - After 50% deduction: `0.5% * 50% = 0.25%` of total trading volume.

   - **User A's Share**:
     - Before deduction: `1% * 15% = 0.15%` of total trading volume.
     - After 50% deduction: `0.15% * 50% = 0.075%` of total trading volume.

   - **Our (Platform's) Earnings**:
     - From Elon's claim: `0.5% * 50% = 0.25%` (deducted portion of Elon's share).
     - From User A's claim: `0.15% * 50% = 0.075%` (deducted portion of User A's share).
     - **Total Platform Earnings**: `0.25% + 0.075% = 0.325%` of total trading volume.

   - **Wow.xyz/Moonshot's Share**:
     - `PROTOCOL_FEE_BPS`: `1% * 20% = 0.2%` of total trading volume.

   - **ORDER_REFERRER_FEE_BPS**:
     - `1% * 15% = 0.15%` of total trading volume.
     - Earned by the `ORDER_REFERRER` set by traders during each transaction.

   - **Total Allocated Fees**:
     - Elon's net earnings: **0.25%**
     - User A's net earnings: **0.075%**
     - Our earnings: **0.325%**
     - Wow.xyz/Moonshot's earnings: **0.2%**
     - `ORDER_REFERRER_FEE_BPS`: **0.15%**
     - **Total**: **1%** (matches the `TOTAL_FEE_BPS`)

9. **Finalization**:
   - Once Elon and User A have claimed their fees and tokens, the meme coin is officially linked to Elon and User A, potentially increasing its value and legitimacy.
   - Leaderboards and statistics on our platform showcase earnings, trading volumes, and enhance visibility.

---

## User Story 2: Creating a Meme Coin for Personal Benefit

*As a Twitter user (**User A**), I want to create a meme coin and set myself as the fee recipient, so that I can earn fees directly from its trading activity, understanding that a 50% fee will be deducted when I claim my share.*

### Steps

1. **Initiation**:
   - User A decides to create a meme coin.
   - He composes a tweet mentioning our Twitter bot (`@OurTwitterBot`) with the following details:
     - **Name**: `[Inputted Coin Name]`
     - **Symbol**: `[Inputted Coin Symbol]`
     - **Fee Recipient Twitter ID**: `@UserA` (his own Twitter handle)
     - **Description**: `[Inputted Description]`
     - **Meme Content**: Includes the meme picture or video.

2. **Processing**:
   - Our server processes the request and mints the meme coin via the Wow.xyz/Moonshot contract.
   - The fee distribution parameters are set as:

     ```plaintext
     TOTAL_FEE_BPS = 100       // 1% total fee on transactions
     TOKEN_CREATOR_FEE_BPS = 5000  // 50% of TOTAL_FEE_BPS (shared by User A and us when User A claims)
     PROTOCOL_FEE_BPS = 2000       // 20% of TOTAL_FEE_BPS (earned by Wow.xyz)
     PLATFORM_REFERRER_FEE_BPS = 1500  // 15% of TOTAL_FEE_BPS (shared by User A and us when User A claims fees)
     ORDER_REFERRER_FEE_BPS = 1500     // 15% of TOTAL_FEE_BPS (earned by the ORDER_REFERRER set by traders)
     ```

   - The minting uses a multisignature wallet with two signers:
     - One controlled by us.
     - One controlled by a smart contract operable by any wallet with the correct Twitter ID attestation.

3. **Confirmation**:
   - The meme coin is launched successfully.
   - Our Twitter bot replies with a confirmation message and a TLink to our landing page.

4. **Accessibility**:
   - The coin is visible on Twitter and available for trading on platforms like Wow.xyz, Moonshot, and Uniswap.
  

## 🚀 Features
- Create meme coins directly from social platforms like x.com
- Automatic fee distribution to content creators
- Cross-platform utilities via tapp technology
- Integrated with polular memecoin launchers

## 💎 Core Benefits
- Monetize social influence
- Earn from viral content
- Trade through established DEXs
- Powered by SmartLayer's tapp framework

## 🔗 Links
- Website: socialmint.xyz
- Twitter: @SocialMintApp
- Documentation: docs.socialmint.xyz

Built by SmartLayer Labs 🏗️

5. **Claiming Fees**:
   - User A clicks the TLink to visit our landing page.
   - He verifies ownership of his Twitter ID.
   - Upon verification, he can claim his

