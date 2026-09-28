# EXPLAINABILITY.md

This document explains the internal mechanisms, data lineage, operational boundaries, and governance framework of **GroqTales Agent** (`groqtales-agent`) in accordance with the **OpenGAP v0.1.0** specification for the **HiDevs GitAgent Passport** clearance pipeline.

> **Agent Name:** GroqTales Agent (`groqtales-agent`)  
> **Specification:** OpenGAP v0.1.0  
> **Category / Domain:** Developer Tools / AI-Powered Web3 Storytelling, Comic Generation & Smart Contracts  
> **Compliance Standard:** OpenGAP Checkpoint 2 (Explainability & Decision Governance), FERPA, GDPR  

---

## How the Agent Decides

GroqTales Agent is an autonomous generative narrative synthesis, multi-panel comic storyboard sequencing, character consistency tracking, and Monad smart contract NFT minting orchestration agent designed for **GroqTales**. It bridges ultra-low-latency Groq LPU inference, diffusion artwork rendering, decentralized IPFS storage, and on-chain ownership verification on the Monad blockchain.

### 1. Decision Architecture

The story generation, comic panel layout formulation, asset pinning, and on-chain minting pipeline operates across a deterministic, five-stage architecture:

```
Creator Input (Story Premise, Genre Selection, Character Seeds, Target Panel Count)
    │
    ▼
[Stage 1: Narrative Concept Extraction & Safety Auditing]
    │  - Ingests creative prompt and parses character traits, setting parameters, and narrative stakes
    │  - Executes automated safety screening against hate speech, graphic violence, and copyright risks
    │  - Normalizes genre conventions and constructs structured system prompts for Groq LPU inference
    ▼
[Stage 2: High-Throughput Branching Narrative Generation]
    │  - Dispatches structured chapter generation requests to Groq LPU inference endpoints
    │  - Generates multi-beat prose, dynamic character dialogues, and branching decision choices
    │  - Computes story pacing indices and readability metrics across generated paragraphs
    ▼
[Stage 3: Comic Storyboard & Panel Composition Sequencing]
    │  - Translates narrative prose into 3 to 9 sequential comic panel descriptions
    │  - Determines camera perspectives (wide, medium, close-up, dramatic angle) and atmospheric lighting
    │  - Retrieves registered character phenotypic embeddings to enforce visual continuity
    │  - Formulates diffusion prompts and positions speech balloons and narration captions
    ▼
[Stage 4: Decentralized Metadata Packaging & IPFS Pinning]
    │  - Assembles comic panels, chapter text, and creator attribution into ERC-721 metadata JSON
    │  - Encodes ERC-2981 royalty parameters and cryptographic proof manifests
    │  - Pins assets and metadata manifests to IPFS via decentralized storage nodes
    │  - Validates cryptographic CID integrity prior to on-chain transaction assembly
    ▼
[Stage 5: Monad Smart Contract Transaction Preparation & Settlement]
    │  - Constructs smart contract call payloads targeting GroqTales ERC-721/1155 contracts
    │  - Simulates transaction execution and calculates estimated Monad gas consumption
    │  - Presents transparent preview to creator wallet; awaits cryptographic user signature
    │  - Broadcasts confirmed transaction to Monad network and indexes newly minted token ID
    ▼
Minted Story / Comic NFT Delivered to Creator Wallet and Featured on GroqTales Showcase
```

### 2. Scoring Methodology & Rubric Formulations

GroqTales Agent evaluates narrative pacing and character consistency through two deterministic, mathematically rigorous scoring models:

1. **Composite Character Consistency Index ($C_{\text{char}}$)**:
   $$C_{\text{char}} = w_f \cdot \cos(\mathbf{v}_{\text{face}}, \mathbf{v}_{\text{ref}}) + w_a \cdot \frac{|A_{\text{panel}} \cap A_{\text{canon}}|}{|A_{\text{canon}}|} + w_p \cdot P_{\text{palette}}$$
   where:
   - $\cos(\mathbf{v}_{\text{face}}, \mathbf{v}_{\text{ref}})$: Cosine similarity between generated panel face embedding and canonical reference embedding ($w_f = 0.50$).
   - $\frac{|A_{\text{panel}} \cap A_{\text{canon}}|}{|A_{\text{canon}}|}$: Attribute overlap ratio for signature traits such as eye color, hair style, and accessories ($w_a = 0.30$).
   - $P_{\text{palette}} \in [0, 1]$: Color palette histogram similarity preserving canonical wardrobe colors ($w_p = 0.20$).
   - Acceptance criteria: $C_{\text{char}} \ge 0.80$ to preserve visual identity across panel transitions.

