# Attendance Management System with SMS Notifications

## Project Description
This project automates the process of student attendance tracking and sends SMS notifications to parents if their child is marked absent. The system uses a CSV file upload to record attendance data in a MySQL database and utilizes Twilio API to send real-time SMS alerts.

---

## Features
- **CSV File Upload**: Upload a CSV file to record attendance.
- **MySQL Integration**: Store student attendance details in a MySQL database.
- **SMS Notifications**: Notify parents via SMS when their child is marked absent.
- **Error Handling**: Logs errors for failed database operations or SMS delivery.

---

## Technologies Used
- **Backend**: Node.js, Express.js
- **Database**: MySQL
- **File Upload**: Multer
- **SMS API**: Twilio
- **CSV Parsing**: csv-parser

---

## Prerequisites
1. **Node.js**: Ensure Node.js is installed on your system.
2. **MySQL**: A MySQL database with the required schema.
3. **Twilio Account**: Obtain your Twilio `accountSid`, `authToken`, and phone number.
4. **Dependencies**: Install project dependencies using `npm install`.

---

## Database Setup
1. Create a database named `attendance_db`.
2. Use the following SQL script to create the required table:
    ```sql
    CREATE DATABASE attendance_db;

    USE attendance_db;

    CREATE TABLE attendance (
        id INT AUTO_INCREMENT PRIMARY KEY,
        name VARCHAR(100) NOT NULL,
        class VARCHAR(50) NOT NULL,
        branch VARCHAR(50) NOT NULL,
        time DATETIME NOT NULL,
        status ENUM('Present', 'Absent') NOT NULL,
        parent_contact VARCHAR(15) NOT NULL
    );
    ```

---

## Installation and Setup
1. Clone the repository:
    ```bash
    git clone <[repository_url](https://github.com/zishanrn2003/Attendance-Management-System-with-SMS-Notification)>
    cd <Attendance-Management-System-with-SMS-Notification>
    ```

2. Install dependencies:
    ```bash
    npm install
    ```

3. Create a `.env` file in the root directory with the following content:
    ```env
    TWILIO_ACCOUNT_SID=your_account_sid
    TWILIO_AUTH_TOKEN=your_auth_token
    TWILIO_PHONE_NUMBER=your_twilio_phone_number
    ```

4. Start the server:
    ```bash
    npm start
    ```

5. The server will be running at `http://localhost:3000`.

---

## API Endpoints

### 1. **Upload Attendance CSV**
   **Endpoint**: `/upload`  
   **Method**: `POST`  
   **Description**: Upload a CSV file to process attendance records.  

   **Sample CSV Format**:
   ```csv
   name,class,branch,time,status,parent_contact
   John Doe,10A,Science,2025-01-01 09:00:00,Absent,+1234567890
   Jane Doe,10B,Commerce,2025-01-01 09:00:00,Present,+1234567891
