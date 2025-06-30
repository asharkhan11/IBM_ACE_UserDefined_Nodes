# IBM ACE User Defined Nodes

This repository contains multiple user-defined nodes for IBM App Connect Enterprise (ACE), each organized by functionality in separate folders (e.g., `cryptography`).

---

## 📁 Structure

Each folder (e.g., `cryptography`) represents a specific functionality and includes the required `.jar` files to configure and use the corresponding user-defined node in IBM ACE.

Example structure:

```
IBM_ACE_UserDefined_Nodes/
├── cryptography/
│   ├── CryptoNode.jar
│   └── Crypto_timestamp.jar
├── other_functionality/
│   ├── OtherNode.jar
│   └── Other_timestamp.jar
```

---

## ⚙️ Setup Instructions (for `cryptography` node)

### 1. **Copy the Node Implementation JAR**
- Copy `CryptoNode.jar` to any folder of your choice.
- In the `node.conf.yaml` file of the **integration node**, update the `lilPath` field to include the path where `CryptoNode.jar` resides.

  Example `node.conf.yaml` snippet:

  ```yaml
  lilPath: "C:\Users\YourName\IBM_ACE\nodes\custom_nodes"
  ```

### 2. **Copy the Timestamped JAR**
- Copy `Crypto_timestamp.jar` to the **dropins** folder of your IBM ACE installation.

  **Windows Example Path:**

  ```
  C:\Program Files\IBM\ACE-12.0.0.0\tools\dropins
  ```

### 3. **Reload Toolkit and Restart Node**
- Close **IBM ACE Toolkit** if it's running.
- Open **App Connect Console** and type:

  ```bash
  ace toolkit reload
  ```

- Restart your **Integration Node**.

---

## 🧪 Usage

Once the above steps are complete:

- Open the ACE Toolkit.
- In the **Node Palette**, scroll to the bottom — you should now see the **CryptoNode** available.

### 🔐 Supported Operations

This node supports several cryptographic operations:

- Generate public key
- Generate private key
- Generate symmetric key
- Encrypt symmetric key
- Decrypt symmetric key
- Encrypt data
- Decrypt data

---

## 🔧 Dynamic Property Override

You can override node properties at runtime using the **LocalEnvironment**:

```bash
OutputLocalEnvironment.Destination.Crypto.[propertyName]
propertyName :
	action
	publicKey
	privateKey
	SymmetricKey
```

---

## 📥 Input Format

The input message to the node should be in **JSON** format, like this (if you are Encrypting or Decrypting data):

```json
{
  "data": "data to encrypt or decrypt"
}
```

---

## 💬 Notes

- Make sure paths are properly set based on Windows or Linux.
- Restarting the integration node is **mandatory** after configuration changes.
- You can replicate the above setup for other folders/nodes by following the same structure.

---

## 📄 License

None
