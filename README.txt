AL HASANA ONLINE - COMPLETE REPLACEMENT PACKAGE

FILES
1. index.html       - Complete website
2. firestore.rules  - Firestore security rules

SETUP
1. Extract ZIP.
2. Replace your old index.html with this new index.html in GitHub.
3. Firebase Console > Firestore Database > Rules:
   Copy all content from firestore.rules and Publish.
4. Firebase Authentication > Sign-in method:
   Enable Email/Password.
5. Use your existing admin email/password to login.

FEATURES
- Admin Login
- Create & Publish Exams
- Add unlimited questions
- Add/remove options
- Select correct answer
- Edit/Delete published exams
- Public exam list
- Student Name + Phone + Place
- Automatic marks and percentage
- Save results to Firestore
- Admin result list with search
- View individual answer details
- Delete results
- Study Materials
- Announcements

IMPORTANT
This version intentionally does NOT write to a separate 'leaderboard' collection.
That avoids the previous result-save failure caused by the extra Firestore write.
