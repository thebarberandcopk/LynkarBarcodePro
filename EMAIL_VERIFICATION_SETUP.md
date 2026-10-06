# Email Verification + Automatic 3-Day Trial

## New user flow

1. User creates a Firebase account.
2. Firestore creates `users/{uid}` with `status: pending`, `subscription: trial`, and `trialStart/trialEnd: null`.
3. Firebase sends the built-in email verification link.
4. User clicks the verification link.
5. LynkKar checks Firebase `emailVerified` and automatically changes the account to:
   - `status: active`
   - `subscription: trial`
   - `trialStart: current time`
   - `trialEnd: current time + 3 days`
6. No admin approval is required.

## Firebase Console requirements

- Enable **Email/Password** under Authentication → Sign-in method.
- Add the production domain to Authentication → Settings → Authorized domains.
- Customize the verification email template under Authentication → Templates if desired.

## Firestore rules

Publish `firebase/firestore.rules` in Firebase Console → Firestore Database → Rules.

The activation rule requires `request.auth.token.email_verified == true`, so a user cannot self-activate an unverified account by editing Firestore.
