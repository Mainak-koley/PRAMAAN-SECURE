# PRAMAAN — SIH26190

Secure Digital Document Management System for Legal and Investigation Documents.

## Frontend-only hackathon prototype

This package intentionally contains **frontend only**. No backend/API server is required to run the prototype. Backend/API integration can be added later by the backend team.

### Run

```bash
npm install
npm run dev
```

Open the Vite URL, normally `http://localhost:5173/`.

### Demo login

- Email: `demo@pramaan.gov`
- Password: `Pramaan@2026!`

### Main frontend features

- Responsive dashboard, cases, documents and evidence workflows
- Drag-and-drop document upload
- SHA-256 hashing using Web Crypto API
- Browser document preview for uploaded PDF/image/text files
- Local My Vault using IndexedDB with preview/download/remove
- Verification and digital-signature prototype workflows
- Chain of Custody timeline and local event recording
- PII detection and animated redaction workflow
- Pramaan AI local assistant with history
- Reports and downloadable JSON artifacts
- Audit logs and security alerts
- Roles & Permissions local prototype matrix
- Offline mode and Sync Center with timestamped history
- Dark mode
- English / Hindi / Marathi interface navigation
- Profile update, picture, data download and logout
- Animated page transitions, charts, cards, modals and upload states
- Mobile/tablet/desktop responsive layouts

### Important status labels

Government integrations, advanced cryptography, OCR/AI infrastructure and backend authorization are clearly treated as prototype/integration-ready where applicable. This frontend does not claim live government API access.
