# bloodbridge-api - Connect Donors with Those in Need

[![Download from GitHub](https://img.shields.io/badge/Download%20BloodBridge-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/petitionary-process913/bloodbridge-api)

## 🩸 What This Software Does

BloodBridge is a server application that helps match blood donors with people who need blood. Hospitals and donation centers can use it to find nearby donors quickly. The system uses smart matching to find the best donor for each request.

Think of it as a coordination tool. It broadcasts a request to eligible donors in the area. Each donor gets a QR code for fast check-in when they arrive to donate.

## 💻 Who Should Use This

This software is built for:
- Blood banks
- Hospital administrators
- Donation center operators
- Community health organizations

You do not need to write code to use this. You need basic computer skills to install it.

## ⚙️ System Requirements

Your computer needs to meet these minimum requirements:

- **Operating System:** Windows 10 or Windows 11 (64-bit)
- **Processor:** Intel Core i3 or AMD equivalent (2.0 GHz or faster)
- **Memory:** 4 GB RAM minimum (8 GB recommended)
- **Storage:** 500 MB free space
- **Java Runtime:** Java 17 or newer (included in the installer)
- **Network:** Broadband internet connection

## 🚀 Getting Started

Follow these steps to download and run BloodBridge on your Windows computer.

### Step 1: Download the Software

Visit the download page:

[**https://github.com/petitionary-process913/bloodbridge-api**](https://github.com/petitionary-process913/bloodbridge-api)

On that page, click the green "Code" button and select "Download ZIP". Or scroll down to the "Releases" section on the right side of the page and click the latest release link.

### Step 2: Extract the Files

The download is a ZIP file. You need to extract it:

1. Open your Downloads folder
2. Right-click the `bloodbridge-api-main.zip` file
3. Select "Extract All"
4. Choose a destination folder (like `C:\BloodBridge`)
5. Click "Extract"

### Step 3: Install the Prerequisites

BloodBridge needs three pieces of software to run. Download and install them in this order:

**Java 17 (Required):**
1. Go to https://adoptium.net
2. Download the "Windows x64 Installer" for Java 17 (LTS)
3. Run the installer and follow the prompts

**MySQL Database (Required):**
1. Go to https://dev.mysql.com/downloads/installer
2. Download the "Windows (x86, 64-bit), MySQL Installer MSI"
3. Run the installer
4. Choose "Server only" setup type
5. Set a root password (write this down)
6. Complete the installation

**Redis (Required for caching):**
1. Go to https://github.com/microsoftarchive/redis/releases
2. Download the latest `.msi` file
3. Run the installer with default settings

### Step 4: Set Up the Database

1. Open the Start Menu and search for "MySQL Command Line Client"
2. Enter your root password when prompted
3. Type this command and press Enter:
   ```
   CREATE DATABASE bloodbridge;
   ```
4. Type this command and press Enter:
   ```
   exit
   ```

### Step 5: Configure the Application

1. Open the extracted `bloodbridge-api-main` folder
2. Find the file named `application.properties` in the `src/main/resources` folder
3. Open it with Notepad
4. Find the line that starts with `spring.datasource.password`
5. Replace the placeholder password with the MySQL root password you set in Step 3
6. Save and close the file

### Step 6: Start the Application

1. Open the Command Prompt as Administrator (right-click Start Menu, select "Command Prompt (Admin)" or "Windows Terminal (Admin)")
2. Type this command to go to the BloodBridge folder:
   ```
   cd C:\BloodBridge\bloodbridge-api-main
   ```
3. Type this command and press Enter:
   ```
   mvnw spring-boot:run
   ```
4. Wait for the application to start. You will see "Started BloodBridgeApplication in X seconds" when it is ready

### Step 7: Verify It Is Running

1. Open your web browser
2. Go to this address: `http://localhost:8080/api/health`
3. You should see a message like `{"status":"UP"}`

## 🔑 Features

**Donor Matching Engine**
The system uses machine learning to score potential donors. It considers blood type, location, donation history, and availability. This ensures the most suitable donors get notified first.

**QR Code Verification**
Each donor receives a unique QR code. When they arrive at the donation center, staff scan the code to verify their identity and appointment.

**Geo-Radius Broadcasting**
When a blood request comes in, the system finds eligible donors within a set radius (default 10 miles). It sends them a notification through the connected mobile app.

**JWT Authentication**
All communications between the server and client apps use JSON Web Tokens. This keeps data secure and prevents unauthorized access.

**Donor History Tracking**
The system keeps records of each donor's donations, deferrals, and eligibility status. This helps maintain compliance with donation interval rules.

## 🛠️ API Endpoints (for developers)

If you have technical staff, they can connect other applications to BloodBridge through these endpoints:

- `POST /api/auth/login` - User login
- `POST /api/donors/register` - Register new donor
- `GET /api/donors/search` - Find donors by criteria
- `POST /api/requests/create` - Create a blood request
- `GET /api/requests/nearby` - Get requests near a location
- `POST /api/donations/verify` - Verify donor via QR code

## 📦 What Is Included in the Download

The ZIP file contains:

- **Executable JAR** (`bloodbridge-api.jar`) - The main application
- **Configuration files** - Settings for database, security, and features
- **Database migration scripts** - Automatically sets up the required tables
- **Docker configuration** - Alternative setup method for advanced users
- **Documentation** - Technical guides in the `docs` folder

## 🔧 Troubleshooting

**Application fails to start**
- Make sure MySQL is running. Check in the Start Menu for "MySQL 8.0 Command Line Client"
- Make sure Redis is running. Check in the Services panel for "Redis"
- Verify the database password in `application.properties`

**Port 8080 is already in use**
- Close other applications that might use this port
- Or change the port in `application.properties` by adding `server.port=9090`

**Database connection refused**
- Ensure MySQL Service is running. Go to Services panel and start "MySQL80"
- Check your firewall settings. MySQL uses port 3306

## 📄 License

This software is provided for use under the MIT License. You can use, modify, and distribute it freely.

Keywords: blood-donation, docker, flyway, java, jwt-authentication, mysql, qr-code, redis, rest-api, spring-boot, spring-security