`Draft 2024-09-20`

# CARDANO BLOCKCHAIN ECOSYSTEM CONSTITUTION

## PREAMBLE

Through the adoption of this Constitution, the Cardano Blockchain ecosystem establishes a transparent and accountable governance framework to ensure that decisions are made in the best interest of the Cardano community. The Constitution acknowledges the role and empowers the Constitutional Committee to enforce its articles and make decisions when "code as law" is insufficient, necessitating the presence of a governance structure with people in the loop. This Constitution serves as a guiding document to promote the long-term sustainability and success of the Cardano Blockchain ecosystem.

## ARTICLE I. CARDANO BLOCKCHAIN TENETS AND GUARDRAILS

### Section 1

Transactions on the Cardano Blockchain shall not be intentionally degraded or censored.

The cost of transactions on the Cardano Blockchain should be predictable and reasonable.

Any individual or entity desiring to develop and deploy non-malicious applications on the Cardano Blockchain shall not be prevented from deploying such applications as-intended.

When contributions to the system are recognized, recorded, or processed, they should be done so fairly.

The system shall not spend, delegate, or stake any ADA owner’s assets without the owner’s consent.

The Cardano Blockchain shall reasonably preserve any value and information an owner of ADA seeks to store, while accommodating evolving innovations that ensure sustainable resource management.

Resources, whether system, network, or economic, shall not be unnecessarily wasted.

Users shall be treated fairly, and the system shall adapt in alignment with their collective will, ensuring long-term sustainability and viability.

The system shall not require users to violate local laws and regulations, and should provide alternatives whenever feasible.

Operations should be transparent, predictable, verifiable, and interpretable, ensuring fairness and balance, while also supporting privacy-focused use cases where appropriate.

### Section 2

Operations shall be in accordance with the Guardrails as set forth in the Guardrails appendix and on-chain scripts.

The Cardano community may modify the Guardrails after a proposal to change them is voted on and ratified.

## ARTICLE II. THE CARDANO BLOCKCHAIN COMMUNITY

### Section 1

No formal membership shall be required to use, participate in, or benefit from the Cardano Blockchain.

### Section 2

Members of the Cardano community who own ADA are entitled to access and participate in the on-chain decision-making processes of the Cardano Blockchain ecosystem, including voting and taking part in on-chain governance.

Reasonable fees and/or deposits may be set via parameters to prevent spam and abuse of the governance process.

## ARTICLE III. PARTICIPATORY GOVERNANCE

### Section 1

The Cardano Blockchain ecosystem shall be governed by a decentralized, on-chain governance model.

### Section 2

All owners of ADA shall have the right to propose changes to the governance structure of the Cardano Blockchain ecosystem.

### Section 3

The process for participating in, submitting and voting on on-chain governance actions shall be open, transparent, and protected from undue influence and manipulation.

### Section 4

No withdrawals from the Cardano treasury shall be permitted except as part of a periodic budget as-required by the Cardano Blockchain Guardrails.

No withdrawals from the Cardano treasury in excess of 1,000,000 ADA shall be permitted without sufficient independent audits, oversight metrics, and a reasonable amount of ADA to cover the cost of such audits.

The total supply of ADA shall not be modified to be less or more than 45,000,000,000.

## ARTICLE IV. DELEGATED REPRESENTATIVES

### Section 1

Any owner of ADA shall have the permissionless option to register as a dRep. 

Any owner of ADA shall be allowed to delegate their voting stake to one or more registered dReps, including themselves.

## ARTICLE V. STAKE POOLS

### Section 1

Any owner of ADA shall have the permissionless option to register a stake pool.

Any owner of ADA shall be allowed to delegate their voting stake to one or more registered stake pools, including their own.

## ARTICLE VI. CONSTITUTIONAL COMMITTEE

### Section 1

The Constitutional Committee shall be limited to voting on the constitutionality of governance actions.

### Section 2

The Constitutional Committee shall be composed of a set number of members and must pass any proposals via a voting threshold defined by the Cardano Blockchain Guardrails.

### Section 3

Members of the Constitutional Committee shall serve terms for a specific period of time as-defined by the Cardano Blockchain Guardrails.

### Section 4

The Constitutional Committee shall transparently publish each decision and provide the basis for any "no" votes with reference to specific Articles of this Constitution.

