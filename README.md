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

Le projet utilise une stack technologique moderne et professionnelle :

* Blockchain : Ethereum (Solidity 0.8.x).
* Framework de Dev : Hardhat (environnement de test et de déploiement).
* Stockage : IPFS (InterPlanetary File System) via Pinata.
* Frontend : Next.js / Tailwind CSS / Ethers.js.
* Sécurité : OpenZeppelin (Role-Based Access Control).

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
4. Vérification : Le juge accède au dossier. La DApp télécharge le fichier depuis IPFS, recalcule son hash et le compare avec celui de la blockchain.
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


