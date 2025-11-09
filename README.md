# React Firebase Chat App

A real-time chat application built with React, Vite, and Firebase.

## Features

- 🔥 Firebase Authentication
- 💬 Real-time messaging with Firestore
- 📁 File uploads with Firebase Storage
- 🎨 Modern React with Hooks
- ⚡ Fast development with Vite
- 🚀 Production-ready build configuration

## Prerequisites

Before you begin, ensure you have:
- Node.js (v16 or higher) installed
- A Firebase account (free tier works great)
- npm or yarn package manager

## Firebase Setup

1. **Create a Firebase Project**
   - Go to [Firebase Console](https://console.firebase.google.com/)
   - Click "Add project" and follow the setup wizard
   - Enable Google Analytics (optional)

2. **Enable Firebase Services**
   - **Authentication**: Go to Authentication > Sign-in method > Enable Email/Password
   - **Firestore Database**: Go to Firestore Database > Create database > Start in test mode
   - **Storage**: Go to Storage > Get started > Start in test mode

3. **Get Firebase Configuration**
   - Go to Project Settings (⚙️ icon)
   - Scroll down to "Your apps" section
   - Click the web icon (`</>`) to register your app
   - Copy the configuration object

## Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/shyamreddy1904/react-firebase-chat.git
   cd react-firebase-chat
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure environment variables**
   - Copy `.env.example` to `.env`
   ```bash
   cp .env.example .env
   ```
   - Open `.env` and replace the placeholder values with your Firebase config:
   ```env
   VITE_API_KEY=your_actual_api_key
   VITE_AUTH_DOMAIN=your_project_id.firebaseapp.com
   VITE_PROJECT_ID=your_project_id
   VITE_STORAGE_BUCKET=your_project_id.appspot.com
   VITE_MESSAGING_SENDER_ID=your_messaging_sender_id
   VITE_APP_ID=your_app_id
   ```

4. **Start development server**
   ```bash
   npm run dev
   ```
   The app will open at `http://localhost:3000`

## Building for Production

Build the app for production:
```bash
npm run build
```

Preview the production build locally:
```bash
npm run preview
```

## Deployment Options

### Option 1: Firebase Hosting (Recommended)

1. **Install Firebase CLI**
   ```bash
   npm install -g firebase-tools
   ```

2. **Login to Firebase**
   ```bash
   firebase login
   ```

3. **Initialize Firebase Hosting**
   ```bash
   firebase init hosting
   ```
   - Select your Firebase project
   - Set public directory to: `dist`
   - Configure as single-page app: `Yes`
   - Don't overwrite `dist/index.html`

4. **Deploy**
   ```bash
   npm run deploy:firebase
   ```
   Or manually:
   ```bash
   firebase deploy
   ```

### Option 2: Vercel

1. **Install Vercel CLI**
   ```bash
   npm install -g vercel
   ```

2. **Deploy**
   ```bash
   npm run deploy:vercel
   ```
   Or:
   ```bash
   vercel --prod
   ```

3. **Add environment variables in Vercel Dashboard**
   - Go to your project settings
   - Add all `VITE_*` environment variables

### Option 3: Netlify

1. **Install Netlify CLI**
   ```bash
   npm install -g netlify-cli
   ```

2. **Deploy**
   ```bash
   npm run deploy:netlify
   ```
   Or:
   ```bash
   netlify deploy --prod
   ```

3. **Add environment variables in Netlify Dashboard**
   - Go to Site settings > Build & deploy > Environment
   - Add all `VITE_*` environment variables

### Option 4: GitHub Pages

1. **Update `vite.config.js` base path**
   ```js
   base: '/your-repo-name/'
   ```

2. **Build and deploy**
   ```bash
   npm run build
   # Push the dist folder to gh-pages branch
   ```

## Firebase Security Rules

### Firestore Rules (Development)
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

### Storage Rules (Development)
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

> ⚠️ **Important**: Update these rules for production to add proper validation and security!

## Project Structure

```
react-firebase-chat/
├── public/              # Static assets
├── src/
│   ├── components/      # React components (add your components here)
│   ├── lib/
│   │   └── firebase.js  # Firebase configuration
│   ├── App.jsx          # Main app component
│   ├── main.jsx         # Entry point
│   └── index.css        # Global styles
├── .env                 # Environment variables (create from .env.example)
├── .env.example         # Environment variables template
├── .gitignore           # Git ignore rules
├── index.html           # HTML template
├── package.json         # Dependencies and scripts
├── vite.config.js       # Vite configuration
└── README.md            # This file
```

## Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run lint` - Run ESLint
- `npm run deploy:firebase` - Build and deploy to Firebase Hosting
- `npm run deploy:vercel` - Build and deploy to Vercel
- `npm run deploy:netlify` - Build and deploy to Netlify

## Troubleshooting

### Firebase initialization error
- Make sure all environment variables are set correctly in `.env`
- Verify your Firebase project is active
- Check that Firebase services (Auth, Firestore, Storage) are enabled

### Build errors
- Delete `node_modules` and `package-lock.json`
- Run `npm install` again
- Clear Vite cache: `rm -rf node_modules/.vite`

### Deployment issues
- Ensure `.env` variables are added to your hosting platform
- Check that the `dist` folder is being built correctly
- Verify Firebase configuration is correct

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is open source and available under the [MIT License](LICENSE).

## Support

If you have any questions or run into issues, please open an issue on GitHub.

## Acknowledgments

- Built with [React](https://react.dev/)
- Powered by [Firebase](https://firebase.google.com/)
- Bundled with [Vite](https://vitejs.dev/)
