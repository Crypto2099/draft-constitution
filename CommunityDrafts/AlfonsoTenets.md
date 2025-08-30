# 10 Crucial Tenets/Protections to Append to Cardano’s Constitution

1. **Updating the Ledger**
   - **Guaranteed Inclusion**: All valid ledger state transitions (transactions) shall be included in a block, in a time no longer than `<tₛ>` seconds after being broadcasted to the network `<t₀>`.
   - **Tier-assignment and Expediency**: Transactions will be assigned a tier, proportional to an attached ADA fee, and where the number of tiers is determined by the protocol. For a given tier, transactions shall be included in a block in an order determined by their age since broadcasting (older transactions first).

2. **Transaction Creation**
   - **Predictability**: The specific outcomes of any potential transaction, the required fee costs to include it in the ledger, and whether it’s a valid or invalid ledger transition, shall be knowable by the issuer before broadcasting it.

3. **Access, Usage, and Deployment of Transactions and Logic**
   - **Pseudonymity**: Users of the chain shall not be required to identify themselves or prove their worthiness before being able to access or use the chain.
   - **Fungibility of Actors**: Any information gatherable from, or broadcasted by users using the chain, shall not compromise the fungibility of actors. This means any two users should be as indistinguishable as possible from one another when looking at how they interact with the chain, or the chain itself.
   - **Censoring**: The chain shall not censor the deployment of valid transactions of any type or logic in the form of smart contracts, as long as they don’t compromise any of the other tenets listed here.

4. **Guaranteed Ownership Over Assets and Data**
   - **Ownership**: Ownership shall be defined as the exclusive and non-revocable ability of an individual or collection of individuals to unilaterally spend, move, revoke, or create assets and data. Ownership shall be enforced/enabled via secure cryptographic means.

5. **Privacy**
   - **Frugality**: Actors in the space will minimize the amount of data and information collected from users, beyond the minimum necessary to perform their duties or offer their services.
   - **Disclosure and Consent**: Users shall be promptly and properly informed of any data a service requests, or may gather from them, before such gathering happens. This gathering shall only happen with the express consent of users.

6. **Conservation of Value (ADA) and Information (Transaction History)**
   - **Value**: There will be no issuance of any further ADA tokens beyond the expected 45 billion units. ADA will always be an acceptable currency to pay for fees and engage in on-chain governance.
   - **Information**: The entire transaction history of the Cardano blockchain shall be preserved somewhere, in perpetuity, so that any actor has the means to access it. Furthermore, the chain will guarantee the cryptographic verification of all transactions since the Genesis block to the present day, requiring only the knowledge of the information contained in the Genesis block (Ouroboros Genesis).

7. **Optimization of Resources**
   - **Efficiency**: As a default, Cardano shall maximize efficiency in operations, processes, logic, resource consumption. Non-efficient alternatives must be properly justified/argued for before being implemented, on a case-by-case basis.

8. **Trust in Governance**
   - **Legitimacy**: Cardano shall strive to achieve and maintain sufficient levels of decentralization and representation in order to preserve the legitimacy of governance. No key governance actions will happen without the express consent of a majority of ADA holders, and other key actors when relevant, such as stake pools, institutions, the constitutional committee.

9. **Compliance and Regulations**
   - **Opt-in Conditional Logic**: Cardano shall offer optional compliance mechanisms for those who wish to use the Cardano blockchain while abiding by further regulations and requirements; which we’ll refer to here as—additional conditional logic—that requires providing personal or otherwise additional data beyond the typical necessary to engage with the chain (that necessary to prove ownership of assets or data, or consent by a third party whose assets or data are being managed, usually in the form of private cryptographic keys). But these shall never be implemented at the ledger level, which will remain agnostic to particular regulations, permissioned usage, and other forms of additional conditional logic—such as KYC, AML, and others.

10. **Non-secrecy**
    - **Transparency and Access**: Cardano is a public permissionless blockchain, and will therefore make the entire history of the chain auditable and accessible by any party. Furthermore, Cardano shall strive to maximize levels of transparency and mechanisms for accountability in governance. Transactions containing private or obfuscated information are still allowed, but are nonetheless recorded on the history of the chain.