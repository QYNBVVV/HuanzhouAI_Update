# HuanzhouAI Update

这是幻昼 AI Android 的公开更新仓库，用于托管：

- `update.json`：远程版本检测与 APK 更新信息
- `announcement.json`：远程公告
- `changelog.md`：更新日志
- GitHub Releases：APK 安装包

源码仓库可以保持私有；本仓库只放公开更新元数据与发布包。

## Raw 地址

```text
https://raw.githubusercontent.com/QYNBVVV/HuanzhouAI_Update/main/update.json
https://raw.githubusercontent.com/QYNBVVV/HuanzhouAI_Update/main/announcement.json
```

## update.json 字段

- `enabled`：是否启用更新检测
- `latestVersionCode`：最新版本号，用于和 Android `versionCode` 比较
- `latestVersionName`：最新版本名
- `minSupportedVersionCode`：最低可用版本，低于该值会触发强制更新
- `forceUpdate`：是否强制更新
- `title`：更新弹窗标题
- `description`：更新说明
- `apkUrl`：GitHub Release 中 APK 的下载地址
- `apkSize`：APK 文件大小，单位 byte
- `sha256`：APK SHA256 校验值
- `releasePageUrl`：Release 页面地址
- `publishedAt`：发布时间

## announcement.json 字段

- `enabled`：是否启用公告
- `version`：公告版本号，递增后可再次向用户展示
- `title`：公告标题
- `content`：公告内容
- `level`：公告等级，例如 `normal` / `important` / `maintenance`
- `showOnce`：是否只展示一次
- `startAt`：开始展示时间
- `endAt`：结束展示时间

## 发布新版本流程

1. 构建新版 APK。
2. 在本仓库创建 GitHub Release，例如 `v1.1.0`。
3. 上传 APK，例如 `HuanzhouAI-v1.1.0.apk`。
4. 计算 APK SHA256。
5. 更新 `update.json`：
   - `latestVersionCode`
   - `latestVersionName`
   - `apkUrl`
   - `apkSize`
   - `sha256`
   - `releasePageUrl`
   - `publishedAt`
6. 提交并推送到 `main` 分支。

## 计算 SHA256

Linux / macOS：

```bash
sha256sum HuanzhouAI-v1.1.0.apk
```

Windows PowerShell：

```powershell
Get-FileHash .\HuanzhouAI-v1.1.0.apk -Algorithm SHA256
```
