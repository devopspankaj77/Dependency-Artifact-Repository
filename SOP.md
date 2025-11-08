🧩 STEP 1 — Setup package.json for Each Node Version
📂 Folder:
vault/node18/package.json, vault/node20/package.json etc.
Example:

{
  "name": "@org/node18-deps",
  "version": "1.0.0",
  "private": true,
  "description": "Approved production dependencies for Node 18 apps",
  "dependencies": {
    "express": "^4.19.0",
    "axios": "^1.7.2",
    "dotenv": "^16.4.1"
  }
}

🔹 Sirf approved dependencies rakho.
🔹 package-lock.json generate karne ke liye ek baar manually run karo:

cd vault/node18
npm install --package-lock-only

Ye lockfile deterministic build ke liye zaroori hai.



---
⚙️ STEP 2 — Add and Configure the Builder Pipeline

📂 File: azure-pipelines/dependency-vault-builder.yml