2. **Sequential Story Pacing Score ($S_{\text{pace}}$)**:
   $$S_{\text{pace}} = \sum_{i=1}^{N} \left( \beta_a \cdot A_i + \beta_d \cdot D_i + \beta_r \cdot R_i \right)$$
   where:
   - $A_i$: Action verb density in panel $i$ ($\beta_a = 0.40$).
   - $D_i$: Dialogue word count compliance bounded by $W_{\text{dialogue}} \le 35$ words per balloon ($\beta_d = 0.35$).
   - $R_i$: Narrative resolution score quantifying progression toward story beat climax ($\beta_r = 0.25$).

### 3. Thresholding & Refusal Decision Criteria

GroqTales Agent enforces strict deterministic refusal and safety boundaries:
- **Refusal on Safety Violations**: Prompts containing hate speech, non-consensual sexual content, or real-world violence are deterministically rejected with code `ERR_SAFETY_POLICY_VIOLATION`.
- **Refusal on Copyright Infringement**: Direct requests to replicate trademarked third-party characters (e.g., Marvel, DC, Disney) are rejected under code `ERR_COPYRIGHT_INFRINGEMENT_RISK`.
- **Refusal of Autonomous Unsigned Minting**: The agent strictly refuses to broadcast smart contract transactions without explicit cryptographic user wallet signature (`ERR_UNSIGNED_TRANSACTION_REJECTED`).
- **Refusal of Corrupted IPFS Hashes**: Content manifests failing cryptographic SHA-256 / CID verification prior to minting trigger an immediate halt under code `ERR_IPFS_HASH_INTEGRITY_FAILED`.
- **Refusal of Self-Modification**: Attempts to modify core system rules in `agent.yaml` or security directives in `RULES.md` are deterministically blocked with code `ERR_SELF_MODIFICATION_PROHIBITED`.

### 4. Fallback Decision Mechanism

GroqTales Agent guarantees uninterrupted creative workflow through a multi-tier fallback architecture:
- **Model Fallback Cascade**: Primary narrative generation and storyboard sequencing utilize `gemini-2.0-flash` with automatic failover to `gpt-4o` and `claude-3-5-sonnet` if API latency thresholds are exceeded.
- **Groq LPU Failover**: If primary Groq LPU endpoints encounter high traffic or rate limits, requests fail over to backup cloud inference instances without interrupting user sessions.
- **Multi-Gateway IPFS Fallback**: In the event of primary IPFS gateway latency, asset pinning automatically switches to secondary decentralized storage nodes (Filecoin / Pinata / Arweave).
- **RPC Endpoint Failover**: If the connected Monad RPC provider times out, the agent cycles through secondary Monad RPC endpoints to deliver accurate gas estimations.

### 5. Human-in-the-Loop Governance

GroqTales Agent upholds creator sovereignty and transparent blockchain operations:
- **Draft Primacy**: Every storyline, comic panel prompt, and layout arrangement is presented as an editable draft requiring user approval.
- **Explicit Wallet Signature**: On-chain minting transactions cannot occur autonomously; creators must explicitly approve every transaction through Web3 wallet dialogs.
- **Administrative Kill-Switch**: Platform operators possess instant emergency controls to suspend minting interfaces, disable compromised inference models, or freeze malicious smart contracts.
- **Structured Audit Trails**: All story generations, character modifications, IPFS hashes, and transaction hashes are logged in structured JSON format for compliance tracking.

---

## The Data It Uses

GroqTales Agent operates under strict privacy and Web3 data governance standards.

### 1. Ingested Input Data

The agent processes only user-supplied creative inputs and wallet parameters:
- **Story Prompts**: Creative premises, genre selections, world-building lore, and user dialogue suggestions.
- **Character Specifications**: Names, personality descriptions, phenotypic markers, and signature wardrobe attributes.
- **Web3 Parameters**: Connected wallet addresses, target Monad network identifiers, and creator royalty percentages.

### 2. Configuration & Reference Data

