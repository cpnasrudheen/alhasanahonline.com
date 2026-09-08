AL HASANA ONLINE – COMPLETE SETUP

WHAT THIS VERSION DOES
======================
1. Admin Login using Firebase Authentication.
2. Only the configured admin email can open the Admin Dashboard.
3. Admin can Create & Publish an Exam.
4. Each exam can have unlimited Questions.
5. Each Question can have unlimited Options (minimum 2).
6. Admin selects the Correct Answer from a dropdown.
7. Published exams automatically appear for all website visitors.
8. Students enter Name + Phone Number and take the exam.
9. Score, percentage, full answers and submission time are saved.
10. Admin can search all exam participants.
11. Admin can view each participant's full answer details.
12. Admin can delete results.
13. Admin can edit or delete published exams.
14. Admin can add/delete Study Materials.
15. Admin can publish/delete Announcements.
16. Public leaderboard uses a separate collection without phone numbers.

IMPORTANT FIRESTORE RULES
=========================
Firebase Console → Firestore Database → Rules

Paste the following rules and click Publish:

rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {

    function isAdmin() {
      return request.auth != null
        && request.auth.token.email == 'alhasanah.dw@gmail.com';
    }

    // Published exams are visible to everyone. Only admin can create/edit/delete.
    match /exams/{examId} {
      allow read: if true;
      allow write: if isAdmin();
    }

    // Public learning materials
    match /studyMaterials/{materialId} {
      allow read: if true;
      allow write: if isAdmin();
    }

    // Public announcements
    match /announcements/{announcementId} {
      allow read: if true;
      allow write: if isAdmin();
    }

    // Full private results: students can submit, only admin can read/delete.
    match /examResults/{resultId} {
      allow create: if true;
      allow read, update, delete: if isAdmin();
    }

    // Public leaderboard contains NO phone number or answer details.
    match /leaderboard/{resultId} {
      allow read, create: if true;
      allow update, delete: if isAdmin();
    }
  }
}

FIREBASE AUTHENTICATION
=======================
Firebase → Authentication → Users

Make sure this admin user exists:
alhasanah.dw@gmail.com

Use the password you created for that Firebase Authentication user.

HOW TO ADD AN EXAM
==================
Admin Login
→ Create New Exam
→ Enter Exam Title
→ Enter Description
→ Type Question
→ Add Option for each answer choice
→ Select Correct Answer
→ Add New Question
→ Repeat
→ Publish Exam

Once Publish Exam is clicked, the exam is immediately visible in the public Exams section.

GITHUB DEPLOYMENT
=================
Replace your old website files with this ZIP's contents:
- index.html
- logo.png
- hero.jpg
- README files

Then commit/push to GitHub Pages.
