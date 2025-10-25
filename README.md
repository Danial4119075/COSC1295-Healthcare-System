
# Healthcare Management System - User Guide

**Student:** Danial Awais Ansari (S4119075)  
**Course:** COSC1295 Advanced Programming  
**Institution:** RMIT University  
**Semester:** 2, 2025

---

## Table of Contents

1. [Prerequisites & Dependencies](#1-prerequisites--dependencies)
2. [Installation & Setup](#2-installation--setup)
3. [Sample Data for Testing](#3-sample-data-for-testing)
4. [Assignment Rubric Implementation](#4-assignment-rubric-implementation)
5. [System Features & Workflow Guide](#5-system-features--workflow-guide)
6. [Troubleshooting](#6-troubleshooting)

---

## 1. Prerequisites & Dependencies

### System Requirements

**Operating System:**
- Windows 10/11
- macOS 10.14 or higher
- Linux (Ubuntu 20.04 or higher)

**Hardware:**
- Minimum 4GB RAM
- 500MB free disk space
- 1280x720 display resolution or higher

### Required Software

**Java Development Kit (JDK):**
- **Version:** JDK 11 or higher
- **Download:** https://www.oracle.com/java/technologies/downloads/
- **Verification:**
  ```
  java -version
  # Should output: java version "11.0.x" or higher
  ```

**Gradle:**
- **Version:** 7.x or higher (wrapper included in project)
- **Note:** No separate installation required; use included `gradlew` / `gradlew.bat`

### Project Dependencies

All dependencies are automatically managed by Gradle. The project uses:

| Dependency | Version | Purpose |
|------------|---------|---------|
| JavaFX Controls | 17.0.2 | GUI components (buttons, text fields, layouts) |
| JavaFX FXML | 17.0.2 | Declarative UI layout files |
| SQLite JDBC | 3.42.0.0 | Database connectivity for archiving |
| JUnit Jupiter | 5.9.0 | Unit testing framework |
| SLF4J API | 2.0.7 | Logging framework API |
| SLF4J Simple | 2.0.7 | Logging implementation |

**Dependency Configuration Location:** `build.gradle` file

---

## 2. Installation & Setup

### Step 1: Extract Project Files

Extract the submitted ZIP file to a location on your computer:
```
E:\Healthcare\HealthCareSystem\
```

### Step 2: Open Terminal/Command Prompt

Navigate to the project root directory:
```
cd E:\Healthcare\HealthCareSystem
```

### Step 3: Build the Project

**Windows:**
```
gradlew.bat clean build
```

**Mac/Linux:**
```
./gradlew clean build
```

**Expected Output:**
```
BUILD SUCCESSFUL in 30s
12 actionable tasks: 12 executed
```

**What Happens During Build:**
- Downloads all dependencies (JavaFX, SQLite, JUnit)
- Compiles all Java source files
- Runs unit tests (3 test classes)
- Creates executable JAR file in `build/libs/`

### Step 4: Run the Application

**Windows:**
```
gradlew.bat run
```

**Mac/Linux:**
```
./gradlew run
```

**Alternative - Using IntelliJ IDEA:**
1. Open project in IntelliJ IDEA
2. Wait for Gradle sync to complete
3. Right-click `src/main/java/healthcare/gui/MainApplication.java`
4. Select **"Run 'MainApplication.main()'"**

**If JavaFX Module Error Occurs:**
Add VM arguments in Run Configuration:
```
--add-modules javafx.controls,javafx.fxml
```

### Step 5: First-Time Login

The application will open with a login screen.

**Default Manager Account:**
- Username: `admin`
- Password: `admin123`

---

## 3. Sample Data for Testing

Use these example values when testing system functionality. Each dialog box is shown once with complete sample data.

### 3.1 Login Screen

| Field | Sample Value |
|-------|--------------|
| Username | `admin` |
| Password | `admin123` |

---

### 3.2 Add New Patient

**Navigation:** Manager → Patients menu → Add New Patient

| Field | Sample Value |
|-------|--------------|
| Patient ID | `PAT101` |
| First Name | `John` |
| Last Name | `Smith` |
| Date of Birth | `15/03/1965` |
| Gender | `M` |
| Email | `john.smith@email.com` |
| Phone | `0412345678` |
| Address | `123 Main Street, Melbourne VIC 3000` |
| Medical Condition | `Post-operative care following hip replacement surgery` |
| Admission Date | `20/10/2025` |
| Ward | `General Care` (select from dropdown) |
| Room | `GC-R1` (select from dropdown) |
| Bed | `GC-R1-B1` (select from dropdown - must be vacant) |

---

### 3.3 Add New Staff Member

**Navigation:** Manager → Staff menu → Add New Staff

| Field | Sample Value |
|-------|--------------|
| Staff ID | `DOC005` |
| First Name | `Sarah` |
| Last Name | `Johnson` |
| Email | `sarah.johnson@hospital.com` |
| Phone | `0498765432` |
| Staff Type | `Doctor` (dropdown: Doctor, Nurse, Manager) |
| Username | `sjohnson` |
| Password | `doc456` |
| Specialization (Doctor only) | `Orthopedics` |

---

### 3.4 Add Prescription

**Navigation:** Doctor → Patients menu → Add Prescription

| Field | Sample Value |
|-------|--------------|
| Select Patient | `John Smith (PAT101)` (from dropdown) |

**Medication 1:**
| Field | Sample Value |
|-------|--------------|
| Medication Name | `Paracetamol` |
| Dosage | `500mg` |
| Frequency | `Twice daily` |
| Duration | `7 days` |

**Medication 2:**
| Field | Sample Value |
|-------|--------------|
| Medication Name | `Ibuprofen` |
| Dosage | `200mg` |
| Frequency | `Three times daily` |
| Duration | `5 days` |

---

### 3.5 Administer Medication

**Navigation:** Nurse → Patients menu → Administer Medication

| Field | Sample Value |
|-------|--------------|
| Select Patient | `John Smith (PAT101)` |
| Select Prescription | `Prescription #1 (20/10/2025)` |
| Select Medication | `Paracetamol 500mg - Twice daily` |
| Notes | `Medication administered at 9:00 AM. Patient tolerated well, no adverse reactions observed.` |

---

### 3.6 Move Patient

**Navigation:** Manager/Nurse → Patients menu → Move Patient

| Field | Sample Value |
|-------|--------------|
| Select Patient | `John Smith (PAT101)` |
| Target Ward | `Intensive Care` |
| Target Room | `IC-R1` |
| Target Bed | `IC-R1-B2` (must be vacant and same gender) |
| Reason | `Patient requires closer monitoring due to elevated blood pressure readings` |

---

### 3.7 Discharge Patient

**Navigation:** Manager → Patients menu → Discharge Patient

| Field | Sample Value |
|-------|--------------|
| Select Patient | `John Smith (PAT101)` |
| Discharge Reason | `Treatment Complete - Recovered` (from dropdown) |
| Discharge Notes | `Patient fully recovered from surgery. Wound healing progressing well. Discharged with pain management medication. Follow-up appointment scheduled for 03/11/2025.` |

---

### 3.8 Assign Staff Shift

**Navigation:** Manager → Shifts menu → Manage Shifts

**For Nurse:**
| Field | Sample Value |
|-------|--------------|
| Select Staff | `Jane Smith (NUR001)` |
| Day of Week | `Monday` |
| Shift Type | `8AM-4PM` (Morning shift) |

**For Doctor:**
| Field | Sample Value |
|-------|--------------|
| Select Staff | `Dr. Sarah Johnson (DOC005)` |
| Day of Week | `Monday` |
| Shift Time | `9AM-10AM` (1-hour block) |

---

## 4. Assignment Rubric Implementation

This section demonstrates how each assignment requirement has been implemented in the system.

### 4.1 Object-Oriented Programming (OOP) Principles

**Requirement:** Demonstrate encapsulation, inheritance, and polymorphism.

**Implementation:**

**Encapsulation:**
- All model classes use `private` fields with public getter/setter methods
- Example: `Patient.java` has private fields `patientId`, `name`, `dateOfBirth` accessible only through `getPatientId()`, `getName()`, `getDateOfBirth()`
- Data validation occurs in setters (email format, phone number validation)

**Inheritance:**
- Three-level hierarchy: `Person` (abstract base) → `Staff`/`Patient` → `Doctor`/`Nurse`/`Manager`
- `Person` defines common attributes (id, name, email, phone)
- Staff subclasses inherit all Person properties plus staff-specific features (username, shifts, permissions)

**Polymorphism:**
- `canPerformAction(String action)` method overridden in each staff type
- Runtime behavior varies by actual object type
- Example: `staff.canPerformAction("add_prescription")` returns `true` for Doctor, `false` for Nurse

**Files:** `Person.java`, `Staff.java`, `Doctor.java`, `Nurse.java`, `Manager.java`, `Patient.java`

---

### 4.2 Collections and Generics

**Requirement:** Use Java Collections framework with proper generic types.

**Implementation:**

- `Map<String, Patient>` - stores all active patients indexed by ID for O(1) lookup
- `Map<String, Staff>` - stores all staff members indexed by ID
- `List<Ward>` - maintains ordered list of hospital wards
- `List<Room>` - stores rooms within each ward
- `List<Bed>` - stores beds within each room
- `List<Prescription>` - patient prescription history
- `Map<String, List<String>>` - weekly shift schedule (day → list of shifts)

**Benefit:** Type safety prevents runtime errors; efficient data access patterns.

**Files:** `CareHome.java`, `Patient.java`, `Staff.java`, `Ward.java`

---

### 4.3 Exception Handling

**Requirement:** Custom exception classes with meaningful error messages.

**Implementation:**

**Custom Exceptions Created:**

1. **BedOccupiedException**
   - Thrown when: Attempting to assign patient to occupied bed
   - Information included: Bed ID, current patient ID, attempted patient ID
   - File: `BedOccupiedException.java`

2. **StaffNotAuthorizedException**
   - Thrown when: Staff member attempts unauthorized action
   - Information included: Staff ID, staff type, attempted action
   - File: `StaffNotAuthorizedException.java`

3. **StaffNotRosteredException**
   - Thrown when: Staff tries to perform action while off-shift
   - Information included: Staff ID, attempted action, current timestamp
   - File: `StaffNotRosteredException.java`

**Usage Example:**
```
if (!staff.canPerformAction("add_prescription")) {
    throw new StaffNotAuthorizedException(staff, "add_prescription", staff.getStaffType());
}
```

**Files:** `exceptions/` package, `CareHome.java`

---

### 4.4 Business Rules Validation

**Requirement:** Enforce specified business rules with appropriate checks.

**Implementation:**

**1. Staff Authorization:**
- Doctors: Can view patients, add prescriptions
- Nurses: Can view patients, administer medication, move patients
- Managers: Can perform all actions including discharge and staff management
- Enforcement: `canPerformAction()` method checks before every operation

**2. Shift Compliance:**
- Nurses: Maximum 7 shifts per week (one 8-hour shift per day)
- Doctors: Minimum 7 hours per week across 7 days
- Validation: `ShiftScheduler.checkCompliance()` generates compliance reports
- View: Reports menu → Check Shift Compliance

**3. Roster Checking:**
- Staff must be on current shift to perform actions
- Method: `isRosteredNow()` checks current day/time against schedule
- Throws: `StaffNotRosteredException` if staff not on duty

**4. Gender Segregation:**
- Patients of different genders cannot share a room
- Check occurs during: Add patient, Move patient operations
- Validation: Iterates existing room occupants, compares gender
- Empty rooms accept any gender initially

**Files:** `CareHome.java`, `Staff.java`, `ShiftScheduler.java`

---

### 4.5 Data Persistence (Serialization)

**Requirement:** Save and restore system state to/from file.

**Implementation:**

- All model classes implement `Serializable` interface
- Save location: `data/carehome_data.ser`
- Save triggers: Manual (File menu → Save Data) and automatic on exit
- Restore: Automatic on application startup
- Backup: Creates `carehome_data.ser.backup` before overwriting
- Transient fields: `DatabaseManager` and `AuditLogger` marked `transient` (re-initialized on load)

**Save Method:**
```
public void saveData() throws IOException {
    ObjectOutputStream out = new ObjectOutputStream(new FileOutputStream("data/carehome_data.ser"));
    out.writeObject(this);
    out.close();
}
```

**Files:** `CareHome.java`, all model classes

---

### 4.6 Database Integration (JDBC/SQLite)

**Requirement:** Archive discharged patient data to external database accessible by auditors.

**Implementation:**

**Database Type:** SQLite (embedded database)
**Location:** `data/healthcare.db`
**Connection:** JDBC driver (org.xerial:sqlite-jdbc:3.42.0.0)

**Database Schema (5 Tables):**

1. **discharged_patients** - Main patient information
   - Columns: patient_id (PK), name, dob, gender, email, phone, address, medical_condition, admission_date, discharge_date, discharge_reason, discharge_notes, discharged_by_staff_id

2. **archived_prescriptions** - Prescription records
   - Columns: prescription_id (PK), patient_id (FK), prescribed_by_doctor_id, date_prescribed
   - Foreign Key: References discharged_patients(patient_id)

3. **archived_medications** - Individual medications
   - Columns: medication_id (PK), prescription_id (FK), medication_name, dosage, frequency, duration
   - Foreign Key: References archived_prescriptions(prescription_id)

4. **archived_medication_records** - Administration logs
   - Columns: record_id (PK), patient_id (FK), medication_name, dosage, administered_by_nurse_id, administered_at, notes
   - Foreign Key: References discharged_patients(patient_id)

5. **audit_log** - System action trail
   - Columns: log_id (PK), staff_id, action, details, timestamp

**Archiving Process:**
1. Manager clicks: Patients → Discharge Patient
2. System calls: `DatabaseManager.archiveDischargedPatient(patient, reason, notes, staffId)`
3. Database operations:
   - INSERT patient record into `discharged_patients`
   - INSERT all prescriptions into `archived_prescriptions`
   - INSERT all medications into `archived_medications`
   - INSERT all medication records into `archived_medication_records`
   - INSERT discharge action into `audit_log`
4. Patient removed from active system
5. Bed marked as vacant

**Security:** PreparedStatement prevents SQL injection
**Transaction:** All-or-nothing archiving (if any insert fails, entire transaction rolls back)

**Viewing Database:**
- Use "DB Browser for SQLite" (free tool)
- Open `data/healthcare.db`
- Browse all archived records

**Files:** `DatabaseManager.java`, `CareHome.java`

---

### 4.7 Graphical User Interface (JavaFX)

**Requirement:** JavaFX-based GUI with visual bed display and color coding.

**Implementation:**

**Architecture:**
- Pattern: Model-View-Controller (MVC)
- View: FXML files (`login.fxml`, `dashboard.fxml`)
- Controller: Java classes (`LoginController.java`, `DashboardController.java`)

**Main Components:**

1. **Login Screen:**
   - Username and password fields
   - Role-based authentication
   - Error messages for invalid credentials

2. **Dashboard:**
   - Menu bar: File, Patients, Staff, Shifts, Reports
   - Visual ward layout: GridPane with colored rectangles
   - Real-time clock: Updates every second
   - Status bar: Shows logged-in user and current shift status

3. **Visual Bed Display:**
   - Each bed shown as colored rectangle
   - **Blue** = Male patient occupied
   - **Pink** = Female patient occupied
   - **Gray** = Vacant bed
   - Click bed to view patient details

4. **Dialog Boxes:**
   - Add Patient, Add Staff, Add Prescription, Administer Medication
   - Move Patient, Discharge Patient, Assign Shifts
   - All with input validation and error messages

**Files:** `gui/` package, `resources/fxml/` folder

---

### 4.8 Unit Testing (JUnit)

**Requirement:** Comprehensive unit tests for business logic.

**Implementation:**

**Three Test Classes:**

1. **CareHomeTest.java** (10 tests)
   - Bed occupancy validation
   - Authorization checking (doctor prescriptions, nurse medication)
   - Patient movement between beds
   - Staff authentication
   - Ward and bed initialization

2. **StaffTest.java** (5 tests)
   - Permission testing for each staff type
   - Shift management (add, remove, duplicate prevention)
   - Polymorphic behavior verification
   - Inheritance hierarchy validation

3. **ValidationUtilsTest.java** (8 tests)
   - Email format validation
   - Phone number validation (10-15 digits)
   - ID format validation (3-10 alphanumeric)
   - Gender validation (M/F)
   - Dosage format validation (number + unit)
   - String cleaning and formatting

**Test Methodology:**
- Positive tests: Valid inputs succeed
- Negative tests: Invalid inputs throw expected exceptions
- Setup: `@BeforeEach` initializes fresh test data
- Assertions: `assertTrue`, `assertFalse`, `assertThrows`, `assertEquals`

**Running Tests:**
```
./gradlew test
```

**Test Report Location:**
```
build/reports/tests/test/index.html
```

**Files:** `test/java/healthcare/` directory

---

### 4.9 Design Patterns

**Requirement:** Demonstrate understanding of design patterns.

**Implementation:**

**1. Singleton Pattern:**
- **Classes:** `CareHome`, `DatabaseManager`, `AuditLogger`
- **Purpose:** Ensure only one instance exists; global access point
- **Benefit:** Prevents conflicting state; single database connection
- **Implementation:**
  ```
  private static CareHome instance;
  private CareHome() { /* private constructor */ }
  public static synchronized CareHome getInstance() {
      if (instance == null) instance = new CareHome();
      return instance;
  }
  ```

**2. Model-View-Controller (MVC):**
- **Model:** Domain classes (`Patient`, `Staff`, `Prescription`, etc.)
- **View:** FXML files (declarative UI layouts)
- **Controller:** GUI controllers (handle user interactions, update model)
- **Benefit:** Separation of concerns; testable business logic

**3. Factory Method (implicit):**
- **Staff creation:** Manager methods create Doctor/Nurse/Manager instances
- **Benefit:** Centralized object creation; consistent initialization

**Files:** Throughout codebase

---

## 5. System Features & Workflow Guide

This section explains each feature with step-by-step navigation.

### 5.1 Patient Management

#### Feature: Add New Patient

**Purpose:** Admit new patient to the facility and assign to available bed.

**Who Can Use:** Manager only

**Navigation:**
1. Login as Manager (`admin` / `admin123`)
2. Click **Patients menu** → **Add New Patient**
3. Dialog opens with form fields
4. Fill all required fields (see Section 3.2 for sample data)
5. Select available bed from dropdowns (Ward → Room → Bed)
6. Click **Add Patient**

**System Actions:**
- Validates all input (email format, phone format, gender, etc.)
- Checks bed availability
- Checks gender segregation in selected room
- Creates patient record
- Marks bed as occupied
- Saves to serialized data
- Logs action to audit trail

**Result:** Patient added; bed shown in blue/pink on ward layout.

---

#### Feature: View Patient Details

**Purpose:** View comprehensive patient information including prescriptions and medication records.

**Who Can Use:** All staff

**Navigation:**
1. Login as any staff member
2. Click on any **colored bed rectangle** in ward layout
3. Patient details dialog appears

**Information Shown:**
- Personal details (name, DOB, gender, contact)
- Medical condition
- Admission date
- Current bed location
- All prescriptions
- Medication administration history

**Result:** Read-only view of patient data.

---

#### Feature: Move Patient

**Purpose:** Transfer patient to different bed (different ward or room).

**Who Can Use:** Manager, Nurse

**Navigation:**
1. Login as Manager or Nurse
2. Click **Patients menu** → **Move Patient**
3. Select patient from dropdown
4. Select target location (Ward → Room → Bed)
5. Enter reason for move
6. Click **Move Patient**

**System Actions:**
- Validates target bed is vacant
- Checks gender segregation in target room
- Vacates original bed
- Occupies target bed
- Updates patient record
- Logs move to audit trail

**Result:** Patient moved; ward layout updates instantly.

---

#### Feature: Discharge Patient

**Purpose:** Archive patient data and free bed when patient leaves facility.

**Who Can Use:** Manager only

**Navigation:**
1. Login as Manager
2. Click **Patients menu** → **Discharge Patient**
3. Select patient from dropdown
4. Choose discharge reason from dropdown
5. Enter discharge notes (optional but recommended)
6. Click **Discharge Patient**

**System Actions:**
- Archives all patient data to SQLite database:
  - Patient personal information
  - All prescriptions
  - All medications
  - All medication administration records
- Removes patient from active system
- Frees up bed
- Logs discharge to audit trail
- **Database location:** `data/healthcare.db`

**Result:** Patient discharged; bed becomes vacant (gray); data preserved in database.

---

### 5.2 Prescription Management

#### Feature: Add Prescription

**Purpose:** Doctor prescribes medications for patient.

**Who Can Use:** Doctor only

**Navigation:**
1. Login as Doctor (`doctor1` / `doc123`)
2. Click **Patients menu** → **Add Prescription**
3. Select patient from dropdown
4. Add medications:
   - Enter medication name
   - Enter dosage (e.g., 500mg)
   - Select frequency (e.g., Twice daily)
   - Enter duration (e.g., 7 days)
5. Click **Add More Medications** to prescribe multiple (optional)
6. Click **Add Prescription**

**System Actions:**
- Validates doctor authorization
- Creates prescription record with timestamp
- Attaches to patient record
- Logs action to audit trail

**Result:** Prescription available for nurses to administer.

---

#### Feature: Administer Medication

**Purpose:** Record when nurse gives medication to patient.

**Who Can Use:** Nurse only

**Navigation:**
1. Login as Nurse (`nurse1` / `nur123`)
2. Click **Patients menu** → **Administer Medication**
3. Select patient from dropdown
4. Select prescription from dropdown
5. Select specific medication from prescription
6. Enter notes (optional)
7. Click **Record Administration**

**System Actions:**
- Validates nurse authorization
- Validates nurse is currently on shift
- Creates medication record with timestamp
- Attaches to patient history
- Logs action to audit trail

**Result:** Medication administration recorded; viewable in patient details and archived on discharge.

---

### 5.3 Staff Management

#### Feature: Add New Staff

**Purpose:** Register new staff member (Doctor, Nurse, or Manager).

**Who Can Use:** Manager only

**Navigation:**
1. Login as Manager
2. Click **Staff menu** → **Add New Staff**
3. Fill form fields (see Section 3.3 for sample data)
4. Select staff type from dropdown
5. Enter credentials (username, password)
6. For doctors, enter specialization
7. For nurses, enter certification
8. Click **Add Staff**

**System Actions:**
- Validates input (email, phone, unique username)
- Creates staff record
- Logs action to audit trail

**Result:** New staff member can login with provided credentials.

---

#### Feature: Assign Shifts

**Purpose:** Schedule staff work shifts for the week.

**Who Can Use:** Manager only

**Navigation:**
1. Login as Manager
2. Click **Shifts menu** → **Manage Shifts**
3. Select staff member from dropdown
4. Select day of week
5. Select shift:
   - **Nurses:** 8AM-4PM (morning) or 2PM-10PM (afternoon)
   - **Doctors:** 1-hour block (e.g., 9AM-10AM)
6. Click **Assign Shift**

**System Actions:**
- Validates shift rules:
  - Nurses: Max 1 shift per day, max 7 per week
  - Doctors: Min 7 total hours per week
- Updates weekly schedule
- Logs action to audit trail

**Result:** Staff shift visible in compliance report.

---

### 5.4 Reporting

#### Feature: Shift Compliance Report

**Purpose:** Verify staff meet shift requirements.

**Who Can Use:** Manager

**Navigation:**
1. Login as Manager
2. Click **Reports menu** → **Check Shift Compliance**

**Report Shows:**
- Staff name and type
- Shifts assigned per day
- Total shifts/hours per week
- Compliance status (Compliant / Non-compliant)

**Result:** Identifies staff not meeting requirements.

---

#### Feature: Audit Log

**Purpose:** View complete history of all system actions.

**Who Can Use:** Manager

**Navigation:**
1. Login as Manager
2. Click **Reports menu** → **View Audit Log**

**Log Shows:**
- Timestamp
- Staff ID
- Action performed
- Details

**Examples:**
- `2025-10-25 09:15:30 | admin | ADD_PATIENT | Added patient PAT101 to bed GC-R1-B1`
- `2025-10-25 10:22:15 | doctor1 | ADD_PRESCRIPTION | Prescribed medications for PAT101`
- `2025-10-25 14:33:45 | nurse1 | ADMINISTER_MEDICATION | Administered Paracetamol to PAT101`

**Result:** Complete accountability trail for regulatory compliance.

---

### 5.5 Data Persistence

#### Feature: Save System State

**Purpose:** Manually save all data to file.

**Who Can Use:** Any staff

**Navigation:**
1. Click **File menu** → **Save Data**

**System Actions:**
- Serializes entire CareHome object
- Saves to `data/carehome_data.ser`
- Creates backup of previous save

**Result:** Data preserved; can restore if system crashes.

---

#### Feature: Automatic Data Restoration

**Purpose:** Reload saved state on application start.

**Who Can Use:** Automatic (no user action)

**Process:**
1. Application starts
2. Checks for `data/carehome_data.ser`
3. If exists, deserializes and loads data
4. If not exists, initializes with sample data

**Result:** Previous session state restored automatically.

---

## 6. Troubleshooting

### Issue: "JavaFX components could not be loaded"

**Symptoms:**
```
Error: JavaFX runtime components are missing
```

**Cause:** JavaFX modules not explicitly loaded.

**Solution:**
Add VM arguments:
```
--add-modules javafx.controls,javafx.fxml
```

**Steps for IntelliJ:**
1. Run → Edit Configurations
2. Select MainApplication
3. VM options field: `--add-modules javafx.controls,javafx.fxml`
4. Apply → OK

---

### Issue: Build fails with "JAVA_HOME not set"

**Symptoms:**
```
ERROR: JAVA_HOME is not set and no 'java' command could be found
```

**Cause:** Java not in system PATH.

**Solution:**

**Windows:**
```
set JAVA_HOME=C:\Program Files\Java\jdk-11
set PATH=%JAVA_HOME%\bin;%PATH%
```

**Mac/Linux:**
```
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk-11.jdk/Contents/Home
export PATH=$JAVA_HOME/bin:$PATH
```

---

### Issue: Database locked error

**Symptoms:**
```
SQLiteException: database is locked
```

**Cause:** Previous application instance did not close properly.

**Solution:**
1. Close application properly (File → Logout, then close window)
2. Delete `data/healthcare.db.lock` if exists
3. Restart application

---

### Issue: "Permission denied" when writing files

**Symptoms:**
```
IOException: Permission denied: data/carehome_data.ser
```

**Cause:** Insufficient write permissions in project directory.

**Solution:**
1. Run application with administrator privileges
2. Or move project to user directory (e.g., `C:\Users\YourName\`)

---

### Issue: Tests fail with NullPointerException

**Symptoms:**
```
java.lang.NullPointerException at CareHomeTest.setUp()
```

**Cause:** Test data not initialized properly.

**Solution:**
```
./gradlew clean test
```

This rebuilds and re-runs tests fresh.

---

### Issue: Application window too small or cut off

**Symptoms:** Buttons or text not visible.

**Cause:** Display resolution too low.

**Solution:**
Minimum resolution: 1280x720. Increase display resolution in system settings.

---

## Contact & Support

**Student:** Danial Awais Ansari  
**Student ID:** S4119075  
**Institution:** RMIT University  
**Course:** COSC1295 Advanced Programming  
**Semester:** 2, 2025

For questions about this assignment submission, please contact through Canvas.

---

**Document Version:** 1.0  
**Last Updated:** October 25, 2025  
**Total Pages:** This comprehensive guide

---

## Appendix: File Structure

```
HealthCareSystem/
├── src/
│   ├── main/
│   │   ├── java/healthcare/
│   │   │   ├── database/
│   │   │   │   └── DatabaseManager.java
│   │   │   ├── exceptions/
│   │   │   │   ├── BedOccupiedException.java
│   │   │   │   ├── StaffNotAuthorizedException.java
│   │   │   │   └── StaffNotRosteredException.java
│   │   │   ├── gui/
│   │   │   │   ├── DashboardController.java
│   │   │   │   ├── LoginController.java
│   │   │   │   ├── PatientDialog.java
│   │   │   │   ├── PrescriptionDialog.java
│   │   │   │   ├── StaffDialog.java
│   │   │   │   └── MainApplication.java
│   │   │   ├── model/
│   │   │   │   ├── Person.java
│   │   │   │   ├── Patient.java
│   │   │   │   ├── Staff.java
│   │   │   │   ├── Doctor.java
│   │   │   │   ├── Nurse.java
│   │   │   │   ├── Manager.java
│   │   │   │   ├── Ward.java
│   │   │   │   ├── Room.java
│   │   │   │   ├── Bed.java
│   │   │   │   ├── Prescription.java
│   │   │   │   ├── Medication.java
│   │   │   │   ├── MedicationRecord.java
│   │   │   │   └── CareHome.java
│   │   │   └── utils/
│   │   │       ├── ValidationUtils.java
│   │   │       ├── AuditLogger.java
│   │   │       └── ShiftScheduler.java
│   │   └── resources/
│   │       └── fxml/
│   │           ├── login.fxml
│   │           └── dashboard.fxml
│   └── test/
│       └── java/healthcare/
│           ├── CareHomeTest.java
│           ├── StaffTest.java
│           └── ValidationUtilsTest.java
├── data/                         (auto-generated on first run)
│   ├── carehome_data.ser
│   ├── healthcare.db
│   └── audit_log.txt
├── build.gradle
├── gradlew
├── gradlew.bat
├── module-info.java
└── README.md
```



## **AI Assistance Acknowledgement**

During the development of this healthcare management system, I utilized AI tools (ChatGPT/Perplexity) as a supplementary learning resource to overcome specific technical challenges and accelerate problem-solving. This section transparently documents how AI assisted my learning process while emphasizing that all core design decisions, implementation logic, and architectural choices remain my own work.

### **Role of AI in Development Process**

AI tools served as an **on-demand technical reference** and **debugging assistant**, similar to consulting documentation or Stack Overflow, but with more contextual understanding of my specific code. The AI did not write the system architecture or business logic; rather, it helped clarify concepts, identify syntax errors, and suggest best practices when I encountered obstacles.

**Important Note:** All final code decisions, class designs, and feature implementations were made by me after understanding AI suggestions and evaluating their appropriateness for the assignment requirements.

***

### **Specific Scenarios Where AI Assisted**

#### **1. JavaFX Threading Issue - Real-Time Clock Update**

**Challenge:** My initial attempt to display a live clock using `Thread.sleep()` in a loop completely froze the user interface.

**My Approach:** Researched JavaFX threading model but struggled to understand Application Thread vs background thread execution.

**AI Interaction:**
- **Prompt:** "Why does Thread.sleep() in JavaFX freeze my UI, and how can I update a Label every second without blocking?"
- **AI Response:** Explained that JavaFX UI updates must occur on the Application Thread, suggested using `Timeline` with `KeyFrame` for scheduled updates.
- **My Action:** Implemented Timeline solution, tested thoroughly, and verified non-blocking behavior.

**Outcome:** Successfully implemented real-time clock that updates every second without UI freeze. **This solution was AI-suggested but implemented and tested by me.**

---

#### **2. SQLite Foreign Key Enforcement**

**Challenge:** Despite defining foreign key relationships in my database schema, SQLite allowed orphaned prescription records (prescriptions referencing deleted patients).

**My Approach:** Reviewed JDBC documentation but couldn't identify why constraints weren't enforced.

**AI Interaction:**
- **Prompt:** "My SQLite foreign keys aren't working - I can insert invalid references. What's wrong?"
- **AI Response:** Explained that SQLite disables foreign key enforcement by default for backward compatibility; must execute `PRAGMA foreign_keys = ON` before creating tables.
- **My Action:** Added pragma statement to `DatabaseManager.initializeDatabase()`, retested with invalid data to confirm enforcement.

**Outcome:** Database now properly rejects invalid foreign key insertions. **This was a configuration issue I learned about through AI guidance.**

***

#### **3. Java Module System Configuration**

**Challenge:** Application compiled successfully with Gradle but crashed immediately when run with `java.lang.NoClassDefFoundError: javafx/application/Application`.

**My Approach:** Suspected dependency issue but unclear why JavaFX wasn't loading despite being in build.gradle dependencies.

**AI Interaction:**
- **Prompt:** "JavaFX application compiles but crashes with NoClassDefFoundError on runtime. Dependencies are in build.gradle."
- **AI Response:** Explained Java 9+ module system requires explicit module loading; JavaFX isn't in JDK anymore. Suggested `--add-modules javafx.controls,javafx.fxml` VM argument.
- **My Action:** Added VM arguments to build.gradle `applicationDefaultJvmArgs` and IntelliJ run configuration.

**Outcome:** Application launches successfully. **This was a deployment configuration insight from AI, not code generation.**

***

#### **4. Polymorphic Permission Checking Logic**

**Challenge:** Needed clean way to enforce role-based permissions (doctors prescribe, nurses administer) without massive if-else chains.

**My Approach:** Initially wrote authorization checks in every method with switch statements on staff type.

**AI Interaction:**
- **Prompt:** "I have repetitive authorization checks for doctor/nurse/manager permissions. Is there a better design pattern?"
- **AI Response:** Suggested polymorphic `canPerformAction(String action)` method overridden in each Staff subclass, enabling runtime behavior variation.
- **My Action:** Refactored authorization logic to polymorphic method, created test cases for each staff type.

**Outcome:** Cleaner, more maintainable code following Open/Closed Principle. **AI suggested the pattern; I implemented and tested it.**

***

#### **5. JUnit Test Setup with @BeforeEach**

**Challenge:** Tests were failing intermittently because previous test data wasn't cleared before next test.

**My Approach:** Manually initialized test objects in each test method, causing duplication and inconsistencies.

**AI Interaction:**
- **Prompt:** "How do I ensure each JUnit test starts with fresh data? Tests interfere with each other."
- **AI Response:** Explained `@BeforeEach` annotation runs setup method before each test, ensuring isolation.
- **My Action:** Created `setUp()` method annotated with `@BeforeEach`, moved initialization code there.

**Outcome:** Tests now properly isolated and repeatable. **This was a JUnit best practice I learned through AI explanation.**

***

### **What AI Did NOT Do**

To maintain academic integrity, it's important to clarify that AI assistance was **limited to specific technical guidance**:

**AI did not:**
- Design the class hierarchy (Person → Staff → Doctor/Nurse/Manager)
- Decide to use Singleton pattern for CareHome
- Choose SQLite over MySQL or other databases
- Implement business rules (gender segregation, shift compliance)
- Write the database schema or archiving logic
- Design the JavaFX UI layout or controller structure
- Generate test cases or testing strategy

**All architectural decisions, design patterns, and implementation choices were mine**, informed by assignment requirements and software engineering principles learned in the course.

***

### **Learning Outcomes from AI Usage**

**1. Deeper Understanding Through Explanation:**
Rather than just providing code snippets, AI explanations helped me understand *why* solutions work. For example, learning about JavaFX's threading model fundamentally changed how I approach UI development.

**2. Faster Problem Resolution:**
Instead of spending hours debugging obscure issues (like the SQLite pragma), AI quickly identified the root cause, allowing me to focus on implementing features rather than fighting configuration problems.

**3. Best Practice Awareness:**
AI suggestions introduced me to industry patterns (polymorphism for permissions, `@BeforeEach` for test isolation) that I could then research further and apply appropriately.

**4. Documentation Clarification:**
When official documentation was unclear or overwhelming (e.g., JavaFX module system), AI provided concise explanations with relevant examples that helped me understand complex topics.

***

### **Ethical Use of AI Tools**

I used AI assistance in accordance with academic integrity principles:

- **Transparency:** This acknowledgment fully discloses AI usage
- **Learning Focus:** Used AI to understand concepts, not copy-paste solutions
- **Independent Verification:** Tested and validated all AI suggestions
- **Original Work:** All design decisions and final implementations are my own
- **Critical Thinking:** Evaluated AI responses; did not blindly accept suggestions

AI served as a **learning accelerator** and **technical reference**, similar to how professionals use documentation, forums, or consult colleagues. The system architecture, business logic, and overall implementation demonstrate my understanding of advanced programming concepts taught in COSC1295.


**END OF USER GUIDE**
```