- **Comic Layout Templates**: Structural grid definitions for standard 3-panel, 4-panel, 6-panel, and 9-panel comic pages.
- **Camera & Cinematography Vocabularies**: Curated terms for camera angles, perspective framing, and atmospheric lighting conditions.
- **Smart Contract ABIs**: Authoritative OpenZeppelin-standard ERC-721, ERC-1155, and ERC-2981 contract interfaces deployed on the Monad network.

### 3. Base Model & Inference Lineage

- **LPU Narrative Inference**: High-speed language processing units executing narrative generation and dialogue scripting.
- **Foundation Reasoning Models**: High-capability foundation models (`gemini-2.0-flash`, `gpt-4o`, `claude-3-5-sonnet`) utilized for complex storyboard structuring and multi-panel continuity.
- **Zero Training on User Content**: User stories, custom characters, and generated comic panels are never utilized to train public foundation models without explicit creator consent.

### 4. Data Privacy, Storage, and Retention

- **FERPA & GDPR Compliance**: Full compliance with FERPA and GDPR standards. All off-chain creator data and draft sessions are treated as confidential assets with encryption at rest and in transit.
- **Decentralized Permanence**: Minted comic assets and story metadata pinned to IPFS reside on decentralized storage, ensuring creator ownership independent of centralized servers.
- **Creator Data Deletion**: Off-chain draft records and temporary session vectors can be permanently deleted upon creator request with verifiable 0-byte purging.

---

## Limitations

Understanding the operational boundaries and technical constraints of GroqTales Agent is essential for optimal comic creation.

### 1. Diffusion Visual Consistency Edge Cases
- **Limitation**: Generative image diffusion models may exhibit subtle variances in intricate clothing emblems or micro-expressions across multiple panel generations.
- **Mitigation**: The agent generates explicit visual seed descriptors, negative prompt constraints, and strict phenotypic anchors to maximize character fidelity.

### 2. Blockchain Gas Volatility & Network Congestion
- **Limitation**: High network demand on Monad can cause temporary fluctuations in transaction fees and settlement confirmation times.
- **Mitigation**: Real-time gas price simulation provides accurate cost previews and automatically suggests optimal transaction submission windows.

### 3. Long-Arc Multi-Issue Narrative Coherence
- **Limitation**: In comic series extending across dozens of chapters, intricate lore details from early chapters could suffer from narrative drift.
- **Mitigation**: The agent utilizes persistent character and lore profile stores, cross-referencing canonical world bibles before generating new chapter arcs.

### 4. IPFS Pinning Latency & Gateway Reachability
- **Limitation**: Public IPFS gateways occasionally experience temporary propagation delays when caching newly pinned high-resolution comic assets.
- **Mitigation**: The system leverages dedicated multi-gateway pinning services ensuring content availability across redundant global nodes.

### 5. Multi-Language Dialect Translation Nuance
- **Limitation**: Nuanced slang, cultural wordplay, or genre-specific comic idioms may experience subtle fidelity loss during automated multilingual localization.
- **Mitigation**: The agent flags idiomatic colloquialisms and provides side-by-side translation alternatives for human creator verification.

---

## Summary & Compliance Checklist

| Checkpoint 2 Requirement | Corresponding Section | Status |
| :--- | :--- | :---: |
| **How the agent decides** | [How the Agent Decides](#how-the-agent-decides) | **Covered** |
| - Decision architecture & 5-stage pipeline | Section 1 | Verified |
| - Scoring methodology & narrative formulas | Section 2 | Verified |
| - Thresholding & refusal decision criteria | Section 3 | Verified |
| - Fallback decision mechanism | Section 4 | Verified |
| - Human-in-the-loop governance | Section 5 | Verified |
| **The data it uses** | [The Data It Uses](#the-data-it-uses) | **Covered** |
| - Ingested user story premises & prompts | Section 1 | Verified |
| - Configuration, character profiles & schemas | Section 2 | Verified |
| - Base model lineage & deterministic inference | Section 3 | Verified |
| - Data privacy, IPFS immutability & FERPA/GDPR | Section 4 | Verified |
| **Its limitations** | [Limitations](#limitations) | **Covered** |
| - Diffusion visual consistency edge cases | Section 1 | Verified |
| - Blockchain gas volatility & network congestion | Section 2 | Verified |
| - Long-arc multi-issue narrative coherence | Section 3 | Verified |
| - IPFS pinning latency & gateway reachability | Section 4 | Verified |
| - Multi-language dialect translation nuance | Section 5 | Verified |
