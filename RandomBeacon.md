# Random Beacon

Proposal for smart contract that will run a beacon of random data. 

Random Data Provider:

- An endpoint that allows the beacon to notify them that they should submit random data for block 'X'.
- Code that would automatically respond to random data requests at block 'X'.

Beacon:

- An endpoint for providers to "buy in" to the beacon.
- An endpoint for providers to submit their data.
- An endpoint for buyers to notify the beacon that they want to buy random data at block 'X'.
- An endpoint for buyers to retrieve the number that they bought.