## ARTICLE VII. AMENDMENTS

### Section 1

Amendments to this Constitution require approval through an on-chain governance action by ADA owners, meeting a threshold set by the Cardano Blockchain Guardrails and corresponding parameters for constitutional amendments.

### Section 2

In case of inconsistencies between the Guardrails documented in the Appendix and the Guardrails implemented on-chain, the on-chain version shall prevail, and the Constitutional Committee shall work to reconcile such inconsistencies through appropriate governance actions.

## APPENDIX I: CARDANO BLOCKCHAIN GUARDRAILS

### 1. Introduction

This Appendix sets forth guardrails that must be applied to Cardano on-chain governance actions. These guardrails cover both essential, intrinsic limits on settings, and recommendations that are based on experience, measurement and governance objectives.

These guardrails are designed to avoid unexpected problems with the operation of the Cardano Blockchain. They are intended to guide the choice of sensible parameter settings and avoid potential problems with security, performance or functionality. As described below, some of these guardrails are automatable and will be enforced via an on-chain script or built-in ledger rules.  However, many of them require the input of human experts which will be enforced by the Constitutional Committee through referencing this document.

#### Automated Checking ("Guardrails Script")

A script hash is associated with the constitution hash when a New Constitution or Guardrails Script governance action is enacted. It acts as an additional safeguard to the ledger rules and types, filtering non-compliant governance actions.

The guardrails script only affects two types of governance actions:

- Parameter Update actions.
- Treasury Withdrawal actions.

The script is executed when either of these types of governance action is submitted on-chain. The purpose of this script is to avoid scenarios where an erroneous script could prevent the chain from ever enacting a Hard Fork action, resulting in deadlock.

##### Symbol and Explanation

- (y) The script can be used to enforce the guardrail.
- (x) The script cannot be used to enforce the guardrail.
- (~ - reason) The script cannot be used to enforce the guardrail for the reason given, but future ledger changes could enable this.

Guardrails may overlap: in this case, the most restrictive set of guardrails will apply.

### 2. GUARDRAILS AND GUIDELINES ON PROTOCOL PARAMETER UPDATE ACTIONS

- PARAM-01 (y) Any protocol parameter that is not explicitly named in this document must not be changed by a Parameter update governance action.
- PARAM-02 (y) Where a protocol parameter is explicitly listed in this document but no checkable guardrails are specified, the guardrails script must not impose any constraints on changes to the parameter. Checkable guardrails are shown by a (y).

#### 2.1 Critical Protocol Parameters

##### Parameters that are Critical to the Operation of the Blockchain

- `maxBlockBodySize` (maximum block body size)
- `maxTxSize` (maximum transaction size)
- `maxBlockHeaderSize` (maximum block header size)
- `maxValueSize` (maximum size of a serialized asset value)
- `maxBlockExecutionUnits` (maximum script execution/memory units in a single block)
- `txFeePerByte` (minimum fee coefficient)
- `txFeeFixed` (minimum fee constant)
- `minFeeRefScriptCoinsPerByte` (minimum fee per byte for reference scripts)
- `utxoCostPerByte` (minimum Lovelace deposit per byte of serialized UTxO)
- `govDeposit` (governance action deposit)

Guardrails:
- PARAM-03 (y) Critical protocol parameters require an SPO vote in addition to a DRep vote: SPOs must say "yes" with a collective support of more than 50% of all active block production stake. This is enforced by the guardrails on the stake pool voting threshold.
- PARAM-04 (x) At least 3 months should pass between the publication of an off-chain proposal to change a critical protocol parameter and the submission of the corresponding on-chain governance action. This guardrail may be relaxed in the event of an emergency network issue following careful technical discussion and evaluation.

---

##### Parameters that are Critical to the Governance System

- `stakeAddressDeposit` (delegation key Lovelace deposit)
- `stakePoolDeposit` (pool registration Lovelace deposit)
- `minPoolCost` (minimum fixed rewards cut for pools)
- `dRepDeposit` (DRep deposit amount)
- `committeeMinSize` (minimal Constitutional Committee size)
- `committeeMaxTermLimit` (maximum term length in epochs for the Constitutional Committee members)

