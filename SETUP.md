# 🚀 Quick Setup Guide

Your chat application is now fully built! Follow these steps to get it running:

## Step 1: Add Firebase Credentials

1. Open the `.env` file in the root directory
2. Replace the placeholder values with your actual Firebase configuration:

```env
VITE_API_KEY=your_actual_api_key
VITE_AUTH_DOMAIN=your_project_id.firebaseapp.com
VITE_PROJECT_ID=your_project_id
VITE_STORAGE_BUCKET=your_project_id.appspot.com
VITE_MESSAGING_SENDER_ID=your_messaging_sender_id
VITE_APP_ID=your_app_id
```

## Step 2: Enable Firebase Services

Go to your Firebase Console and enable:

1. **Authentication**
   - Navigate to Authentication > Sign-in method
   - Enable "Email/Password"

2. **Firestore Database** ✅ (Already done)
   - Set up security rules (see below)

3. **Storage**
   - Navigate to Storage > Get started
   - Set up security rules (see below)

### Firestore Security Rules
```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if request.auth != null;
    }
  }
}
```

### Storage Security Rules
```javascript
rules_version = '2';
service firebase.storage {
  match /b/{bucket}/o {
    match /{allPaths=**} {
      allow read, write: if request.auth != null;
    }
  }
}
```

## Step 3: Run the Application

The dev server should already be running. If not:

```bash
npm run dev
```

The app will open at http://localhost:3000

## ✨ Features Included

- ✅ User Registration & Login
- ✅ Real-time messaging
- ✅ User search and add contacts
- ✅ Profile pictures & avatars
- ✅ Image sharing in chats
- ✅ Online status indicators
- ✅ Last seen timestamps
- ✅ Profile management
- ✅ Responsive design
- ✅ Secure authentication

## 🎯 How to Use

1. **Register**: Click "Create account" and sign up with email/password
2. **Setup Profile**: Add your name, bio, and profile picture
3. **Find Users**: Search for other users by their username
4. **Start Chatting**: Click on a user to start a conversation
5. **Send Messages**: Type and send text messages or share images

## 📱 Deployment

When ready to deploy, build the app:

```bash
npm run build
```

Deploy to:
- **Firebase Hosting**: `npm run deploy:firebase`
- **Vercel**: `npm run deploy:vercel`  
- **Netlify**: `npm run deploy:netlify`

See the full README.md for detailed deployment instructions!

## 🐛 Troubleshooting

If you see a blank page:
- Make sure you've added your Firebase credentials to `.env`
- Check that all Firebase services are enabled
- Open the browser console for any error messages

## 🎨 Customization

- **Colors**: Edit the CSS files in `src/components/` and `src/pages/`
- **Logo**: Replace the SVG data URIs in `src/assets/assets.js`
- **Styling**: Modify component CSS files to match your brand

Enjoy your chat app! 💬
