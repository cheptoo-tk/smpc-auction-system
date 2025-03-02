# Secure Auction System

This repository contains a secure auction system implementation using Obliv-C for secure multi-party computation. The system matches 3 buyers with 3 sellers while preserving the privacy of their bid/ask values.

## Overview

The auction system allows buyers and sellers to participate in a secure auction without revealing their private valuation information:

- Each buyer has a maximum price they're willing to pay
- Each seller has a minimum price they're willing to accept
- The system finds appropriate matches and determines fair pricing
- All computation happens securely, with only the final results revealed

## Implementation Details

- **Allocation Method**: A greedy algorithm that processes buyers in order (B1, B2, B3) and matches them with available sellers
- **Price Computation**: The final price is set as the average between buyer's maximum and seller's minimum: `Ci = (Yi + X[Ri]) / 2`
- **Security**: All computation is done within Obliv-C's secure environment, preserving privacy throughout the matching process

## Files

- `auction.oc`: The secure auction implementation in Obliv-C
- `auction.h`: Header file for the auction protocol
- `auction.c`: Main driver for the auction protocol
- `Makefile`: Compilation instructions
- `input1.txt` and `input2.txt`: Sample input files for testing
- `report.pdf`: Detailed report explaining the implementation and security analysis

## Running the Code

1. Ensure Obliv-C is installed properly (path set to CILPATH in Makefile)
2. Compile the code:
   ```
   make
   ```
3. Run the auction in server mode:
   ```
   ./a.out 1234 -- input1.txt
   ```
4. Run the auction in client mode (in a separate terminal):
   ```
   ./a.out 1234 localhost input2.txt
   ```

## Input Format

Input files should contain 6 integers representing:
- First three values: Buyer 1, 2, and 3's maximum bids (for party 1) or shares (for party 2)
- Last three values: Seller 1, 2, and 3's minimum asks (for party 1) or shares (for party 2)

## Security Considerations

This implementation maintains privacy of buyer and seller values, revealing only the final matching results and prices. For detailed analysis of information leakage, please refer to the report.

## License

MIT License - See LICENSE file for details