Guardrails:
- PARAM-05 (y) DReps must vote "yes" with a collective support of more than 50% of all active voting stake. This is enforced by the guardrails on the DRep voting thresholds.
- PARAM-06 (x) At least 3 months should pass between the publication of an off-chain proposal to change a parameter that is critical to the governance system and the submission of the corresponding on-chain governance action. This guardrail may be relaxed in the event of an emergency network issue following careful technical discussion and evaluation.

---

#### 2.2. Economic Parameters

##### `txFeePerByte` (transaction fee per byte)

Guardrails:
- TFPB-01 (y) `txFeePerByte` must not be lower than 30 (0.000030 ada). This protects against low-cost denial of service attacks.
- TFPB-02 (y) `txFeePerByte` must not exceed 1,000 (0.001 ada). This ensures that transactions can be paid for.
- TFPB-03 (y) `txFeePerByte` must not be negative.

---

##### `txFeeFixed` (fixed transaction fee)

Guardrails:
- TFF-01 (y) `txFeeFixed` must not be lower than 100,000 (0.1 ada). This protects against low-cost denial of service attacks.
- TFF-02 (y) `txFeeFixed` must not exceed 10,000,000 (10 ada). This ensures that transactions can be paid for.
- TFF-03 (y) `txFeeFixed` must not be negative.
- TFGEN-01 (x - "should") To maintain a consistent level of protection against denial-of-service attacks, `txFeeFixed` and `txFeePerByte` should be adjusted whenever Plutus Execution prices are adjusted (`executionUnitPrices[steps/memory]`).
- TFGEN-02 (x - unquantifiable) Any changes to `txFeeFixed` or `txFeePerByte` must consider the implications of reducing the cost of a denial-of-service attack or increasing the maximum transaction fee so that it becomes impossible to construct a transaction.

---

##### `utxoCostPerByte` (UTxO cost per byte)

Guardrails:
- UCPB-01 (y) `utxoCostPerByte` must not be lower than 3,000 (0.003 ada).
- UCPB-02 (y) `utxoCostPerByte` must not exceed 6,500 (0.0065 ada).
- UCPB-03 (y) `utxoCostPerByte` must not be zero.
- UCPB-04 (y) `utxoCostPerByte` must not be negative.
- UCPB-05 (x - "should") Changes should account for:
  - The acceptable cost of attack.
  - The acceptable time for an attack (at least one epoch is assumed).
  - The acceptable memory configuration for full node users (assumed to be 16GB for wallets or 24GB for stake pools).
  - The sizes of UTxOs (~200B per UTxO minimum, up to about 10KB).
  - The current total node memory usage.

  ---

##### `stakeAddressDeposit` (Stake address deposit)

Guardrails:
- SAD-01 (y) `stakeAddressDeposit` must not be lower than 1,000,000 (1 ada).
- SAD-02 (y) `stakeAddressDeposit` must not exceed 5,000,000 (5 ada).
- SAD-03 (y) `stakeAddressDeposit` must not be negative.

---

##### `stakePoolDeposit` (Stake pool deposit)

Guardrails:
- SPD-01 (y) `stakePoolDeposit` must not be lower than 250,000,000 (250 ada).
- SPD-02 (y) `stakePoolDeposit` must not exceed 500,000,000 (500 ada).
- SPD-03 (y) `stakePoolDeposit` must not be negative.

---

##### `minPoolCost` (Minimum Pool Cost)

Guardrails:
- MPC-01 (y) `minPoolCost` must not be negative.
- MPC-02 (y) `minPoolCost` must not exceed 500,000,000 (500 ada).
- MPC-03 (x - "should") `minPoolCost` should be set in line with the economic cost for operating a pool.

---

##### `treasuryCut` (Treasury Cut)

Guardrails:
- TC-01 (y) `treasuryCut` must not be lower than 0.1 (10%).
- TC-02 (y) `treasuryCut` must not exceed 0.3 (30%).
- TC-03 (y) `treasuryCut` must not be negative.
- TC-04 (y) `treasuryCut` must not exceed 1.0 (100%).
- TC-05 (~ - no access to change history) `treasuryCut` must not be changed more than once in any 36-epoch period (approximately 6 months).

---

##### `monetaryExpansion` (Monetary Expansion Rate)

