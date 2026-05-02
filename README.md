# NetBird 内网穿透部署指南

本指南帮助你在 GitHub Actions 中自动化部署 NetBird 内网穿透服务。

---

## 前置准备

### 1. 注册 NetBird 账户
访问 [NetBird Dashboard](https://app.netbird.io/) 完成注册并登录。

### 2. 创建出口分组
1. 进入 [Groups 页面](https://app.netbird.io/groups)
2. 创建默认出口分组（例如：`default-group`）

### 3. 创建访问策略
1. 进入 [ACL 页面](https://app.netbird.io/access-control)
2. 创建默认访问策略（例如：`default-acl`）


### 4. 创建网络路由
1. 进入 [网络路由](https://app.netbird.io/network-routes)
2. 创建默认网络路由（例如：`default-route`）

### 5. 创建 SetUp Key
1. 进入 [Setup Keys 页面](https://app.netbird.io/setup-keys)
2. 点击 **New Setup Key**
3. 填写名称，选择刚才创建的分组
4. 复制生成的 Key

### 6. 配置 GitHub Secrets
进入 `{{YOUR_REPO_URL}}/settings/secrets/actions`，添加以下密钥：

| Secret 名称 | 说明 |
|-----------|------|
| `NETBIRD_SETUP_KEY` | 上面创建的 SetUp Key |
| `NETBIRD_GROUP_ID` | 出口分组 ID（可选） |

---

## 触发部署

1. 进入 [Actions 页面](https://app.netbird.io/actions/workflows)
2. 选择对应的 Workflow
3. 点击 **Run workflow** 手动触发，或等待自动触发

---

## 客户端配置

### 安装客户端
根据你的操作系统选择安装方式：

- **macOS/Linux**: `curl -fsSL https://get.netbird.io/install.sh | sh`
- **Windows**: 下载 [安装包](https://docs.netbird.io/get-started/install)

### 连接使用
1. 启动 NetBird 客户端
2. 使用注册的账户登录
3. 连接后，在界面中选择出口网络/分组
4. 确认连接状态为 `Connected`

---

## 注意事项

- 确保 Setup Key 在有效期内
- GitHub Actions 运行需要足够的构建时间
- 客户端需要信任自签名证书（如果使用自托管管理服务）