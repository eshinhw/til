# Blockchain

Blockchain is Distributed Ledge that is open to anyone in the blockchain network. Each block contains 1) Data 2) Hash and 3) Hash of previous block. The data stored inside each block depends on application domain. For example, each block inside bitcoin blockchain may contain the information about From, To and Amount. Hash is like a fingerprint that can be used to uniquely identify each block in the network. Hashes are very useful to detect any changes in a block because modifying or updating data inside a block causes to generate new hash.

From a business perspective, it’s helpful to think of blockchain technology as a type of next-generation business process improvement software. Collaborative technology, such as blockchain, promises the ability to improve the business processes that occur between companies, radically lowering the “cost of trust.” For this reason, it may offer significantly higher returns for each investment dollar spent than most traditional internal investments.

Genesis block: the first block of blockchain network which doesn't contain hash of previous block.

Blockchain can be secured by the use of HASHING and PROOF OF WORK.
Proof of Work: 

Blockchain technology can be used in storing medical records, e-notary or even collecting taxes.

Smart contracts is a tiny program stored inside blockchain.

Smart contracts can be used in crowdfunding platforms.

Smart contracts are immutable and distributed.

## Oracle Problem

오라클 문제(oracle problem)란 블록체인 밖에 있는 데이터를 블록체인 안으로 가져올 때 발생하는 문제를 말한다. 오라클 현상 또는 연결성 문제(connectivity problem)라고도 한다.

블록체인 분야에서 오라클(oracle)이란 블록체인 밖에 있는 데이터를 블록체인 안으로 가져오는 것을 말한다. 이때 블록체인 밖에 있는 데이터를 오프체인(off-chain)이라고 하고, 그 데이터가 블록체인 안으로 들어온 것을 온체인(on-chain)이라고 한다. 블록체인(blockchain)은 데이터의 위변조가 거의 불가능한 분산 저장 기술이지만, 데이터가 블록체인 안으로 들어와야 블록체인으로 관리할 수 있다. 데이터가 블록체인 안으로 들어오지 않거나, 혹은 블록체인 안으로 들어오는 과정에서 위변조가 발생한다면, 설령 그 데이터가 블록체인으로 관리된다고 할지라도 신뢰하기 어렵다.

현실 세계에 있는 데이터가 블록체인 안으로 들어오는 과정은 생각만큼 쉽지 않다. 오프체인 데이터가 온체인 데이터로 바뀌기 위해서는, 현실 세계와 블록체인의 중간에서 데이터를 블록체인 안에 넣어주는 사람이나 장치가 필요하다. **오라클 문제는 이러한 중간자 역할을 하는 사람이나 장치를 어떻게 신뢰할 수 있을 것인가 하는 문제**이다. 블록체인은 탈중앙 분산화를 추구하므로 권위를 가진 중앙이 존재하지 않는다. 따라서 블록체인에 데이터를 입력하는 중간자를 신뢰할 수 있는 특별한 방법이 필요하다.

블록체인에서 오라클 문제를 해결하기 위해 다양한 방법이 도입되고 있으나 확실한 해결책은 존재하지 않는다. 암호화폐 소유자들의 투표(voting)를 통해 결정하거나, 다양한 데이터의 중앙값(median)을 선택하거나, 현실 세계와 블록체인 사이에서 신뢰할 수 있는 데이터를 제공해 주는 중간자(middleware)를 두는 방법 등 블록체인 오라클 문제를 해결하기 위한 다양한 방안이 제시되고 있다.

## The Value of Blockchain

- **Value**: Enables a unique asset tobe transferred over the internet without a middle centralized agent. We can create a digital asset that is unique and transfer the unique asset to other people directly without losing its uniqueness and needing any third parties. 
- **Trust**: Creates a permanent, secure and unalterable record of who owns what. Using advanced cryptography, "Information integrity" is preserved. We can have digital fingerprints of every single transaction that happens on the network. 
- **Reliability**: Decentralized network structure ensures that there is no single point of failure which could bring the entire system down.

Prove authenticity and guarantee integrity

Blockchain provide a single source of truth that is permanent, verifable and unchangeable. 

## Characteristics of Blockchain

- Ledger
- Costantly growing
- Permanent record of all transactions
- Secure
- Chronological
- Immutable

## Double Spending

Double spending is one of the key problems with sending money over the Internet and why there has traditionally been a need for third parties such as banks and other institutions. Bitcoin solves this issue.

## The Roles of Bitcoin Miners

- Process and confirm transactions
- Anyone can be a Bitcoin miner due to decentralization
- Creates blocks on the Bitcoin Blochain
- Secure the Bitcoin network
- More Bitcoin miners, more secure the Bitcoin blockchain network because more Bitcoin miners make harder to hack the network and manipulate the stored data
- Miners need specialized and powerful computers which are specifically designed for Bitcoin mining.
- Solve cryptography math problems.
- Miners get rewarded/paid in Bitcoin, and that's how Bitcoin is created.

## Hash Functions

- Secure Hash Algorithm (SHA) 256 developed by National Security Agency (NSA)
- Cryptography is a key component.
- SHA256 allows to generate unique hash from given data
- Hash is a one way function: there is no way of getting the data from hash
- On the other hand, encryption allows two ways conversion. We can convert the data into encrypted form and also retrieve data from encrypted code.

## Block Hashing

- Miners are in the process of creating blocks
- Nonce: Number used Once

## Nonce

"Nonce" is a portmanteau of **"number used only once."** It is a four-byte number added to a hashed—or encrypted—block in a blockchain that, when rehashed, meets the difficulty level restrictions. The nonce is the number that blockchain miners are solving for. When the solution is found, the blockchain miner that solves it is given the block reward.