Guardrails:
- ME-01 (y) `monetaryExpansion` must not exceed 0.005
- ME-02 (y) `monetaryExpansion` must not be lower than 0.001
- ME-03 (y) `monetaryExpansion` must not be negative.
- ME-04 (x - "should") `monetaryExpansion` should not be varied by more than +/- 10% in any 73-epoch period (approximately 12 months).
- ME-05 (x - "should") `monetaryExpansion` should not be changed more than once in any 36-epoch period (approximately 6 months).

---

##### `executionUnitPrices` (Plutus Script Execution Prices [priceSteps/priceMemory])

Guardrails:
- EIUP-PS-01 (y) `executionUnitPrices[priceSteps]` must not exceed 2,000 / 10,000,000.
- EIUP-PS-02 (y) `executionUnitPrices[priceSteps]` must not be lower than 500 / 10,000,000.
- EIUP-PM-01 (y) `executionUnitPrices[priceMemory]` must not exceed 2,000 / 10,000.
- EIUP-PM-02 (y) `executionUnitPrices[priceMemory]` must not be lower than 400 / 10,000.
- EIUP-GEN-01 (x - "similar to") The execution prices must be set so that:
  - i) the cost of executing a transaction with maximum CPU steps is similar to the cost of a maximum-sized non-script transaction and
  - ii) the cost of executing a transaction with maximum memory units is similar to the cost of a maximum-sized non-script transaction.
- EIUP-GEN-02 (x - "should") The execution prices should be adjusted whenever transaction fees are adjusted (`txFeeFixed`/`txFeePerByte`). The goal is to ensure that the processing delay is similar for "full" transactions, regardless of their type, and to ensure that the requirements on block diffusion/propagation times are met.

---

##### `minFeeRefScriptCoinsPerByte` (Transaction fee per byte for a reference script)

Guardrails:
- MFRS-01 (y) `minFeeRefScriptCoinsPerByte` must not exceed 1,000 (0.001 ada).
- MFRS-02 (y) `minFeeRefScriptCoinsPerByte` must not be negative.
- MFRS-03 (x - "should") To maintain a consistent level of protection against denial-of-service attacks, `minFeeRefScriptCoinsPerByte` should be adjusted whenever Plutus Execution prices are adjusted (`executionUnitPrices[steps/memory]`) and whenever `txFeeFixed` is adjusted.
- MFRS-04 (x - unquantifiable) Any changes to `minFeeRefScriptCoinsPerByte` must consider the implications of reducing the cost of a denial-of-service attack or increasing the maximum transaction fee.

---

#### 2.3. Network Parameters

Guardrails:
- NETWORK-01 (x - "should") No individual network parameter should change more than once per two epochs.
- NETWORK-02 (x - "should") Only one network parameter should be changed per epoch unless they are directly correlated, e.g., per-transaction and per-block memory unit limits.

---

##### `maxBlockBodySize` (Block Size)

Guardrails:
- MBBS-01 (y) `maxBlockBodySize` must not exceed 122,880 Bytes (120KB).
- MBBS-02 (y) `maxBlockBodySize` must not be lower than 24,576 Bytes (24KB).
- MBBS-03 (x - "exceptional circumstances") `maxBlockBodySize` must not be decreased, other than in exceptional circumstances where there are potential problems with security, performance, or functionality.
- MBBS-04 (~ - no access to existing parameter values) `maxBlockBodySize` must be large enough to include at least one transaction (that is, `maxBlockBodySize` must be at least `maxTxSize`).
- MBBS-05 (x - "should") `maxBlockBodySize` should be changed by at most 10,240 Bytes (10KB) per epoch (5 days), and preferably by 8,192 Bytes (8KB) or less per epoch.
- MBBS-06 (x - "should") The block size should not induce an additional Transmission Control Protocol (TCP) round trip. Any increase beyond this must be backed by performance analysis, simulation, and benchmarking.
- MBBS-07 (x - "unquantifiable") The impact of any change to `maxBlockBodySize` must be confirmed by detailed benchmarking/simulation and not exceed the requirements of the block diffusion/propagation time budgets, as described below. Any increase to `maxBlockBodySize` must also consider future requirements for Plutus script execution (`maxBlockExecutionUnits[steps]`) against the total block diffusion target of 3s with 95% block propagation within 5s. The limit on maximum block size may be increased in the future if this is supported by benchmarking and monitoring results.

---

##### `maxTxSize` (Transaction Size)

