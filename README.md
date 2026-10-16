# Mitra - LazyCat App

[Mitra](https://github.com/a11delavar/mitra)（一体化日历：事件与任务规划）的懒猫微服（LazyCat）打包。

## 模式

- **镜像模式（mirror）**：`ghcr.io/a11delavar/mitra` 镜像经 `ghcr.1ms.run` 加速器拉取，`require_digest_match: true` 校验镜像内容与上游一致。
- **自动跟随上游**：GHCR 无版本 tag（`latest` 可变），采用 digest 比对 + `bump: patch`——上游发布新 release 后 `latest` 更新，自动 patch +1 发布。
- **喵喵商店发布**：仅私有商店（MiaoMiao private store），不发布官方商店。

## 说明

- 单容器 Next.js，数据卷 `/lzcapp/var/mitra:/app/data`（开箱即用，单用户无登录）
- CalDAV / Google / Apple / Notion / Tempo 同步在应用内配置（连接外部服务需公网）
- 健康检查 `/api/health`（node fetch）

## 所需 Secrets

| Secret | 说明 |
| --- | --- |
| `APPSTORE_URL` / `APPSTORE_TOKEN` | 喵喵商店 API 地址与发布令牌 |
| `APP_ID` | 可选 |
| `PRIVATE_STORE_GROUP_CODES` | 可选，私有分组码 |

## 许可

AGPL-3.0（上游）
