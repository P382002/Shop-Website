# Sri Vignaraja Fabrics – Shop (Firebase version)

- `index.html` – customer shop (live products, cart, checkout, WhatsApp order)
- `admin.html` – owner panel at `/admin` (secure login, products, live orders)
- `firebase-config.js` – your Firebase keys (you paste them here)
- `firestore.rules` – database security rules (you paste them into Firebase)

## Setup (about 10 minutes, all free)

### 1. Create the Firebase project
Go to https://console.firebase.google.com > Add project > give it a name > continue (Google Analytics not needed).

### 2. Register the web app and copy the config
Project overview > click the **</>** (Web) icon > give a nickname > Register app.
Copy the `firebaseConfig` values into **firebase-config.js**.

### 3. Create the database
Build > **Firestore Database** > Create database > choose location **asia-south1 (Mumbai)** > Start in **production mode**.

### 4. Create the owner login
Build > **Authentication** > Get started > Sign-in method > enable **Email/Password**.
Then Users tab > **Add user** > enter your email + a strong password. This is what you use on `/admin`.

### 5. Add the security rules
Firestore Database > **Rules** tab > delete everything > paste the contents of **firestore.rules**.
Replace `OWNER_EMAIL_HERE` with the exact email from step 4 > **Publish**.

### 6. Deploy
Push this folder to GitHub, then in Vercel: Add New > Project > import repo > Framework "Other" > Deploy.
Shop: `https://your-project.vercel.app/`   Admin: `https://your-project.vercel.app/admin`

### 7. Final touches
- In Firebase > Authentication > Settings > **Authorized domains**, add `your-project.vercel.app` (and your own domain if you connect one).
- Log in at `/admin` > Settings > enter your WhatsApp number (e.g. 919876543210).
- Add your first products.

## How it works
- Products you add appear for every customer instantly.
- Customer orders are saved to the database and show up live in Admin > Orders (with a WhatsApp customer button).
- Stock is reduced when you move an order from Pending to Confirmed (and restored if you cancel it).
- Customers can only create orders; only your login can read or change anything else.
