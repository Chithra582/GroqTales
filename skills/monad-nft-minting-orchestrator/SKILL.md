---
name: monad-nft-minting-orchestrator
description: Orchestrates IPFS metadata preparation, ERC-721/ERC-1155 minting transactions, and royalty distribution on the Monad network.
---

# Monad NFT Minting Orchestrator

## Overview
The `monad-nft-minting-orchestrator` skill bridges completed stories and comics with the Monad blockchain. It packages multimedia assets, verifies decentralized IPFS pinning, constructs smart contract transaction calls, and monitors on-chain settlement with transparent gas estimations.

## Core Capabilities
- **Decentralized Metadata Assembly**: Compiles comic page artwork, story transcripts, creator attribution, and attributes into OpenSea/ERC-721 compliant JSON.
- **IPFS Pinning & CID Validation**: Pushes artwork and metadata to decentralized storage gateways and verifies cryptographic content hashes.
- **Monad Contract Call Construction**: Encodes minting functions for ERC-721 and ERC-1155 contracts deployed on Monad.
- **ERC-2981 Royalty Encoding**: Embeds creator royalty percentages and payout addresses directly into on-chain metadata.

## Inputs
- `story_id`: Internal unique identifier of the story or comic.
- `artwork_url`: Local or staged URL of the final comic cover and page spreads.
- `creator_wallet`: Monad network EVM wallet address of the creator.
- `royalty_percentage`: Creator secondary sale royalty basis points (e.g., 500 for 5%).

## Outputs
- `ipfs_metadata_uri`: Permanent `ipfs://` URI pointing to the immutable metadata manifest.
- `transaction_payload`: Encoded hex data ready for wallet signature and dispatch.
- `estimated_gas`: Projected transaction fee in MON tokens on the Monad network.
