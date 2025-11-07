------

```
                                    ⊱ ────────────────── {༺ ❁ ༻} ────────────────── ⊰

                                      ..|'''.|                   '||                      
                                    .|'     '  .... ... ... ...   || ..     ....  ... ..  
                                    ||          '|.  |   ||'  ||  ||' ||  .|...||  ||' '' 
                                    '|.      .   '|.|    ||    |  ||  ||  ||       ||     
                                     ''|....'     '|     ||...'  .||. ||.  '|...' .||.    
                                               .. |      ||                               
                                                ''      ''''  

                                    ⊱ ────────────────── {༺ ★ ༻} ────────────────── ⊰
```

---

A Python-based tool to securely encrypt and decrypt files in a folder using AES encryption (Fernet). This program allows users to select a folder via a GUI, encrypt all files recursively while preserving the folder structure, and decrypt them using a password. <br><br>
Encrypted files are stored in a separate `<original_folder_name>_encrypted` folder, and decrypted files are saved in a `<original_folder_name>_decrypted` folder. <br>
<br>
The tool features a rich terminal interface with progress bars and styled output for a polished user experience.

## Features

- **AES Encryption (Fernet)**: Securely encrypts files using a password-derived key with PBKDF2 and a random salt.
- **Folder Structure Preservation**: Maintains the original folder hierarchy in encrypted and decrypted outputs.
- **Separate Output Folders**:
  - Encrypted files are saved in `<original_folder_name>_encrypted`.
  - Decrypted files are saved in `<original_folder_name>_decrypted`.
- **Keep Original Files Option**: Choose whether to keep or delete source files after processing.
- **Graphical Folder Selection**: Uses Tkinter for a user-friendly folder picker.
- **Rich Terminal UI**: Leverages the `rich` library for styled output, progress bars, and interactive prompts.
- **Error Handling**: Robustly handles file access issues, invalid passwords, and missing files with clear feedback.
- **Password Security**: Enforces a minimum 8-character password and hides input during entry.

## Prerequisites

- **Python**: Version 3.10 or higher.
- **Dependencies**:
  - `cryptography`: For Fernet encryption.
  - `rich`: For styled terminal output and prompts.
  - `tkinter`: For the folder selection dialog (usually included with Python; ensure Tk/Tcl is installed).

## Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/file-encryptor-decryptor.git
   cd file-encryptor-decryptor
   ```

2. **Create a Virtual Environment** (optional but recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install Dependencies**:
   ```bash
   pip install cryptography rich
   ```

4. **Verify Tkinter**:
   Ensure Tkinter is available by running:
   ```bash
   python -c "import tkinter"
   ```
   If it fails, install Tk/Tcl (e.g., `sudo apt-get install python3-tk` on Ubuntu).

## Usage

1. **Run the Program**:
   ```bash
   python encryptor_decryptor.py
   ```

2. **Follow the Prompts**:
   - **Select Folder**: A Tkinter dialog will prompt you to choose a folder to encrypt or decrypt.
   - **Choose Mode**: Enter `e` for encryption or `d` for decryption.
   - **Keep Source Files**: Confirm whether to keep original files (default: yes).
   - **Enter Password**: Provide a password (minimum 8 characters). For decryption, use the same password used for encryption.
   - **Proceed**: Confirm to start the operation or cancel.

3. **Encryption**:
   - Select a folder (e.g., `MyFolder`).
   - Files are encrypted and saved in `MyFolder_encrypted` with `.enc` extensions.
   - A `salt.txt` file is created in the working directory to store the salt for key derivation.

4. **Decryption**:
   - Select the encrypted folder (e.g., `MyFolder_encrypted`).
   - Files are decrypted and saved in `MyFolder_decrypted` (or the base name without `_encrypted`).
   - Ensure `salt.txt` from the encryption process is in the working directory.

5. **Output**:
   - A progress bar shows processing status.
   - A summary displays the number of files processed successfully or failed.

## Example

```bash
$ python encryptor_decryptor.py
╭─────────────────────────────────────────────────────────────────────────────────────────────────╮
│                                                                                                 │
│                             Welcome to File Encryptor/Decryptor                                 │
│                                                                                                 │
╰─────────────────────────────────────────────────────────────────────────────────────────────────╯
Enter 'e' for encrypt, 'd' for decrypt [e]: d
Select the folder "MyFolder_encrypted" in the dialog
Keep source files? (y/n) [y]: y
Enter the password: ********
[+] Ready to decrypt folder: MyFolder_encrypted
[+] Decrypting files from: MyFolder_encrypted
[+] Decrypted files will be saved to: MyFolder_decrypted
Proceed with the operation? [y]: y
[Decrypting files...] 100% |██████████████████████████████████████████| 0:00:00
╭───────────────────────────────────────────────────────────────────────────────────────────────╮
│ [+] Operation completed. 10 files processed successfully, 0 failed.                           │
╰───────────────────────────────────────────────────────────────────────────────────────────────╯
```

## File Structure

- `encryptor_decryptor.py`: The main Python script.
- `salt.txt`: Generated during encryption to store the salt for key derivation (keep this for decryption).In the latest version salt is stored inside the encrypted folder.
- `<original_folder_name>_encrypted/`: Output folder for encrypted files (`.enc` extension).
- `<original_folder_name>_decrypted/`: Output folder for decrypted files.

## Security Notes

- **Password**: Use a strong password (minimum 8 characters). The same password must be used for encryption and decryption.
- **Salt File**: The `salt.txt` file is required for decryption. Do not delete or modify it.
- **Plaintext Passwords**: The password is not stored; only a random salt is saved in `salt.txt`. Keep your password secure.
- **Error Handling**: If decryption fails (e.g., wrong password), the program copies the encrypted file to the output folder and logs the issue.

## Limitations

- The program processes all files in the selected folder recursively. Large folders may take time.
- Files that cannot be encrypted/decrypted (e.g., due to permissions) are copied to the output folder with a warning.
- Ensure the `salt.txt` file from encryption is available for decryption.

## Contributing

Contributions are welcome! Please:
1. Fork the repository.
2. Create a feature branch (`git checkout -b feature/YourFeature`).
3. Commit changes (`git commit -m 'Add YourFeature'`).
4. Push to the branch (`git push origin feature/YourFeature`).
5. Open a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Built with [Python](https://www.python.org/), [cryptography](https://cryptography.io/), and [rich](https://github.com/Textualize/rich).
- Inspired by the need for a simple, secure file encryption tool with a user-friendly interface.



---


