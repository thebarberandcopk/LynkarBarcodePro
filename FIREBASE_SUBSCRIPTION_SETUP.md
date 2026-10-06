# Subscription settings

After the main admin is bootstrapped, publish `firebase/firestore.rules`.

The app will create/read:
`settings/subscriptions`

The main admin can edit:
- Plan name
- Price
- Billing period
- Monthly tag/label generation limit (0 = unlimited)
- User-seat limit (0 = unlimited)
- Feature flags
- Allowed export formats: PDF, JPG, EPS, AI, XLSX, JSON
- Support email
- WhatsApp support number

The public login page reads this document to display current pricing. No password, token, or private credential is stored there.
