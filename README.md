# PixelCanvas - Interactive NFT Canvas Gaming Platform

PixelCanvas is a decentralized platform for collaborative pixel art creation, built using the Clarity smart contract language. It allows users to mint, modify, and engage with pixels on a virtual grid while earning rewards for participation and engagement.

---

## Features

### Collaborative Pixel Art
- Users can mint individual pixels on a grid, specifying their color (RGB).
- Minted pixels become NFTs owned by the creator.
- Users can modify pixels they own, enabling continuous creativity.

### Engagement and Rewards
- Engage with pixels created by others to increase their engagement score.
- Pixel creators earn STX tokens as an engagement bonus.

### Decentralized Management
- Fully decentralized, with actions controlled by smart contracts.
- Admin privileges are minimal and limited to withdrawing accumulated funds.

---

## Contract Overview

### Constants
- **`ADMIN`**: The contract deployer.
- **`GRID_DIMENSION`**: Dimensions of the pixel grid (100x100).
- **`MINT_COST`**: Cost to mint a pixel (1000 STX).
- **`ENGAGEMENT_BONUS`**: Reward distributed to the creator when a pixel is engaged with (100 STX).

### Error Codes
- **`ERR_ACCESS_DENIED`**: Unauthorized action attempted.
- **`ERR_OUT_OF_BOUNDS`**: Coordinates are outside the valid grid range.
- **`ERR_ALREADY_MINTED`**: Pixel at the specified coordinates already minted.
- **`ERR_PAYMENT_FAILED`**: Payment transfer failed.

### State Variables
- **`minted-count`**: Total number of minted pixels.
- **`distributed-rewards`**: Total rewards distributed to participants.

---

## Functions

### Core Functions
1. **Mint Pixel**
   - `mint-pixel(x uint, y uint, rgb string-utf8)`
   - Mints a new pixel at the specified grid coordinates with the given color.
   - Requires the minting cost to be paid in STX.

2. **Modify Pixel**
   - `modify-pixel(x uint, y uint, new-rgb string-utf8)`
   - Allows the owner of a pixel to change its color.

3. **Engage with Pixel**
   - `engage-with-pixel(x uint, y uint)`
   - Increases the engagement score of a pixel.
   - Rewards the pixel's creator with an engagement bonus in STX.

### Read-Only Functions
1. **Get Pixel Data**
   - `get-canvas-pixel(x uint, y uint)`
   - Retrieves details about a specific pixel, including its owner, color, timestamp, and engagement score.

2. **Get Participant Data**
   - `get-participant-data(user principal)`
   - Returns metrics for a participant, including owned pixels and earned rewards.

3. **Validate Coordinates**
   - `validate-coordinates(x uint, y uint)`
   - Ensures the coordinates are within the grid dimensions.

### Administrative Functions
1. **Withdraw Funds**
   - `admin-withdraw(amount uint)`
   - Allows the admin to withdraw accumulated funds from the contract.

---

## Data Structures

### Canvas State
- Stores data for each pixel on the grid.
  ```clarity
  { x: uint, y: uint }
  {
    creator: principal,
    rgb: (string-utf8 7),
    timestamp: uint,
    engagement: uint
  }
  ```

### Participant Metrics
- Tracks data for each user.
  ```clarity
  principal
  {
    owned-pixels: uint,
    earned-rewards: uint
  }
  ```

---

## How to Use

### Deploy the Contract
1. Deploy the `PixelCanvas` contract using a Clarity-compatible blockchain platform such as Stacks.

### Minting Pixels
1. Call the `mint-pixel` function with grid coordinates (x, y) and desired color (in RGB format, e.g., `"#FF5733"`).
2. Ensure the payment of the minting fee (1000 STX).

### Modifying Pixels
1. Use the `modify-pixel` function to update the color of a pixel you own.

### Engaging with Pixels
1. Call the `engage-with-pixel` function on a pixel you wish to interact with.
2. The creator of the pixel will earn a reward.

---

## Development and Testing
- **Language**: Clarity
- **Tools**: Clarinet, Stacks Blockchain
- **Recommended IDE**: VS Code with Clarity plugin

---

## Future Enhancements
1. Expand grid dimensions for larger collaborative artworks.
2. Implement more reward mechanics based on engagement milestones.
3. Introduce advanced features like animations and pixel groups.

---

## License
This project is released under the MIT License.

