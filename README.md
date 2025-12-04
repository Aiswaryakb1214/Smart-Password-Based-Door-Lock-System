📌 Overview

This project implements a password-secured smart door access system using:

ESP8266 NodeMCU

I2C 16×2 LCD

Servo Motor (Door Lock Actuator)

Serial/Keypad Password Input

The system verifies a password, unlocks a door using a servo motor, displays messages on LCD, and includes lockout protection after multiple wrong attempts.

This project helped me understand:

Servo motor PWM control

I2C LCD interfacing

Serial communication

Password validation logic

Lockout & password reset mechanisms

🛠 Features
✔️ Fixed password stored in microcontroller

A predefined password is stored inside the ESP8266 program.

✔️ Correct password entered

LCD displays: “Access Granted”

Servo rotates to unlock position

Door opens for a few seconds and then re-locks automatically

❌ Wrong password entered

LCD shows: “Wrong Password”

User gets up to 3 attempts

🔒 LOCKED Mode (after 3 wrong attempts)

System enters a lockout mode

LCD shows: “System Locked”

User must reset the password

After setting a new password, the system becomes active again

🧠 System Workflow
1️⃣ Idle Mode

LCD displays “Enter Password”
System waits for user input (via Serial Monitor or Keypad)

2️⃣ Password Verification

Compare entered password with stored password

If matched → Unlock door

If not → Increase wrong attempt count

3️⃣ Lockout Condition

If wrong attempts reach 3 times:

System locks

Accepts only “Reset Mode”

User enters new password

4️⃣ Reset Password Mode

User types new password

New password saved in memory (RAM – can be extended to EEPROM)

Attempts reset to 0

System returns to normal operation
🖥 Working Demonstration (Explanation for GitHub)
🔸 Entering Password

User enters password through the Serial Monitor or via keypad.
The ESP8266 reads each character and constructs the password string.

🔸 Password Match

If the entered password matches the stored one:

LCD shows “Access Granted”

Servo rotates to 0° → 90° (Open)

After 3 seconds servo returns to locked position

🔸 Wrong Password

If password does not match:

LCD shows “Wrong Password”

Attempt counter increments

After 3 failed attempts → System Locked

🔸 Lock Mode

LCD continuously shows “System Locked - Reset Password”
User must provide a new password.

🔸 Resetting Password

User enters new password

System saves it

Attempts reset

LCD shows “Password Reset Successful”

System returns to normal operation.

📘 Applications

Smart home door automation

Hostel / PG access systems

School lab access

Secure cabinets/lockers

Basic IoT-based security projects
