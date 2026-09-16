# Sonvashi Devi Bhawan – Home Manager

A mobile-first home management app using HTML, CSS and vanilla JavaScript.

## Features
- Monthly dashboard
- Tenant rent and partial payments
- Floor-wise electricity meter readings and bill sharing
- Separate milk customers with morning/evening entries, monthly calendar and automatic value
- Labour work entries with per-day wage calculation and paid/due status
- Money owed tracking for amounts you need to pay or receive
- House/milk/cow/repair expenses
- Useful service contacts with click-to-call
- CRUD for main records
- Month navigation/history
- Responsive mobile UI

## Run immediately
Open `index.html` through a simple local web server or deploy the folder to GitHub Pages. The project starts in **local demo mode**, using browser localStorage.

## Connect Firebase (no Storage required)
1. Create a Firebase project.
2. Enable **Authentication > Email/Password** and manually create only your family accounts. Do not add public signup.
3. Create **Cloud Firestore**.
4. Firebase project configuration is already connected in `app.js`.
5. Firebase mode is already enabled.
6. Deploy to GitHub Pages.

Suggested Firestore rules (replace the emails with your actual family account emails):

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /homeData/{document=**} {
      allow read, write: if request.auth != null
        && request.auth.token.email in [
          'family1@example.com',
          'family2@example.com'
        ];
    }
  }
}
```

Firebase Web config is expected to be visible in a frontend app. Do not put passwords, Admin SDK credentials, service-account JSON, or other secrets in this repository.

## GitHub Pages
Upload these files to a repository, then enable Pages under repository Settings > Pages. Firebase modules are loaded from Google's CDN, so no npm/build step is needed.
