# n8n-nodes-aliyunoss

English | [简体中文](./README.md)

This is an n8n community node that provides integration with Aliyun OSS (Object Storage Service).

[![npm version](https://badge.fury.io/js/n8n-nodes-aliyunoss.svg)](https://www.npmjs.com/package/n8n-nodes-aliyunoss)
[![npm downloads](https://img.shields.io/npm/dt/n8n-nodes-aliyunoss.svg)](https://www.npmjs.com/package/n8n-nodes-aliyunoss)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

[n8n](https://n8n.io/) is an extendable workflow automation tool. With a [fair-code](https://faircode.io) distribution model, n8n will always have visible source code, be available to self-host, and allow you to add your own custom functions, logic and apps.

## 📦 Installation

Follow the [installation guide](https://docs.n8n.io/integrations/community-nodes/installation/) in the n8n community nodes documentation.

### Method 1: Via n8n Community Nodes (Recommended)

1. Go to **Settings > Community Nodes** in n8n
2. Click **Install**
3. Enter `n8n-nodes-aliyunoss` in the npm Package Name field
4. Click **Install**

### Method 2: Manual Installation

Navigate to your n8n installation directory (usually `~/.n8n/`) and run:

```bash
npm install n8n-nodes-aliyunoss
```

Restart n8n to load the newly installed node.

## ⚡ Supported Operations

This node supports the following OSS operations:

### 📤 Upload File
- Upload binary data to OSS
- Customize file path and name
- Support automatic date-based grouping
- Three file naming patterns:
  - Keep original filename
  - UUID + original filename
  - Custom filename
- Set file access permissions (private/public-read/public-read-write)

### 📥 Download File
- Download files from OSS to workflow
- Automatic MIME type detection
- Output as binary data for further processing

### 🗑️ Delete File
- Delete specified file by path
- Return deletion operation status

### 📋 List Files
- List files in specified bucket
- Support directory prefix filtering
- Support pagination (custom return count)
- Configurable delimiter
- Return file list and directory prefixes

### 🔗 Get Signed URL
- Generate temporary access URLs
- Customizable expiration time (seconds)
- Support various HTTP methods (GET/PUT, etc.)
- Return URL and expiration time

### 📋 Copy File
- Copy files within OSS
- Support copying within the same bucket
- Fast operation without downloading/uploading

### ℹ️ Get File Info
- Retrieve file metadata
- Includes file size, type, last modified time, etc.
- Return complete response headers

## 🔐 Credentials Configuration

Before using this node, you need to configure Aliyun OSS credentials:

### Required Parameters

- **Access Key ID** - Your Aliyun AccessKeyId
- **Access Key Secret** - Your Aliyun AccessKeySecret
- **Endpoint** - OSS service endpoint (e.g., `oss-cn-hangzhou.aliyuncs.com`)
- **Region** - OSS region (select from dropdown)

### Obtaining Credentials

1. Log in to [Aliyun Console](https://ram.console.aliyun.com/users)
2. Go to **RAM Access Control** → **Identities** → **Users**
3. Create a new user or view existing user's AccessKey
4. Ensure the user has OSS operation permissions (recommended: `AliyunOSSFullAccess`)

### Supported Regions

Supports all Aliyun OSS regions, including:
- Mainland China: Hangzhou, Shanghai, Beijing, Shenzhen, Chengdu, etc.
- Hong Kong
- International: Singapore, Tokyo, Silicon Valley, Frankfurt, etc.

## 📖 Usage Examples

### Example 1: Upload File to OSS

```
Manual Trigger → Read Binary File → Aliyun OSS (Upload)
```

Configure OSS node:
- Operation: Upload File
- Bucket Name: your-bucket-name
- Upload Path: uploads/images
- Group by Date: Yes

### Example 2: List and Download Files

```
Schedule Trigger → Aliyun OSS (List) → Aliyun OSS (Download) → Send Email
```

### Example 3: Generate Temporary Share Link

```
Webhook → Aliyun OSS (Get Signed URL) → Return Response
```

Configuration:
- Operation: Get Signed URL
- File Path: images/photo.jpg
- Expires: 3600 seconds (1 hour)

### Example 4: File Backup

```
Schedule Trigger → Aliyun OSS (List) → Aliyun OSS (Copy)
```

Automatically copy important files to backup directory daily.

## 🔧 Compatibility

- **n8n Version**: 1.0.0 and above
- **Node.js Version**: 18.10 and above
- **Aliyun OSS SDK**: 6.18.1

## 🤝 Contributing

Issues and Pull Requests are welcome!

1. Fork this repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 Changelog

### v1.0.0 (2025-10-24)

**Initial Release** 🎉

- ✅ File upload support (multiple naming patterns)
- ✅ File download support
- ✅ File deletion support
- ✅ List files (with filtering)
- ✅ Get signed URL support
- ✅ File copy support
- ✅ Get file info support
- ✅ Complete Chinese and English documentation
- ✅ Support all Aliyun OSS regions

## 📄 License

[MIT](LICENSE.md)

## 🔗 Related Links

- [n8n Official Site](https://n8n.io/)
- [n8n Community Nodes Documentation](https://docs.n8n.io/integrations/community-nodes/)
- [Aliyun OSS Documentation](https://www.alibabacloud.com/help/en/oss/)
- [GitHub Repository](https://github.com/grahamry/n8n-nodes-aliyunoss)
- [npm Package](https://www.npmjs.com/package/n8n-nodes-aliyunoss)

## 💬 Support

If you encounter any issues or have suggestions:

- 📮 Submit a [GitHub Issue](https://github.com/grahamry/n8n-nodes-aliyunoss/issues)
- 💬 Discuss on [n8n Community Forum](https://community.n8n.io/)

## ⭐ Star History

If this project helps you, please give it a Star ⭐️

---

**Author**: nqbt45182  
**Maintainer**: [grahamry](https://github.com/grahamry)
