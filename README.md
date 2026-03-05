⚖️ LexChain: Blockchain-Based Digital Evidence Integrity

LexChain est une solution décentralisée (DApp) conçue pour sécuriser la chaîne de responsabilité (Chain of Custody) des preuves numériques. En utilisant la technologie blockchain Ethereum et le stockage IPFS, le projet garantit qu’une preuve judiciaire ne peut être ni modifiée ni supprimée ni contestée.

---

Sommaire

1. Problématique
2. Solution LexChain
3. Architecture Technique
4. Acteurs & Rôles
5. Fonctionnement (Workflow)
6. Installation

---

🔍 Problématique

Dans le système judiciaire traditionnel, les preuves numériques (vidéos de surveillance, photos, documents) sont vulnérables :

* Altération : Un administrateur peut modifier un fichier de base de données.
* Suppression : risque de perte de preuves cruciales par erreur ou par malveillance.
* Contestation : Difficulté à prouver l’origine exacte et la date de création de la preuve.

---

💡 Solution LexChain

LexChain transforme la preuve numérique en un actif immuable :

* Hachage cryptographique (SHA-256) : Chaque preuve possède une empreinte unique.
* Ancrage Blockchain : L’empreinte est gravée dans le registre Ethereum (Sepolia Testnet).
* Stockage IPFS (CID) : Les fichiers sont stockés de manière décentralisée via un identifiant de contenu (CID).
* Vérification Automatisée : Comparaison instantanée entre le Hash stocké “On-chain” et le fichier “Off-chain”.

---

🏗️ Architecture Technique 

LexChain repose sur une architecture décentralisée en couches (N-Tier DApp Architecture), garantissant sécurité, scalabilité et réduction des coûts de transaction (Gas optimization).

1. Smart Contract Layer 
 
Language: Solidity.

Framework: Hardhat (pour le développement, les tests unitaires et le déploiement).

Security Standard: OpenZeppelin AccessControl (RBAC) pour la gestion stricte des rôles (Ministère, Police, Juge).

Logic: Gestion de l'immuabilité des empreintes (Hashes) et de la traçabilité des dépôts.

2. Decentralized Storage Layer 
   
Protocol: IPFS (InterPlanetary File System).

Provider: Pinata SDK.

Logic: Stockage des fichiers volumineux (vidéos, photos). Seul le CID (Content Identifier) est stocké sur la Blockchain pour optimiser les coûts.

3. Application Layer (Frontend / Web3)
   
Framework: Next.js 14 ou React.js.

Styling: Tailwind CSS + Shadcn/UI .

Blockchain Interaction: Ethers.js v6 ou Wagmi/Viem.

Wallet: MetaMask (Fournisseur d'identité et signature de transactions).

4. Security & Cryptography
   
Hashing Algorithm: SHA-256 (calculé côté client pour garantir l'intégrité avant même l'upload).

Authentication: Signatures numériques via les clés privées Ethereum.

---

👥 Acteurs & Rôles

Le système repose sur une gouvernance stricte (Role-Based Access Control) :

1-Ministère ( Admin	/ Super-User ) :	Gère la Whitelist (Ajout/Révocation des officiers).

2-Officier ( Police /	Uploader ) :	Calcule le Hash, upload sur IPFS et enregistre sur la Blockchain.

3-Juge ( Expert /	Vérificateur	) : Consulte les preuves et valide leur intégrité via la DApp.


---

🔄 Fonctionnement (Workflow)

1. Enregistrement : Le Ministère autorise l’adresse Wallet de l’officier.
2. Dépôt : L’officier télécharge une preuve. Le système génère un CID (via IPFS) et un hash (SHA-256).
3. Validation Blockchain : Une transaction est envoyée pour lier le CaseID, le CID et le Hash à l’adresse de l’officier avec un Timestamp.
4. Vérification : Le juge accède au dossier. La DApp télécharge le fichier depuis IPFS, recalcule son hash (frontend) et le compare avec celui de la blockchain.
  * ✅ Match : Preuve Intégrée.
  * ❌ Mismatch : Preuve Corrompue.

--- 

📊 Diagrammes du Système

A. Cas d'Utilisation (Use Case)
Le diagramme suivant illustre les interactions entre les différents acteurs (Ministère, Police, Juge) et les fonctionnalités de la plateforme.

![Import OVA](https://github.com/user-attachments/assets/276fea61-8750-424e-83ff-7a20e5e94c47) 


B. Diagramme de Séquence (Workflow Technique)
Ce diagramme détaille le flux de données lors de l'enregistrement d'une preuve, garantissant que le fichier est stocké sur IPFS tandis que son empreinte (Hash) est sécurisée sur la Blockchain.

![Import OVA](https://github.com/user-attachments/assets/7d23351d-ae17-48f5-b92b-5923f0957bdf)

---

🚀 6. Installation et configuration

Cette section décrit les étapes nécessaires pour mettre en place l’environnement de développement local.

📋 Prérequis

* Node.js (version 18.x ou supérieure)
* npm (installé avec Node.js)
* VS Code (ou un autre éditeur de texte)

🛠️ Étapes d’installation

1. Initialisation du dossier racine
Créez un dossier pour le projet et initialisez le gestionnaire de paquets npm + Hardhat .


![Import OVA](https://github.com/user-attachments/assets/35393d2d-4823-45d6-88b8-603dbdca3fa1)

2.Initialisation du projet Hardhat 

![Import OVA](https://github.com/user-attachments/assets/99466fe4-4fb9-4da1-80f9-3bd54eca9eee)

![Import OVA](https://github.com/user-attachments/assets/5c8c465a-9493-4aa2-82cf-425bed921bd2)

![import OVA](https://github.com/user-attachments/assets/c250b7c7-61a0-47ca-b4ca-ec5e3f5bc3c5)

3-Installation OpenZeppelin

![Import OVA](https://github.com/user-attachments/assets/88101795-92c3-4c73-9f74-0416debca6c0)


---

 7. Développement du Smart Contract (LexChain.sol)

 Cette étape marque le début du développement de la logique métier sur la blockchain. Le contrat LexChain est le cœur du système, gérant l’immuabilité et l’accès sécurisé aux preuves.

 Description du Contrat

Le contrat LexChain.sol utilise les standards d’OpenZeppelin pour garantir une sécurité maximale :

* Access Control: Seuls les utilisateurs ayant le rôle POLICE_ROLE peuvent enregistrer des preuves.
* Struct Evidence : Stocke de manière structurée le hash du fichier (Intégrité) et le CID d’IPFS (stockage décentralisé).
* Immuabilité : Une fois enregistrée, une preuve ne peut ni être modifiée ni supprimée.
---
Commande de Compilation

Pour transformer le code Solidity en bytecode compréhensible par la machine virtuelle Ethereum (EVM), nous utilisons :

"" npx hardhat compile ""

![Import OVA](https://github.com/user-attachments/assets/f8d0e3c3-d5ad-4607-8204-fde1a2ea3522)

![Import OVA](https://github.com/user-attachments/assets/91cb7c09-5cc3-4c60-ba88-948e5122093c)



