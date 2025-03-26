# Automate flow setup

This guide provides comprehensive instructions for installing Termux and Python, setting up storage permissions, and configuring Automate to execute a Python script


# Automate Setup

1.  **Download Automate:**
    
    -   Install Automate from the [Google Play Store](https://play.google.com/store/apps/details?id=com.llamalab.automate&hl=en).
        
2.  **Launch Automate:**
    
    -   Open Automate from your app drawer.
3.  **Import flow:**
    
    -   Navigate to "Flows" menu from the left side pannel and from the top left, click the 3 dots icon and click import.
    - Select the flow file provided to you on your device
        
## Termux setup

1.  **Download and install F droid:**
    
    -   Visit the [F-Droid Termux page](https://f-droid.org/en/packages/com.termux.tasker/) and download the latest version on your Android device and install it.
        
2.  **Launch F droid:**
    
    -   Open F droid from your app drawer.
    - Wait for the app to load applications when it says "Updating repositories"
  
 3. **Install Termux from F-droid**
      - Click search icon, type Termux in search bar and install it
 4. **Launch Termux**
    - Open Termux app
5. **Setup:**
   -  At the Termux prompt, type:
     ```
   termux-setup-storage
     ```
      This command creates a `storage` folder in your Termux home with symbolic links to public folders (e.g., `shared`, `downloads`, `dcim`).

6. **Install Python in Termux:**
   Note: when these steps are in progress on terminal, it will ask Y/N question, just enter Y and the process will continue
   - Update Package Lists:
   ``
   pkg update && pkg upgrade
``        
    - Install Python:
    ```  pkg install python```
    - Verify the Installation:
     ``python --version``
     You should see the Python version printed.
7. **Setup Python script:**
   - Download the python script on your device
   - Check if the python script is available in download folder
   ``ls /storage/emulated/0/Download/script.py``
   - Move the file to Termux working directory
   ``mv /storage/emulated/0/Download/script.py ~/script.py``
   - Make the script executable
   ``chmod +x ~/script.py``
8. **Termux permission setup:**
    - type ``cd .termux``
    - Once in the folder, type ``nano termux.properties``
    - A editor terminal will pop up, and add `allow-external-apps=true` at a empty line
            - To navigate to a empty line on the editor, press and hold volume up button + s
            - Once added, press and hold volume down button + o, enter, x. One by one sequentially using volume down button to save the file 
            - type ``cd`` to navigate to home directory

## Run the flow
1.  **Permission Setup in Automate:**
    -   Open Automate app
    -   From the left side pannel, navigate to "Settings", under "Access control", click "Privileges".
    - Select check box for below permissions
        - Run commands in Termux environment
        - privileged or full (superuser) access to device features and storage
        - access to manage all files
        - execute shell commands
        - show notifications
        - ignore app hibernation
        - ignore battery optimizations

3. **Call Automate flow:**
   - Start the flow
    - After starting the flow, if no error shown on logs, the flow executed successfully
4. **Verify flow Completion:**
    - To verify successful flow completion, open Termux, on terminal, type:
    ``cat helloworld.txt``
     - It should output `hello world`. If it does, then the flow is successful
   