Guardrails:
- MTS-01 (y) `maxTxSize` must not exceed 32,768 Bytes (32KB).
- MTS-02 (y) `maxTxSize` must not be negative.
- MTS-03 (~ - no access to existing parameter values) `maxTxSize` must not be decreased.
- MTS-04 (~ - no access to existing parameter values) `maxTxSize` must not exceed `maxBlockBodySize`.
- MTS-05 (x - "should") `maxTxSize` should not be increased by more than 2,560 Bytes (2.5KB) in any epoch, and preferably should be increased by 2,048 Bytes (2KB) or less per epoch.
- MTS-06 (x - "should") `maxTxSize` should not exceed 1/4 of the block size.

---

##### `maxBlockExecutionUnits` (Block memory execution unit limits)

Guardrails:
- MBEU-M-01 (y) `maxBlockExecutionUnits[memory]` must not exceed 120,000,000 units.
- MBEU-M-02 (y) `maxBlockExecutionUnits[memory]` must not be negative.
- MBEU-M-03 (x - "should") `maxBlockExecutionUnits[memory]` should not be changed (increased or decreased) by more than 10,000,000 units in any epoch.
- MBEU-M-04 (x - unquantifiable) The impact of any change to `maxBlockExecutionUnits[memory]` must be confirmed by detailed benchmarking/simulation and not exceed the requirements of the diffusion/propagation time budgets, as also impacted by `maxBlockExecutionUnits[steps]`. Any increase must also consider previously agreed future requirements for the total block size (`maxBlockBodySize`) measured against the total block diffusion target of 3s with 95% block propagation within 5s. Future Plutus performance improvements may allow the per-block limit to be increased, but must be balanced against the overall diffusion limits as specified in the previous sentence, and future requirements.

---

##### `maxTxExecutionUnits` (Transaction memory execution unit limits)

Guardrails:
- MTEU-M-01 (y) `maxTxExecutionUnits[memory]` must not exceed 40,000,000 units.
- MTEU-M-02 (y) `maxTxExecutionUnits[memory]` must not be negative.
- MTEU-M-03 (~ - no access to existing parameter values) `maxTxExecutionUnits[memory]` must not be decreased.
- MTEU-M-04 (x - "should") `maxTxExecutionUnits[memory]` should not be increased by more than 2,500,000 units in any epoch.

---

##### `maxBlockExecutionUnits` (CPU block limits in steps)

Guardrails:
- MBEU-S-01 (y) `maxBlockExecutionUnits[steps]` must not exceed 40,000,000,000 (40Bn) units.
- MBEU-S-02 (y) `maxBlockExecutionUnits[steps]` must not be negative.
- MBEU-S-03 (x - "should") `maxBlockExecutionUnits[steps]` should not be changed (increased or decreased) by more than 2,000,000,000 (2Bn) units in any epoch (5 days).
- MBEU-S-04 (x - unquantifiable) The impact of the change to `maxBlockExecutionUnits[steps]` must be confirmed by detailed benchmarking/simulation and not exceed the requirements of the block diffusion/propagation time budgets, as also impacted by `maxBlockExecutionUnits[memory]`. Any increase must also consider previously identified future requirements for the total block size (`maxBlockBodySize`) measured against the total block diffusion target of 3s with 95% block propagation within 5s. Future Plutus performance improvements may allow the per-block limit to be increased, but must be balanced against the overall diffusion limits as specified in the previous sentence, and future requirements.

---

##### `maxTxExecutionUnits` (CPU transaction limits in steps)

Guardrails:
- MTEU-S-01 (y) `maxTxExecutionUnits[steps]` must not exceed 15,000,000,000 (15Bn) units.
- MTEU-S-02 (y) `maxTxExecutionUnits[steps]` must not be negative.
- MTEU-S-03 (~ - no access to existing parameter values) `maxTxExecutionUnits[steps]` must not be decreased.
- MTEU-S-04 (x - "should") `maxTxExecutionUnits[steps]` should not be increased by more than 500,000,000 (500M) units in any epoch (5 days).

---

##### `maxBlockHeaderSize` (Block Header Size)

Guardrails:
- MBHS-01 (y) `maxBlockHeaderSize` must not exceed 5,000 Bytes.
- MBHS-02 (y) `maxBlockHeaderSize` must not be negative.
- MBHS-03 (x - "largest valid header" is subject to change) `maxBlockHeaderSize` must be large enough for the largest valid header.
- MBHS-04 (x - "should") `maxBlockHeaderSize` should only normally be increased if the protocol changes.
- MBHS-05 (x - "should") `maxBlockHeaderSize` should be within TCP's initial congestion window (3 or 10 MTUs).

