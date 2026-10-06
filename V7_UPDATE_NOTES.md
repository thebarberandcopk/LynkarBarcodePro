# LynkKar Pro Label Studio V7 Update

## Changes

### Cloud status
- Cloud status now distinguishes Connected, Cached, Syncing, Cloud Error, and actual Offline browser state.
- Firestore label listener reports a successful connection instead of showing Offline merely because a listener error occurred.
- Browser online/offline events automatically update the status and retry private label sync.

### Faster login
- Authentication now starts immediately instead of waiting for subscription pricing/settings to finish loading.
- Removed the duplicate user-profile read/initial snapshot race from the login flow.
- Dashboard opens immediately after the account profile is verified.
- Added a short signing-in overlay so the transition is clear instead of appearing frozen.
- Live user profile listener remains active for approval, subscription and account-state changes.

### Vector PDF
Added a prominent combined export option:
- Download QR & Barcode as PDF (Vector)

Existing individual vector PDF exports remain available.

### Private accounts
Labels remain stored per Firebase UID under:
`users/{uid}/labels/{labelId}`

No shared/global label collection is used.
