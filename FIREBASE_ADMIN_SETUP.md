# LynkKar Pro Label Studio — Firebase Admin Setup

## 1. Main administrator

Firebase Authentication does not automatically make an account an administrator. The first/main administrator must be designated in Firestore.

Use the existing Firebase Authentication account you want to be the owner/main admin (the account currently visible in Firebase Authentication).

1. Firebase Console → Authentication → Users.
2. Copy that account's **User UID**.
3. Firebase Console → Firestore → Data → `users`.
4. Open the document whose ID is that UID. If it does not exist, create a document with that UID.
5. Set at least these fields:
   - `role` = `admin` (string)
   - `status` = `active` (string)
   - `subscription` = `business` (string)
   - `name` = your admin name (string)
   - `email` = your admin email (string)
   - `createdAt` = current time/number
   - `updatedAt` = current time/number
6. Save it.

After this, sign out and sign back in. The dashboard will show the **Customers** admin tab.

## 2. Security model

- New signups are always created as `role = user` and `status = pending`.
- Pending users are immediately signed out and cannot enter the dashboard.
- Only the main admin role can approve/reject users and activate plans.
- The web UI does not contain an "Admin" role creation option.
- Firestore rules also prevent a normal user from changing their role/status/subscription.
- The admin cannot create another admin through the application because the `role` field is immutable.
- The main admin account itself cannot be deleted from the application.

## 3. Trial and subscription

Default trial: **3 days**.

A pending user does not get dashboard access during the trial until approved.
After approval, the 3-day trial starts. Pending time does not consume the trial.

When the trial expires, the dashboard locks automatically and the user must purchase a plan.
The admin can activate a paid plan for 30 days from the Customers tab after payment is confirmed.

Plans:
- Starter: PKR 999 / 30 days
- Pro: PKR 2,499 / 30 days
- Business: PKR 5,999 / 30 days

## 4. Important

Do not publish the new Firestore rules until the first admin user's Firestore document has been set to `role = admin`, otherwise no client account will have admin privileges.
