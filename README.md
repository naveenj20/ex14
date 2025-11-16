# UiPath Experiment: Encrypt, Send, Receive & Decrypt Text Using Vigenère Cipher (Cryptii)

## Objective
To build a UiPath workflow where:
1. The user enters a text message.
2. The message is encrypted using the **Vigenère Cipher** on **Cryptii** (via Open Browser/Application).
3. The encrypted text is sent through **Gmail**.
4. The receiver extracts the email body, decrypts it using Cryptii, and displays the final decrypted message using a **Message Box**.

---

## Workflow Summary
This experiment demonstrates end-to-end automation of:
- Text encryption  
- Email communication  
- Text decryption  
Using UiPath activities and a web-based cipher tool (Cryptii).

---

## Steps

### 1. Get User Input
- Use **Input Dialog** activity.
- Ask: “Enter the message to encrypt”.
- Store the input in a variable, e.g., `inputText`.

---

### 2. Encrypt the Text Using Vigenère Cipher (Cryptii)
- Use **Open Browser** → navigate to:  
  `https://cryptii.com/pipes/vigenere-cipher`
- Use **Type Into** to enter:
  - The plaintext (`userMessage`)
  - The key (you may set a fixed key like `"UIPath"` or ask user for one)
- Use **Get Text** to extract the **encrypted output**.
- Store it in `encryptedText`.

---

### 3. Send Encrypted Text via Gmail
- Use **Send SMTP Mail Message** or **Send Email (Gmail)** activity.
- Set:
  - To: receiver email
  - Subject: `"Encrypted Message"`
  - Body: `encryptedText`
- Make sure Gmail app-password or secure authentication is configured.

---

### 4. Read the Email on the Receiver Side
- Use **Get IMAP Mail Messages / Gmail Read Email** activity.
- Read the latest email.
- Extract the **email body** into `receivedEncryptedMessage`.

---

### 5. Decrypt the Text on Cryptii
- Open **Cryptii Vigenère Cipher** again using **Open Browser**.
- Clear previous content using **Click** + **Type Into**.
- Enter:
  - Ciphertext → `receivedEncryptedMessage`
  - Same key used earlier.
- Extract the decrypted output using **Get Text** into `decryptedMessage`.

---

### 6. Display Final Message
- Use **Message Box** activity:

Expected Output
- User enters a message → Workflow encrypts it on Cryptii.
  <img width="1920" height="1200" alt="Screenshot (379)" src="https://github.com/user-attachments/assets/bac5e88a-0b6a-4dac-9b75-6dfc9b50f012" />
  <img width="1920" height="1200" alt="Screenshot (380)" src="https://github.com/user-attachments/assets/78cd4b48-e614-4965-a935-17ae93ac1712" />

- Encrypted message is emailed.
- <img width="1920" height="1200" alt="Screenshot (381)" src="https://github.com/user-attachments/assets/99fb7e91-41ab-4bca-b2d4-1c9e8dea997f" />

- Receiver automation reads the email, decrypts it on Cryptii.
- <img width="1920" height="1200" alt="Screenshot (382)" src="https://github.com/user-attachments/assets/6754da6c-3f17-4a72-99bb-29a00fd91a42" />
- <img width="1920" height="1200" alt="Screenshot (383)" src="https://github.com/user-attachments/assets/2fe4bb0e-f0f4-4941-8f4b-cd9db5cce3cd" />

- The final original message appears in a Message Box.
- <img width="1920" height="1200" alt="Screenshot (384)" src="https://github.com/user-attachments/assets/2a0c3bcd-8d73-4a59-b18f-727c28c98b60" />


---

## Result
A complete UiPath automation demonstrating:
- User input handling  
- Web automation  
- Vigenère cipher encryption/decryption  
- Email sending/receiving  
- Display of final decoded output  

This showcases integration of external web tools with UiPath for secure message transmission and automated cryptographic workflows.
