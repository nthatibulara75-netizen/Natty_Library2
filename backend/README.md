NATTY LIBRARY — SQL DATABASE AND BACKEND SETUP
================================================

WHAT CONNECTS THE PROJECT?
- database.sql creates the natty_library database and its three tables.
- db.js uses mysql2/promise to create a connection pool to MySQL/MariaDB.
- .env stores the database host, port, username, password and database name.
- server.js provides the API used by the React frontend.
- frontend/src/api.js uses fetch() to send requests to the API.

PART 1 — START XAMPP
1. Open XAMPP Control Panel.
2. Click Start beside MySQL.
3. Wait until its status shows that it is running.
4. If MySQL does not start, another database service may already be using port 3306.

PART 2 — CREATE THE DATABASE
Option A: MySQL Workbench
1. Open MySQL Workbench.
2. Connect to your local database server (usually host 127.0.0.1, port 3306, user root).
3. Open this folder's database.sql file.
4. Copy all its SQL commands into a new SQL tab in Workbench.
5. Click the lightning-bolt Execute button.
6. Refresh the Schemas list. You should see natty_library, with users, books and transactions.

Note: XAMPP commonly supplies MariaDB. MySQL Workbench versions differ in how well they support MariaDB. If Workbench cannot connect, open http://localhost/phpmyadmin while XAMPP is running, choose the SQL tab, paste database.sql, and click Go.

PART 3 — SET THE BACKEND DATABASE DETAILS
1. Open the Natty_Library_Submission/backend folder in File Explorer.
2. Make a copy of .env.example.
3. Rename the copy to .env (not .env.txt).
4. Open .env in Notepad or VS Code.
5. For a standard fresh XAMPP installation, these settings are commonly used:
   DB_HOST=127.0.0.1
   DB_PORT=3306
   DB_USER=root
   DB_PASSWORD=
   DB_NAME=natty_library
6. If you set a MySQL/MariaDB root password, put that password after DB_PASSWORD=.
7. Replace JWT_SECRET with a long private value. Do not share or upload .env.

PART 4 — CREATE THE FIRST ADMIN ACCOUNT
1. Open Command Prompt in the backend folder.
2. Run: npm install
3. Run this command to create a secure password hash:
   node --input-type=module -e "import bcrypt from 'bcryptjs'; console.log(await bcrypt.hash('Natty12345',10))"
4. Copy the hash printed by the command.
5. Open MySQL Workbench (or phpMyAdmin), select the natty_library database and run the SQL below. Replace PASTE_HASH_HERE with the hash you copied:

USE natty_library;
INSERT INTO users (name, membership_id, role, password_hash)
VALUES ('Library Administrator', 'NATTY001', 'admin', 'PASTE_HASH_HERE');

Login membership ID: NATTY001
Login password: Natty12345

Change this demonstration password after you have signed in and created your own admin account.

PART 5 — START THE BACKEND
In a Command Prompt opened in the backend folder, run:
npm run dev

Keep this window open. The backend should say it is running on port 5000.
Open this address in your browser:
http://localhost:5000/health

Expected success message:
Natty Library is connected to MySQL.

PART 6 — START THE REACT WEBSITE
1. Open a SECOND Command Prompt window.
2. Change directory to the frontend folder.
3. Run:
   npm install
4. Run:
   npm run dev
5. Open the local address shown by Vite, normally:
   http://localhost:5173

Keep BOTH Command Prompt windows open while using the website:
- backend window runs Express and connects to SQL.
- frontend window runs the React development website.

USEFUL COMMAND PROMPT COMMANDS
To move to a folder, use:
cd /d "C:\path\to\Natty_Library_Submission\backend"
Then run npm install and npm run dev.

For the frontend, open another Command Prompt and use:
cd /d "C:\path\to\Natty_Library_Submission\frontend"
Then run npm install and npm run dev.

IMPORTANT
- Start XAMPP MySQL before starting the backend.
- Start the backend before using the frontend.
- Do not close the two Command Prompt windows while testing.
- The local address works on your computer; it is not yet a public internet website.
- Do not upload .env or node_modules to GitHub.
- This project has been prepared for local development. Test it on your computer with your own XAMPP database settings before submitting.
