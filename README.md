
# 📧 Gmail to Google Drive Auto-Backup

> Automatically save Gmail attachments to Google Drive with n8n workflow automation

## 📋 What It Does

This n8n workflow automatically monitors your Gmail inbox for specific labels, extracts email attachments, and uploads them to a designated Google Drive folder. Perfect for archiving invoices, receipts, documents, and any important files sent via email.

**Workflow Steps:**
1. 📧 Fetch emails from Gmail with specific label
2. 📎 Extract attachments from emails
3. ☁️ Upload files to Google Drive folder
4. 🔗 Get shareable Drive links for each file

## 🚀 Quick Start

### 1. Import Workflow to n8n

**Download & Import:**
1. Download `gmail-drive-sync-workflow.json`
2. Open your n8n instance
3. Click **"Import from File"** (Ctrl/Cmd + O)
4. Select the downloaded JSON file
5. Click **"Import"**

### 2. Setup Gmail Credentials

1. In n8n, go to **Credentials** → **Create New**
2. Select **"Gmail OAuth2 API"**
3. Click **"Connect my account"**
4. Authenticate with your Google account
5. Grant Gmail read permissions
6. Save as: `Gmail`

### 3. Setup Google Drive Credentials

1. Go to **Credentials** → **Create New**
2. Select **"Google Drive OAuth2 API"**
3. Click **"Connect my account"**
4. Authenticate with the same Google account
5. Grant Drive write permissions
6. Save as: `Google Drive OAuth2 API`

### 4. Configure Gmail Label

**Create a Gmail Label (if not exists):**
1. Open Gmail
2. Go to **Settings** → **Labels**
3. Click **"Create new label"**
4. Name it (e.g., "Archive to Drive")

**Find Your Label ID:**
1. In the workflow, click **"Gmail1"** node
2. Click **"Get Label IDs"** or use Gmail API
3. Copy your label ID
4. Replace `Label_1819449526183990002` with your label ID

### 5. Configure Google Drive Folder

**Create Destination Folder:**
1. Open Google Drive
2. Create a new folder (e.g., "Email Attachments")
3. Open the folder
4. Copy the folder ID from URL: `https://drive.google.com/drive/folders/`**`FOLDER_ID_HERE`**

**Update Workflow:**
1. Click **"Upload File1"** node
2. Replace `1I-tBNWFhH2FwcyiKeBOcGseWktF-nXBr` with your folder ID

### 6. Test & Activate

1. Send a test email to yourself with an attachment
2. Apply your Gmail label to the email
3. Click **"Execute Workflow"** in n8n
4. Check if file appears in your Google Drive folder
5. If successful, activate the workflow

## 🔧 Workflow Configuration

### Node Details

#### **Gmail1** (Trigger Node)
- **Operation:** Get All Messages
- **Label Filter:** Monitors specific Gmail label
- **Format:** Resolved (includes attachments)

#### **Upload File1** (Action Node)
- **Operation:** Upload file to Drive
- **File Name:** Uses original attachment name
- **Parent Folder:** Your specified Drive folder
- **Binary Data:** Enabled for file transfer

#### **Get attachment Link** (Processing Node)
- **Operation:** Extract Drive file link
- **Output:** Shareable web view URL

### Supported File Types

✅ PDF, DOC, DOCX, XLS, XLSX
✅ Images (JPG, PNG, GIF, SVG)
✅ Videos (MP4, AVI, MOV)
✅ Archives (ZIP, RAR, TAR)
✅ Any email attachment format

## 🔄 Automation Options

### Option 1: Manual Trigger
- Run workflow manually when needed
- Good for on-demand archiving

### Option 2: Schedule Trigger
1. Add **"Schedule Trigger"** node at the start
2. Connect to **"Gmail1"** node
3. Set frequency:
   - Every 15 minutes
   - Hourly
   - Daily at specific time

```
Schedule → Gmail → Upload to Drive → Get Link
```

### Option 3: Webhook Trigger
1. Add **"Webhook"** node at the start
2. Configure webhook URL
3. Use Gmail filters or Zapier to trigger

## 💡 Use Cases

- 📄 **Invoice Archiving** - Auto-save invoices to accounting folder
- 🧾 **Receipt Management** - Organize expense receipts
- 📎 **Document Backup** - Archive important attachments
- 📊 **Report Collection** - Gather weekly/monthly reports
- 🎓 **Assignment Submission** - Store student submissions
- 📸 **Photo Backup** - Save photos sent via email

## 📊 Requirements

- n8n instance (self-hosted or cloud)
- Google account with Gmail and Drive access
- OAuth2 credentials configured
- Sufficient Google Drive storage space

## ⚠️ Troubleshooting

| Problem | Solution |
|---------|----------|
| "Label not found" | Verify label ID in Gmail settings |
| "Folder not found" | Check Drive folder ID and permissions |
| "OAuth error" | Re-authenticate both Gmail and Drive credentials |
| "Attachment not found" | Ensure email has attachments and format is "resolved" |
| "File too large" | Gmail has 25MB attachment limit per email |
| "Permission denied" | Grant full scope access during OAuth setup |

## 🙏 Credits

Built with:
- [n8n](https://n8n.io) - Workflow automation platform
- [Gmail API](https://developers.google.com/gmail/api)
- [Google Drive API](https://developers.google.com/drive)

---
