# n8n-nodes-aliyunoss

[English](./README_EN.md) | 简体中文

这是一个 n8n 社区节点，提供与阿里云对象存储服务(OSS)的集成。

[![npm version](https://badge.fury.io/js/n8n-nodes-aliyunoss.svg)](https://www.npmjs.com/package/n8n-nodes-aliyunoss)
[![npm downloads](https://img.shields.io/npm/dt/n8n-nodes-aliyunoss.svg)](https://www.npmjs.com/package/n8n-nodes-aliyunoss)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

[n8n](https://n8n.io/) 是一个可扩展的工作流自动化工具。通过 [公平代码](https://faircode.io) 分发模式，n8n 将始终提供可见的源代码，可供自托管，并允许您添加自己的自定义功能、逻辑和应用程序。

## 📦 安装

按照 n8n 社区节点文档中的[安装指南](https://docs.n8n.io/integrations/community-nodes/installation/)进行操作。

### 方式1：通过 n8n 社区节点（推荐）

1. 进入 n8n 界面的 **设置 > 社区节点**
2. 点击 **安装**
3. 在 npm 包名称字段输入 `n8n-nodes-aliyunoss`
4. 点击 **安装**

### 方式2：手动安装

进入 n8n 安装目录（通常在 `~/.n8n/`）并运行：

```bash
npm install n8n-nodes-aliyunoss
```

重启 n8n 以加载新安装的节点。

## ⚡ 支持的操作

此节点支持以下 OSS 操作：

### 📤 上传文件
- 支持二进制数据上传
- 可自定义文件路径和名称
- 支持按日期自动分组
- 支持三种文件命名模式：
  - 保持原始文件名
  - UUID + 原始文件名
  - 自定义文件名
- 可设置文件访问权限（private/public-read/public-read-write）

### 📥 下载文件
- 从 OSS 下载文件到工作流
- 自动识别 MIME 类型
- 输出为二进制数据，可继续处理

### 🗑️ 删除文件
- 根据文件路径删除指定文件
- 返回删除操作状态

### 📋 列出文件
- 列出指定 Bucket 中的文件
- 支持目录前缀过滤
- 支持分页（自定义返回数量）
- 可设置分隔符
- 返回文件列表和目录前缀

### 🔗 获取签名 URL
- 生成临时访问 URL
- 可自定义过期时间（秒）
- 支持 GET/PUT 等 HTTP 方法
- 返回 URL 和过期时间

### 📋 复制文件
- 在 OSS 内部复制文件
- 支持同一 Bucket 内复制
- 无需下载再上传，速度快

### ℹ️ 获取文件信息
- 获取文件元数据
- 包含文件大小、类型、最后修改时间等
- 返回完整的响应头信息

## 🔐 凭证配置

使用此节点前，需要配置阿里云 OSS 凭证：

### 必需参数

- **Access Key ID** - 阿里云 AccessKeyId
- **Access Key Secret** - 阿里云 AccessKeySecret
- **Endpoint** - OSS 服务域名（例如：`oss-cn-hangzhou.aliyuncs.com`）
- **Region** - OSS 所在区域（从下拉菜单选择）

### 获取凭证

1. 登录[阿里云控制台](https://ram.console.aliyun.com/users)
2. 进入 **RAM 访问控制** → **身份管理** → **用户**
3. 创建用户或查看现有用户的 AccessKey
4. 确保用户具有 OSS 操作权限（推荐：`AliyunOSSFullAccess`）

### 支持的区域

支持阿里云所有 OSS 区域，包括：
- 中国大陆：杭州、上海、北京、深圳、成都等
- 中国香港
- 海外：新加坡、东京、硅谷、法兰克福等

## 📖 使用示例

### 示例1：上传文件到 OSS

```
Manual Trigger → Read Binary File → 阿里云OSS(上传)
```

配置 OSS 节点：
- 操作：上传文件
- Bucket 名称：your-bucket-name
- 上传路径：uploads/images
- 按日期分组：是

### 示例2：获取文件列表并下载

```
Schedule Trigger → 阿里云OSS(列表) → 阿里云OSS(下载) → 发送邮件
```

### 示例3：生成临时分享链接

```
Webhook → 阿里云OSS(获取签名URL) → 返回响应
```

配置：
- 操作：获取签名URL
- 文件路径：images/photo.jpg
- 有效期：3600 秒（1小时）

### 示例4：文件备份

```
Schedule Trigger → 阿里云OSS(列表) → 阿里云OSS(复制)
```

每天自动将重要文件复制到备份目录。

## 🔧 兼容性

- **n8n 版本**：1.0.0 及以上
- **Node.js 版本**：18.10 及以上
- **阿里云 OSS SDK**：6.18.1

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！

1. Fork 本仓库
2. 创建您的功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交您的更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启一个 Pull Request

## 📝 更新日志

### v1.0.0 (2025-10-24)

**首次发布** 🎉

- ✅ 支持文件上传（多种命名模式）
- ✅ 支持文件下载
- ✅ 支持文件删除
- ✅ 支持列出文件（带过滤）
- ✅ 支持获取签名 URL
- ✅ 支持文件复制
- ✅ 支持获取文件信息
- ✅ 完整的中英文文档
- ✅ 支持所有阿里云 OSS 区域

## 📄 许可证

[MIT](LICENSE.md)

## 🔗 相关链接

- [n8n 官网](https://n8n.io/)
- [n8n 社区节点文档](https://docs.n8n.io/integrations/community-nodes/)
- [阿里云 OSS 文档](https://help.aliyun.com/product/31815.html)
- [GitHub 仓库](https://github.com/grahamry/n8n-nodes-aliyunoss)
- [npm 包](https://www.npmjs.com/package/n8n-nodes-aliyunoss)

## 💬 支持

如果遇到问题或有建议：

- 📮 提交 [GitHub Issue](https://github.com/grahamry/n8n-nodes-aliyunoss/issues)
- 💬 在 [n8n 社区论坛](https://community.n8n.io/)讨论

## ⭐ Star History

如果这个项目对您有帮助，请给个 Star ⭐️

---

**作者**: nqbt45182  
**维护者**: [grahamry](https://github.com/grahamry)