---

#### 2.4. Technical/Security Parameters

##### `stakePoolTargetNum` (Target Number of Stake Pools)

Guardrails:
- SPTN-01 (y) `stakePoolTargetNum` must not be lower than 250.
- SPTN-02 (y) `stakePoolTargetNum` must not exceed 2,000.
- SPTN-03 (y) `stakePoolTargetNum` must not be negative.
- SPTN-04 (y) `stakePoolTargetNum` must not be zero.

---

##### `poolPledgeInfluence` (Pledge Influence Factor)

Guardrails:
- PPI-01 (y) `poolPledgeInfluence` must not be lower than 0.1.
- PPI-02 (y) `poolPledgeInfluence` must not exceed 1.0.
- PPI-03 (y) `poolPledgeInfluence` must not be negative.
- PPI-04 (x - "should") `poolPledgeInfluence` should not vary by more than +/- 10% in any 18-epoch period (approximately 3 months).

---

##### `poolRetireMaxEpoch` (Pool Retirement Window)

Guardrails:
- PRME-01 (y) `poolRetireMaxEpoch` must not be negative.
- PRME-02 (x - "should") `poolRetireMaxEpoch` should not be lower than 1.

---

##### `collateralPercentage` (Collateral Percentage)

Guardrails:
- CP-01 (y) `collateralPercentage` must not be lower than 100.
- CP-02 (y) `collateralPercentage` must not exceed 200.
- CP-03 (y) `collateralPercentage` must not be negative.
- CP-04 (y) `collateralPercentage` must not be zero.

---

##### `maxCollateralInputs` (Maximum number of collateral inputs)

Guardrails:
- MCI-01 (y) `maxCollateralInputs` must not be lower than 1.

---

##### `maxValueSize`

Guardrails:
- MVS-01 (y) `maxValueSize` must not exceed 12,288 Bytes (12KB).
- MVS-02 (y) `maxValueSize` must not be negative.
- MVS-03 (~ - no access to existing parameter values) `maxValueSize` must be less than `maxTxSize`.
- MVS-04 (~ - no access to existing parameter values) `maxValueSize` must not be reduced.
- MVS-05 (x - "sensible output" is subject to interpretation) `maxValueSize` must be large enough to allow sensible outputs (e.g., any existing on-chain output or anticipated outputs that could be produced by new ledger rules).

---

##### `costModels` (Plutus Cost Models)

