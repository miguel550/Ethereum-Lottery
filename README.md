# Ethereum-Lottery
Proposal for smart contract lottery on the ethereum blockchain

### Theory

1. Each player of the lottery sends a tx containing their fee for playing the lottery and a byte of binary data that represents their lotto numbers.
2. After a certain amount of time (blocks) has passed users will no longer be able to buy lotto tickets.
3. The contract will wait for eight blocks to be mined on the network.
4. The block hashes for each of the eight blocks will be converted from base 64 to base ten and then taking the modulo 2 to get the binary digit that represents the block for that lotto drawing.
5. The binary digits will be put in ascending order by block number.
6. Any ticket submitted that matches the lotto byte with their own byte will win an equal share of the winnings.
  7. 10% of the winnings should perhaps be taken on the top to provide a new starting pool for the next lotto.  

### Example

- Lotto starts at block **1492707**
- Players are allowed to buy lotto tickets for 360 blocks (~1 hour)
- After block 360 has been mined players can no longer buy lotto tickets
- The following eight blocks are mined.

| Block       | Hash          | Result  |
| ----------- |:-------------:| -----:|
| 1493067     | 0x2b1df7dc646c5aecac48065b2fb115def2629f8fdc9d11eadc94180f67a7406a | 0 |
| 1493068     | 0x6c94f1dbbde8af5a8335f64e9bf11ad173269cddcbd663d8d415787d54e5b372 |   0 |
| 1493069 | 0xf0c44a4910151658f04210fe569b202171dcce19e74f1ad1ba0c2cbe38fe55ea |    0 |
| 1493070 | 0x758fe3dc17429893b56fa1778bf4372e1d7d96d2055bf13676f8c5abb6f29ce4 |    0 |
| 1493071 | 0x31ccadb869654ad1ab79f81d981434b56bc2fd62eda093e0096c7d0fce6a0d40 |    0 |
| 1493072 | 0xc16f33bd04bed88fc3c22100e5d2ffb5d73e2af8b7eee4d3041f93f0a70d7765 |    1 |
| 1493073 | 0x0dba6046fdeb3e75f2fe54914378c9adecb196bf21d3b542b43954f7a3459fe2 |    0 |
| 1493074 | 0xd5f1371e3e4d8a2d1a2795d230e3bc3adf299110b15e9df9d9bff24a4a7080a5 |    1 |

<sub><sup>Results are calculated by converting the hash from base 64 to base 10 then taking the modulo 2</sub></sup>

- The winning string for this lottery would be `00000101`. Any player that submitted this string during the previous 360 block buy phase would be entitled to an equal share of winnings.

### Caveats

- This proposal introduces an incentive for miners to quietly 51% attack the network to win the lottery. This particular risk could be exacerbated with a PoS system. 
- [An attacker need not control every block mined to unfairly increase their chance at winning the lottery.](https://gist.github.com/alexvandesande/259b4ffb581493ec0a1c#gistcomment-1689689)
