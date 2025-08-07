AWS S3 Bucket with Server-Side Encryption Using KMS

This project demonstrates how to securely configure an Amazon S3 bucket to use AWS Key Management Service (KMS). The goal is to apply fine-grained control and encryption auditing to all objects uploaded to the bucket.

Objectives

- Create a secure AWS S3 bucket for object storage.
- Generate a symmetric KMS key for encryption.
- Enable server-side encryption for the S3 bucket using the KMS key.
- Upload objects and verify that encryption is applied for data-at-rest protection purposes.

Prerequisites

- AWS account with root and IAM access
- AWS CLI or access to AWS Console
-  Permissions to use **KMS**, **S3**, **IAM** policies


## Project Setup & Steps

### 1. **Create a Symmetric KMS Key**

1. Go to AWS Console → **KMS**
2. Click **"Create key"**
3. Choose: `Symmetric`, for encryption and decryption
4. Key usage: `Encrypt and decrypt`
5. Add an alias (e.g. `myS3EncryptionKey`)
6. Set key administrators (e.g. your IAM user)
7. Set key usage permissions (e.g. allow your IAM user or app role)
8. Create key ✅

*This key will now be available for encryption use in S3 or other services.*


### 2. **Create an S3 Bucket**

1. Go to AWS Console → **S3**
2. Click **"Create bucket"**
3. Set bucket name (e.g. `my-secure-bucket-123`)
4. Choose a region (same as KMS key)
5. Leave all defaults or configure as needed
6. Create bucket ✅


### 3. **Enable Bucket Encryption with KMS Key**

1. Open your bucket → **Properties**
2. Scroll to **Default encryption**
3. Select:
   - **Enable**
   - Choose `AWS Key Management Service key (SSE-KMS)`
   - From dropdown, choose your key alias (e.g. `alias/myS3EncryptionKey`)
4. Save changes ✅

-- Now all objects uploaded to this bucket will be encrypted using your KMS key.



### 4. **Upload and Test Encryption**

- Go to the **Objects** tab
- Click **Upload** and add any file (e.g., image or HTML)
- After upload, click the object → under **Properties**, check **Encryption**