Guardrails:
- PCM-01 (x - unquantifiable) Cost model values must be set by benchmarking on a reference architecture.
- PCM-02 (x - primitives and language versions aren't introduced in transactions) The cost model must be updated if new primitives are introduced or a new Plutus language version is added.
- PCM-03 (~ - no access to Plutus cost model parameters) Cost model values should not be negative.
- PCM-04 (~ - no access to Plutus cost model parameters) A cost model must be supplied for each Plutus language version that the protocol supports.

---

#### 2.5. Governance Parameters

##### `govDeposit` (Deposit for Governance Actions)

Guardrails:
- GD-01 (y) `govDeposit` must not be negative.
- GD-02 (y) `govDeposit` must not be lower than 1,000,000 (1 ada).
- GD-03 (y) `govDeposit` must not exceed 10,000,000,000,000 (10 million ada).
- GD-04 (x - "should") `govDeposit` should be adjusted in line with fiat changes.

---

##### `dRepDeposit` (Deposit for DReps)

Guardrails:
- DRD-01 (y) `dRepDeposit` must not be negative.
- DRD-02 (y) `dRepDeposit` must not be lower than 1,000,000 (1 ada).
- DRD-03 (y) `dRepDeposit` must not exceed 100,000,000,000 (100,000 ada).
- DRD-04 (x - "should") `dRepDeposit` should be adjusted in line with fiat changes.

---

##### `dRepActivity` (DRep Activity Period)

Guardrails:
- DRA-01 (y) `dRepActivity` must not be lower than 13 epochs (2 months).
- DRA-02 (y) `dRepActivity` must not exceed 37 epochs (6 months).
- DRA-03 (y) `dRepActivity` must not be negative.
- DRA-04 (~ - no access to existing parameter values) `dRepActivity` must be greater than `govActionLifetime`.
- DRA-05 (x - "should") `dRepActivity` should be calculated in human terms (2 months, etc.).

---

##### dRepVotingThresholds

- `dvtCommitteeNoConfidence`
- `dvtCommitteeNormal`
- `dvtHardForkInitiation`
- `dvtMotionNoConfidence`
- `dvtPPEconomicGroup`
- `dvtPPGovGroup`
- `dvtPPNetworkGroup`
- `dvtPPTechnicalGroup`
- `dvtTreasuryWithdrawal`
- `dvtUpdateToConstitution`

##### poolVotingThresholds

- `pvtCommitteeNoConfidence`
- `pvtCommitteeNormal`
- `pvtHardForkInitiation`
- `pvtMotionNoConfidence`
- `pvtPPSecurityGroup`

Guardrails:
- VT-GEN-01 (y) All thresholds must be greater than 50% and less than or equal to 100%.
- VT-GEN-02 (y) Economic, network, and technical parameter thresholds must be in the range 51%-75%.
- VT-GEN-03 (y) Governance parameter thresholds must be in the range 75%-90%.
- VT-HF-01 (y) Hard fork action thresholds must be in the range 51%-80%.
- VT-CON-01 (y) New Constitution or guardrails script action thresholds must be in the range 65%-90%.
- VT-CC-01 (y) Update Constitutional Committee action thresholds must be in the range 51%-90%.
- VT-NC-01 (y) No confidence action thresholds must be in the range 51%-75%.

---

##### `govActionLifetime` (Governance Action Lifetime)

Guardrails:
- GAL-01 (y) `govActionLifetime` must not be lower than 1 epoch (5 days).
- GAL-03 (x - "should") `govActionLifetime` should not be lower than 2 epochs (10 days).
- GAL-02 (y) `govActionLifetime` must not exceed 15 epochs (75 days).
- GAL-04 (x - "should") `govActionLifetime` should be calibrated in human terms (e.g., 30 days, two weeks) to allow sufficient time for voting, etc., to take place.
- GAL-05 (~ - no access to existing parameter values) `govActionLifetime` must be less than `dRepActivity`.

---

##### `committeeMaxTermLimit` (Maximum Constitutional Committee Term)

Guardrails:
- CMTL-01 (y) `committeeMaxTermLimit` must not be zero.
- CMTL-02 (y) `committeeMaxTermLimit` must not be negative.
- CMTL-03 (y) `committeeMaxTermLimit` must not be lower than 18 epochs (90 days, or approximately 3 months).
- CMTL-04 (y) `committeeMaxTermLimit` must not exceed 293 epochs (approximately 4 years).
- CMTL-05 (x - "should") `committeeMaxTermLimit` should not exceed 220 epochs (approximately 3 years).

---

##### `committeeMinSize` (Minimum Size of the Constitutional Committee)

Guardrails:
- CMS-01 (y) `committeeMinSize` must not be negative.
- CMS-02 (y) `committeeMinSize` must not be lower than 3.
- CMS-03 (y) `committeeMinSize` must not exceed 10.

#### 2.6. Guardrails and Guidelines on Treasury Withdrawal Actions

Guardrails:
- TREASURY-01 (x) DReps must define a net change limit for the Cardano Treasury's balance per period of time.
- TREASURY-02 (x) The budget for the Cardano Treasury must not exceed the net change limit for the Cardano Treasury's balance per period of time.
- TREASURY-03 (x) The budget for the Cardano Treasury must be denominated in ADA.
- TREASURY-04 (x) Treasury withdrawals must not be ratified until there is a community-approved Cardano budget then in effect pursuant to a previous on-chain governance action agreed by the DReps with a threshold of greater than 50% of the active voting stake.

---

#### 2.7 Guardrails and Guidelines on Hard Fork Initiation Actions

Guardrails:
- HARDFORK-01 (~ - no access to existing parameter values) The major protocol version must be the same as or one greater than the major version that will be enacted immediately prior to this change. If the major protocol version is one greater, then the minor protocol version must be zero.
- HARDFORK-02 (~ - no access to existing parameter values) The minor protocol version must be no less than the minor version that will be enacted immediately prior to this change.
- HARDFORK-03 (~ - no access to existing parameter values) At least one of the protocol versions (major or minor or both) must change.
- HARDFORK-04 (x) At least 85% of stake pools by active stake should have upgraded to a Cardano node version that is capable of processing the rules associated with the new protocol version.
- HARDFORK-05 (x) Any new updatable protocol parameters that are introduced with a hard fork must be included in this Appendix and suitable guardrails defined for those parameters.
- HARDFORK-06 (x) Settings for any new protocol parameters that are introduced with a hard fork must be included in the appropriate Genesis file.
- HARDFORK-07 (x) Any deprecated protocol parameters must be indicated in this Appendix.
- HARDFORK-08 (~ - no access to Plutus cost model parameters) New Plutus versions must be supported by a version-specific Plutus cost model that covers each primitive that is available in the new Plutus version.

---

#### 2.8 Guardrails and Guidelines on Update Constitutional Committee or Threshold Actions

Guardrails:
- UPDATE-CC-01 (x) Update Constitutional Committee and/or threshold and/or term governance actions must not be ratified until ADA holders have ratified through an on-chain governance action the Final Constitution.

---

#### 2.9 Guardrails and Guidelines on New Constitution or Guardrails Script Actions

Guardrails:
- NEW-CONSTITUTION-01 (x) A New Constitution or Guardrails Script governance action must be submitted to define any required guardrails for new parameters that are introduced via a Hard Fork governance action.

---

#### 2.10. Monitoring and Reversion of Parameter Changes

A specific reversion/recovery plan must be produced for each parameter change. This plan must include:

- Which parameters need to change and in which ways in order to return to the previous state (or a similar state).
- How to recover the network in the event of a disastrous failure.

This plan should be followed if problems are observed following the parameter change. Note that not all changes can be reverted. Additional care must be taken when making changes to these parameters.

---

#### 2.11. Non-Updatable Protocol Parameters

Some fundamental protocol parameters cannot be changed by the Protocol Parameter Update governance action. These parameters can only be changed in a new Genesis file as part of a hard fork. It is not necessary to provide specific guardrails on updating these parameters.

### LIST OF PROTOCOL PARAMETER GROUPS

The protocol parameters are grouped by type, allowing different thresholds to be set for each group.

The network group consists of:
- `maxBlockBodySize` (maximum block body size)
- `maxTxSize` (maximum transaction size)
- `maxBlockHeaderSize` (maximum block header size)
- `maxValueSize` (maximum size of a serialized asset value)
- `maxTxExecutionUnits[steps]` (maximum script execution units in a single transaction)
- `maxBlockExecutionUnits[steps]` (maximum script execution units in a single block)
- `maxCollateralInputs` (maximum number of collateral inputs)

The economic group consists of:
- `txFeePerByte` (minimum fee coefficient)
- `txFeeFixed` (minimum fee constant)
- `minFeeRefScriptCoinsPerByte` (minimum fee per byte for reference scripts)
- `stakeAddressDeposit` (delegation key Lovelace deposit)
- `stakePoolDeposit` (pool registration Lovelace deposit)
- `monetaryExpansion` (monetary expansion)
- `treasuryCut` (treasury expansion)
- `minPoolCost` (minimum fixed rewards cut for pools)
- `utxoCostPerByte` (minimum Lovelace deposit per byte of serialized UTxO)
- `executionUnitPrices[priceSteps/priceMemory]` (prices of Plutus execution units)

The technical group consists of:
- `poolPledgeInfluence` (pool pledge influence)
- `poolRetireMaxEpoch` (pool retirement maximum epoch)
- `stakePoolTargetNum` (desired number of pools)
- `costModels` (Plutus execution cost models)
- `collateralPercentage` (proportion of collateral needed for scripts)

The governance group consists of all the new protocol parameters that are introduced in CIP-1694:
- `dRepVotingThresholds[...]`, `poolVotingThresholds[...]` (governance voting thresholds)
- `govActionLifetime` (governance action maximum lifetime in epochs)
- `govActionDeposit` (governance action deposit)
- `dRepDeposit` (DRep deposit amount)
- `dRepActivity` (DRep activity period in epochs)
- `committeeMinSize` (minimal constitutional committee size)
- `committeeMaxTermLimit` (maximum term length in epochs for the constitutional committee members)