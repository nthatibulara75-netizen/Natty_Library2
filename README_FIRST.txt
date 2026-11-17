NATTY LIBRARY — SQL-LINKED PROJECT
===================================

Project folders:
- frontend: React website
- backend: Express API and SQL database connection
- backend/database.sql: SQL script to create natty_library and its tables

STARTUP ORDER:
1. Start MySQL in XAMPP.
2. Run backend/database.sql in MySQL Workbench or phpMyAdmin.
3. Configure backend/.env using backend/.env.example as the guide.
4. In backend Command Prompt: npm install, then npm run dev.
5. In another Command Prompt, open frontend and run: npm install, then npm run dev.
6. Browse to http://localhost:5173.

Read backend/README.md for the full step-by-step guide, including creating the first administrator account.

The local website is not public on the internet until it is separately deployed to hosting.
Do not upload .env or node_modules to GitHub.
