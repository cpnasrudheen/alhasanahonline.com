AL HASANA ONLINE - WORKING ADMIN SETUP

Admin Email: alhasanah.dw@gmail.com
Password: Use the password you created in Firebase Authentication.

FIRESTORE RULES (replace current test rules):
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    function isAdmin() { return request.auth != null && request.auth.token.email == 'alhasanah.dw@gmail.com'; }
    match /exams/{id} { allow read: if true; allow write: if isAdmin(); }
    match /studyMaterials/{id} { allow read: if true; allow write: if isAdmin(); }
    match /announcements/{id} { allow read: if true; allow write: if isAdmin(); }
    match /examResults/{id} { allow create: if true; allow read, update, delete: if isAdmin(); }
  }
}

Important: Public leaderboard cannot read examResults with these secure rules. The current page will show leaderboard only if read access is allowed. For production privacy, keep results admin-only or create a separate publicLeaderboard collection using a server/Cloud Function.
