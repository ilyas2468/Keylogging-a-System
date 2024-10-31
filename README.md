# Keylogging-a-System
This project demonstrates a controlled remote keylogger developed using Python, ctypes, and Windows API functions. The keylogger captures keyboard inputs in real time, logging keystrokes along with the active application window to provide context for each input.

## Key Features
- **Low-Level Keyboard Hook:** Uses SetWindowsHookExA with WH_KEYBOARD_LL to capture keystrokes at a low level.
- **Active Application Tracking:** Identifies and logs the foreground application window where each keystroke occurs.
- **Structured Data Capture:** Implements the KBDLLHOOKSTRUCT structure to collect virtual key codes and event details.
- **Safe Testing Environment:** Run within Oracle VM VirtualBox to ensure a secure, isolated environment for keylogging activities.

## Screenshots

### 1. Initial Code Setup
This part of the code:
- Imports Libraries: ctypes and windll.user32 are imported to interface with Windows API functions, which will enable low-level system interactions.
- Defines Constants: WH_KEYBOARD_LL, WM_KEYDOWN, WM_RETURN, and others are defined. These constants specify the types of keyboard events (e.g., WM_KEYDOWN for key presses) and hook IDs.
- Defines Windows API Functions: Several Windows API functions are defined, such as GetWindowTextLengthA and GetKeyState. These will allow the script to interact with the system, such as checking the length of a window’s title text or getting the state of a key.
![Initial Code Setup](https://i.imgur.com/n9CUZhh.png)

### 2. Active Window Tracking and Key Hook Setup
This part of the code:
-	Keyboard Hook Struct: Defines the KBDLLHOOKSTRUCT structure, which is used to store keyboard event data such as virtual key codes and scan codes. This struct is essential for capturing details of each keystroke.
-	Get Foreground Process Function: Implements get_foreground_process(), which identifies the name of the active window (the application currently in use). This function allows the keylogger to track which application each keystroke was made in, adding context to the logged data.
-	Hook Function: Defines the main hook_function, which processes keystrokes. When a key is pressed (WM_KEYDOWN), it logs the key event along with the active window information. This is the core of the keylogging functionality.
![Active Window Tracking and Key Hook Setup](https://i.imgur.com/rhEGboc.png)
### 3. Key Hook Setup Continued
This part of the code:
-	Initializes the last and callback variables, which manage the keyboard hook’s callback function.
-	Sets up the hook with SetWindowsHookExA, specifying WH_KEYBOARD_LL for low-level keyboard events.
-	Enters a message loop to keep the program running and actively listening for keyboard events. This loop allows the keylogger to capture events until it's explicitly stopped.
![Key Hook Setup Continued](https://i.imgur.com/pvaNodD.png)

### 4. Keylogger Script Execution
- Script Start: The keylogger script is initiated within a controlled virtual environment on Oracle VM VirtualBox.
- Real-Time Monitoring: The Command Prompt window displays real-time keystroke capture, verifying the keylogger’s functionality by capturing typed inputs across open applications like Notepad and Google Chrome.
- Application Detection: The keylogger records not only the keystrokes but also identifies the active application window where typing occurs, providing context for each recorded input.
- Typing Verification: Various phrases are typed in both Notepad and Google Chrome to confirm that the keylogger accurately captures and displays each keystroke, regardless of the application in focus.
![Keylogger Script Execution](https://i.imgur.com/EAj1Iyi.png)

- Note: This keylogger was developed for educational and demonstration purposes, conducted within a secure environment.

