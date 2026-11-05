# 公开发布操作指南

## 1. 发布前必须确认
- APK 构建成功，并在目标 Android 设备完成安装、启动、文件权限、相册/视频切换和更新测试。
- 确认与旧版本的签名一致，versionCode 单调递增；不能将临时 GitHub Actions debug 签名包作为长期公开更新链。
- 检查权限说明、隐私政策、应用名称与版本、变更履历和已知问题。
- 计算 APK SHA-256 校验值；不要上传密钥、令牌、私有源码或用户文件。

## 2. 在 GitHub 网页发布
1. 打开 https://github.com/xxxxfhhf/PhoneFileOrganizer-Releases/releases
2. 点击 **Draft a new release**。
3. 选择 **Choose a tag**，新建版本标签，例如 `v3.8.0-beta`，目标分支选 `main`。
4. 填写发布标题和版本说明；测试版勾选 **Set as a pre-release**。
5. 在附件区域上传经过验证的 APK 与 SHA-256 校验文件。
6. 检查文件后点击 **Publish release**。
7. 在 Android 设备通过公开下载链接验证安装包和版本更新提示。

## 3. App 更新通道
- 稳定版：读取本公开仓库的 `releases/latest` 或公开 GitHub Releases API。
- 测试版：读取本公开仓库的 Releases 列表，并按 `prerelease` 和版本号选择候选；不能只调用 latest。
- 在 App 中显示版本、更新说明、APK 大小、签名和下载链接；用户确认后调用 Android 安装流程。
- 不要在 APK 内置任何私有源码仓库的访问令牌。
- **当前开发版仍需要将更新源切换到这个公开仓库，且需要编译验证；本指南不代表自动更新已启用。**

## 4. 回退
保留上一个验证通过的 APK、签名记录和变更履历。Android 不一定支持直接降级；优先修复版本并发布更高 versionCode，而不是要求用户卸载导致数据丢失。
