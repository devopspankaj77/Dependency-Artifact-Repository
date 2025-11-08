# Dependency-Artifact-Repository
Cleaned dependencies are stored here for use in pipelines to save time

dependency-vault/
├── README.md
├── azure-pipelines/
│   ├── dependency-vault-builder.yml      # Pipeline YAML (for building and cleaning deps)
│   ├── consumer-app-pipeline.yml         # Example consumer pipeline
│   └── templates/
│       ├── steps-clean-deps.yml          # optional reusable step templates
│       └── steps-upload-to-blob.yml
│
├── vault/                                # all dependency sets per Node version
│   ├── node16/
│   │   ├── package.json
│   │   ├── package-lock.json
│   │   ├── node_modules/                 # (ignored in git, generated in pipeline)
│   │   └── metadata.json
│   ├── node18/
│   │   ├── package.json
│   │   ├── package-lock.json
│   │   ├── node_modules/                 # (ignored in git)
│   │   └── metadata.json
│   ├── node20/
│   │   ├── package.json
│   │   ├── package-lock.json
│   │   └── metadata.json
│
├── scripts/
│   ├── validate-lockfile.sh              # optional: checks lockfile consistency
│   ├── generate-metadata.js              # optional: custom metadata generator
│   └── post-upload-hook.sh               # optional: post-upload cleanup script
│
├── .gitignore
└── .npmrc                                # optional: internal feed auth for vault build


Each subfolder is version-specific Node runtime ke liye.
Har folder ke andar:

package.json → baseline dependencies (approved by your org)

package-lock.json → deterministic lock file

node_modules/ → pipeline me generate hota hai (not stored in Git)

metadata.json → pipeline se auto-generate hone wala info (Node version, audit report, build time, etc.)

Example:

vault/node18/package.json
