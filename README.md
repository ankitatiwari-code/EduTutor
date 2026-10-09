# EduHome – Home Tuition Finder Website

EduHome is a web-based platform designed to connect parents with suitable home tutors. It helps parents find tutors according to their child's educational requirements, preferred subjects, location, budget, and tuition preferences.

The platform aims to make the process of finding home tuition more convenient by allowing parents to register, provide their child's learning requirements, and explore available tutors.

## ✨ Features

### 👨‍👩‍👧 Parent Registration

* Register using name, email, mobile number, and password.
* Add child details, including name, age, class, and school.
* Select preferred subjects and tuition requirements.
* Specify location, budget, preferred days, and timing.
* Store parent profile information in Firebase Firestore.

### 👩‍🏫 Tutor Discovery

* Browse tutors through the tutor listing page.
* View tutor information and relevant profile details.
* Support the development of a more personalized tutor-search experience.

### 🔐 Authentication

* Create accounts using Firebase Authentication.
* Sign in using registered email and password.
* Associate user profiles with their Firebase Authentication UIDs.
* Support role-based profiles for parents and tutors.

### ☁️ Firebase Integration

* **Firebase Authentication:** Manages user registration and authentication.
* **Cloud Firestore:** Stores user profile and registration information.
* **Firebase Storage:** Available for future features such as tutor profile photos and videos.

### 📱 User Interface

* HTML-based pages with CSS styling.
* JavaScript-powered form validation and interactions.
* Responsive design intended for convenient use across different screen sizes.

## 🛠️ Technologies Used

| Technology              | Purpose                                          |
| ----------------------- | ------------------------------------------------ |
| HTML5                   | Website structure                                |
| CSS3                    | Styling and layout                               |
| JavaScript (ES Modules) | Form handling, validation, and application logic |
| Firebase Authentication | User registration and login                      |
| Cloud Firestore         | Database for user and profile information        |
| Firebase Storage        | Planned support for profile media                |
| Visual Studio Code      | Development environment                          |
| Git and GitHub          | Version control and project hosting              |

## 📂 Project Structure

The project uses a simple file structure with HTML pages, JavaScript modules, and shared styling files.

```text
EduHome/
│
├── index.html
├── login.html
├── signup.html
├── parent-register.html
├── tutor-register.html
├── tutors.html
├── tutor-profile.html
│
├── firebase-config.js
├── auth.js
├── parent.js
├── tutor.js
├── tutors.js
├── navbar-auth.js
├── main.js
│
├── style.css
├── README.md
└── assets/
    ├── images/
    └── icons/
```

**Note:** This is a representative structure. Keep only the files and folders that actually exist in your repository, and update the structure as the project develops.

## ⚙️ Getting Started

Follow these steps to run EduHome locally.

### 1. Clone the Repository

Open a terminal and run:

```bash
git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
```

Replace `YOUR-USERNAME` and `YOUR-REPOSITORY` with your actual GitHub username and repository name.

### 2. Open the Project

```bash
cd YOUR-REPOSITORY
```

Open the folder in Visual Studio Code.

### 3. Configure Firebase

