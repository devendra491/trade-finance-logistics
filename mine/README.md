## GLOSSARY

> Anchor Peer

- Helps in communication between peers of different organizations
- As communication across orgranizations depends on gossip in order to work, there must be at least one anchor peer defined in the channel configuration.
- It is strongly recommended that every organization provides its own set of anchor peers for high availability and redundancy

> ACL ( Access Control List )

- associates access to specific peer resources to a Policy
- part of channel's configuration
- written in configtx.yaml

> Block

- created by the ordering system and validated by peers

> Concurrency Control Version Check

- If the data read for the transaction has changed between execution time and commitment time, then a Concurrency Control Version Check violation has occured, and the transaction is marked as invalid on the ledger and values are not updated in the database

> Configuration Block

- Contains the configuration data defining members and policies for a system chain ( ordering service ) or channel
- Any configuration modifications to a channel or overall network (e.g. a member leaving or joining ) will result in a new configuration block being appended to the appropriate chain.
- This block will contain the contents of the genesis block, plus the delta

> Consortium

- A collection of non-orderer organizations on the blockchain network.
- These are the org. that form and join channels and that owns peers.
- At channel creation time, all organizations added to the channel must be part of a consortium
- However, an organization that is not defined in a consortium may be added to an existing channel

> Endorsement

- Process where specific nodes executes a chaincode transaction
- A proposal response to the client application is returned
- The proposal response includes the chaincode execution response message, results ( read set and write set ), and events, as well as a signature to serve as proof of the peer's chaincode execution
- Chaincode applications have corresponding endorsement policies, in which the endorsing peers are specified

> Endorsement policy

- Defines the peer nodes on a channel that must execute transactions 
- policy could require a transaction to be endorsed by a minimum number of endosing peers

> Hyperledger Fabric CA

- Default certificate authority component, which issues PKI-based certificates to network member organizations and their users
- Issues one root certificate (rootCert) to each member and one enrollment certificate (ECert) to each authorized user

> Gossip Protocol

- Performs three functions
	1. Manages peer discovery and channel membership
	2. Disseminates ledger data across all peers on the channel
	3. syncs ledger state across all peers on the channel

> Initialize

- A method to initialize a chaincode application

> Install

- The process of placing a chaincode on a peer's file system

> Instantiate

- Process of starting and initializing a chaincode application on a specific channel
- After instantiation, peers that have the chaincode installed can accept chaincode invocations

> Invoke

- Used to call chaincode functions
- A client application invokes chaincode by sending a transaction proposal to a peer
- Peer will execute the chaincode and return an endorsed proposal response to the client application
- The client application will gather enough proposal responses to satisfy an endorsement policy, and will then submit the transaction  results for ordering, validation and commit.
- Client application may choose not to submit the transaction results
- Invoke includes a channel identifier, the chaincode function to invoke, and an array of arguments

> Leading Peer

- Each organization can own multiple peers on each channel that they subscribe to
- One or more of these peers should serve as the leading peer for the channel, in order to communicate with the network ordering service on behalf of the organization.
- Ordering service delivers blocks to the leading peer(s) on a channel, who then distribute them to other peers within the same organization

> Ledger

- Consists of two distinct parts
	1. Blockchain: can't be changed once a block has been added
	2. State database: A database containing the current value of the set of key-value pairs that have been added, modified or deleted by the set of validated and committed transactions in teh blockchain
- It's helpful to think of there being one logical ledger for each channel in the network
- In reality, each peer in a channel maintains its own copy of the ledger - which is kept consistent with every other peer's copy through a process called consensus

> Membership Service Provider 

- Refers to an abstract component of the system that provides credentials to clients, and peers for them to participate in a Hyperledger fabric network
- PKI based Implementation

> Ordering Service

- A defined collective of nodes that orders transactions into a block
- Exists independent of the peer processes
- Orders transactions on a first-come-first-serve basis for all channel's on the network

> Peer

- A network entity that maintains a ledger and runs chaincode containers in order to perform read/write operations to the ledger

> Policy

- They are used to restrict access to resources on a blockchain network
- They dictate who can read from or write to a channel, or who can use a specific chaincode API via an ACL
- May be defined in configtx.yaml

> Private Data

- Confidential data that is stored in a private database on each authorized peer, logically seperate from the channel ledger data
- Access to this data is restricted to one or more organizations on a channel via a private data collection definition
- Unauthorized organizations will have a hash of the private data on the channel ledger as evidence of the transaction data

> Private Data Collection ( Collection )

- Used to manage confidential data that two or more organizations on a channel want to keep private from other organizations on that channel

> Proposal

- A request for endorsement that is aimed at specific peers on a channel
- Each proposal is either an instantiate or an invoke ( read/write ) request
