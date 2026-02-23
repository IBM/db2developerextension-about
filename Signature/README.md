# IBM Db2 Developer Extension - Signature Verification Guide

Verify the authenticity and integrity of the IBM Db2 Developer Extension before installation.

## What You'll Need

Download the verification package containing:  
- `db2-for-luw-1.1.0.vsix` - Extension package  
- `db2-for-luw-1.1.0.vsix.cosign.sig` - Digital signature  
- `PRD0015359key.pem.pub.key` - Public key for verification  
- `PRD0015359key.pem.cer` - X.509 certificate  
- `PRD0015359key.pem.chain` - Certificate chain  

> **Important:** After downloading, open your terminal or PowerShell and **change directory (`cd`) to the folder path where these files are downloaded** before running any verification commands.

## Quick Verification (2 Steps)

### Step 1: Install Cosign

**macOS:**
```bash
brew install cosign
```

**Linux:**
```bash
# Download latest release
wget https://github.com/sigstore/cosign/releases/latest/download/cosign-linux-amd64
sudo mv cosign-linux-amd64 /usr/local/bin/cosign
sudo chmod +x /usr/local/bin/cosign
```

**Windows:**
```powershell
# Using Scoop
scoop install cosign

# Or download from: https://github.com/sigstore/cosign/releases
```

**Verify installation:**
```bash
cosign version
```

### Step 2: Verify the Signature

**macOS:**
```bash
# Decode the signature
base64 -D -i db2-for-luw-1.1.0.vsix.cosign.sig -o db2-for-luw-1.1.0.vsix.sig

# Verify with Cosign
cosign verify-blob \
  --key PRD0015359key.pem.pub.key \
  --signature db2-for-luw-1.1.0.vsix.sig \
  --insecure-ignore-tlog=true \
  db2-for-luw-1.1.0.vsix
```

**Linux:**
```bash
# Decode the signature
base64 -d db2-for-luw-1.1.0.vsix.cosign.sig > db2-for-luw-1.1.0.vsix.sig

# Verify with Cosign
cosign verify-blob \
  --key PRD0015359key.pem.pub.key \
  --signature db2-for-luw-1.1.0.vsix.sig \
  --insecure-ignore-tlog=true \
  db2-for-luw-1.1.0.vsix
```

**Windows (PowerShell):**
```powershell
# Decode the signature
[System.Convert]::FromBase64String((Get-Content db2-for-luw-1.1.0.vsix.cosign.sig)) | Set-Content -Encoding Byte db2-for-luw-1.1.0.vsix.sig

# Verify with Cosign
cosign verify-blob `
  --key PRD0015359key.pem.pub.key `
  --signature db2-for-luw-1.1.0.vsix.sig `
  --insecure-ignore-tlog=true `
  db2-for-luw-1.1.0.vsix
```

### Expected Output

```
Verified OK
```

✅ **Success!** The extension is verified and safe to install.

## Optional: Verify Certificate Chain

Verify the IBM certificate chain using OpenSSL:

```bash
openssl verify -CAfile PRD0015359key.pem.chain PRD0015359key.pem.cer
```

**Expected Output:**
```
PRD0015359key.pem.cer: OK
```

Once installed, you can use OpenSSL to verify the certificate chain for IBM Db2 Developer Extension.

## Certificate Information

- **Issuer**: DigiCert Trusted G4 Code Signing RSA4096 SHA384 2021 CA1
- **Subject**: International Business Machines Corporation
- **Valid Until**: December 8, 2027
- **Key Type**: RSA 4096-bit
- **Usage**: Code Signing

## Troubleshooting

### Issue: "cosign: command not found"

**Solution:** Install Cosign using the instructions in Step 1.

### Issue: "Verification failure"

**Possible Causes:**
- Signature file not decoded properly
- Corrupted download
- Wrong files

**Solution:**
1. Ensure you decoded the signature file correctly (creates `.sig` file)
2. Re-download all files from official IBM source
3. Verify you're using the correct public key file

### Issue: "base64: invalid argument" (macOS)

**Solution:** Use the correct macOS syntax:
```bash
base64 -D -i db2-for-luw-1.1.0.vsix.cosign.sig -o db2-for-luw-1.1.0.vsix.sig
```

### Issue: OpenSSL not found

If the `openssl` command is not recognized on your system, follow the steps below to install it.

**macOS:**
```bash
brew install openssl
```

**Linux (Ubuntu/Debian):**
```bash
sudo apt update
sudo apt install openssl -y
```

**Linux (RHEL/CentOS):**
```bash
sudo yum install openssl
```

**Windows:**

1. Download the OpenSSL installer from https://slproweb.com/products/Win32OpenSSL.html
2. Choose the version matching your system architecture (Win32 or Win64)
3. Run the installer and follow the setup prompts
4. Add the OpenSSL `bin` folder (e.g., `C:\Program Files\OpenSSL-Win64\bin`) to your Windows PATH environment variable
5. Restart PowerShell or Command Prompt to apply the PATH changes
6. Verify the installation by running:

```powershell
openssl version
```

**Expected Output:**
```
OpenSSL 3.x.x [date] [platform]
```

## Understanding the Process

1. **Signature File**: The `.cosign.sig` file is base64 encoded and must be decoded first
2. **Verification**: Cosign uses the public key to verify the signature matches the VSIX file
3. **Certificate**: The certificate proves the public key belongs to IBM
4. **Trust Chain**: The certificate chain validates the certificate's authenticity

## Security Best Practices

✓ Always verify signatures before installing extensions  
✓ Download files only from official IBM sources  
✓ Keep Cosign and OpenSSL updated  
✓ Verify certificate expiration date  
✓ Report verification failures to IBM Security

## Need Help?

- **GitHub Issues**: https://github.com/IBM/db2developerextension-about/issues
- **Security Concerns**: security@ibm.com
- **Documentation**: https://ibm.github.io/db2developerextension-about/

## Additional Resources

- **Cosign Documentation**: https://docs.sigstore.dev/cosign/overview/
- **Cosign Installation**: https://docs.sigstore.dev/cosign/installation/
- **OpenSSL Documentation**: https://www.openssl.org/docs/

---

**Version Information**
- Extension Version: 1.1.0
- Product ID: PRD0015359
- Certificate Valid Until: December 8, 2027
- Document Version: 6.1
- Last Updated: February 2026

**Note**: The signature file is base64 encoded and must be decoded before verification. The `--insecure-ignore-tlog=true` flag is required because this signature was created without transparency log integration.