1. Open the [Firebase Console](https://console.firebase.google.com/).
2. Create a Firebase project or select your existing EduHome project.
3. Register a web app in the project settings.
4. Copy the Firebase web app configuration.
5. Add the configuration to `firebase-config.js`.

Example structure:

```javascript
import { initializeApp } from
  "https://www.gstatic.com/firebasejs/12.17.1/firebase-app.js";

import { getAuth } from
  "https://www.gstatic.com/firebasejs/12.17.1/firebase-auth.js";

import { getFirestore } from
  "https://www.gstatic.com/firebasejs/12.17.1/firebase-firestore.js";

import { getStorage } from
  "https://www.gstatic.com/firebasejs/12.17.1/firebase-storage.js";

const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_STORAGE_BUCKET",
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
  appId: "YOUR_APP_ID"
};

const app = initializeApp(firebaseConfig);

const auth = getAuth(app);
const db = getFirestore(app);
const storage = getStorage(app);

export { app, auth, db, storage };
```

Replace the placeholder values with the configuration from your Firebase project. Use the same Firebase project and compatible SDK versions throughout the application.

### 4. Enable Firebase Authentication

1. Open **Firebase Console → Authentication**.
2. Select **Get started**, if required.
3. Open the **Sign-in method** section.
4. Enable **Email/Password** authentication.

### 5. Set Up Cloud Firestore

1. Open **Firebase Console → Firestore Database**.
2. Create a database if one does not already exist.
3. Configure appropriate Firestore security rules.
4. Ensure the application writes parent and tutor profiles to the intended collections.

For example, the application may store user profiles in a `users` collection, with each document identified by the authenticated user's UID.

**Security note:** Never publish service-account private keys or other server-side secrets. Firebase web configuration is not a substitute for Firestore security rules. Restrict access to authenticated users and their permitted data.

### 6. Run the Website

Because the project uses JavaScript ES modules, run it through a local development server rather than opening HTML files directly.

In Visual Studio Code:

1. Install the **Live Server** extension if it is not already installed.
2. Right-click `index.html`.
3. Select **Open with Live Server**.
4. Open the local URL shown in your browser.

## 🧭 Application Workflow

1. A visitor opens the EduHome website.
2. The user navigates to parent or tutor registration.
3. The user enters the required information.
4. Firebase Authentication creates the account.
5. The application stores the profile in Cloud Firestore.
6. The user can log in with the registered credentials.
7. Parents can navigate to the tutor listing page to explore tutor options.

The exact available functionality depends on which pages and features are currently implemented.

## 🗄️ Database Design

A possible Firestore structure is shown below.

```text
Firestore Database
│
└── users (collection)
    │
    ├── {parentUid} (document)
    │   ├── name
    │   ├── email
    │   ├── role: "parent"
    │   ├── mobile
    │   ├── address
    │   └── child
    │       ├── name
    │       ├── age
    │       └── class
    │
    └── {tutorUid} (document)
        ├── name
        ├── email
        ├── role: "tutor"
        ├── mobile
        ├── experience
        └── subjects
```

The fields above illustrate a possible data model. Your actual Firestore documents should match the fields implemented in your JavaScript registration modules.

## 🔒 Security Considerations

* Never store user passwords in Firestore or browser storage.
* Use Firebase Authentication to manage credentials.
* Configure Firestore security rules to prevent unauthorized access.
* Validate user inputs on the client and enforce authorization through database rules.
* Do not commit private keys, passwords, or sensitive personal data to GitHub.
* Avoid publicly exposing parent addresses, child details, or private tutor information.
* Test authentication and database permissions before deploying the application.

## 🚀 Future Enhancements

The following features can be added as the project develops:

* Advanced tutor search by location, class, subject, and budget.
* Individual tutor profile pages with qualifications and experience.
* Tutor profile photo and introductory video uploads.
* Ratings and reviews for tutors.
* Availability and tuition scheduling.
* Parent-to-tutor contact and enquiry functionality.
* Online booking and booking status tracking.
* Improved mobile responsiveness and accessibility.
* An admin dashboard for managing tutor profiles and enquiries.
* Notifications for booking requests and updates.

These are planned enhancements and should not be considered completed features until implemented.

## 🎯 Project Objective

The main objective of EduHome is to simplify the process of finding home tutors by providing a centralized platform where parents can share their child's learning requirements and explore suitable tutoring options.

The project also provides practical experience with frontend development, JavaScript modules, Firebase Authentication, Cloud Firestore, form validation, and user-profile management.

## 👩‍💻 Author

**Ankita Tiwari**

* GitHub: [github.com/ankitatiwari-code](https://github.com/ankitatiwari-code)

## 📄 License

This project is intended for learning and development purposes. A license has not been specified yet. Consider adding an MIT License if you want others to reuse and modify the project under its terms.

