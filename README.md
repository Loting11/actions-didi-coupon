# 滴滴打车自动领券

基于 [hudiemon/didi](https://github.com/hudiemon/didi) 项目，通过 GitHub Actions 每天自动领取滴滴打车优惠券。

## 功能

- 🚖 滴滴打车自动领券（快车/顺风车/代驾等）
- 🐷 花小猪自动领券
- ⛽ 滴滴加油/洗车优惠券
- 😺 福利中心签到领福利金
- 🌳 滴滴果园签到/浇水
- 🎮 养券游戏

## 如何获取 TOKEN

1. 手机或电脑浏览器打开领券页面：
   ```
   https://vv.didi.cn/a8ZdG0j?source_id=88446DIDI88446tkmmchild1001&ref_from=dunion
   ```
2. 点击**立即领取**，登录你的滴滴账号
3. 按 `F12` 打开浏览器开发者工具，切到 **Console（控制台）** 标签
4. 输入以下命令并回车：
   ```js
   localStorage.getItem('didih5_trinity_login_ticket_role_121230').replace(/"/g, '')
   ```
5. 复制输出的字符串，这就是你的 Token

> ⚠️ Token 有效期有限（约7-30天），过期后需要重新获取并更新 Secret。

## 部署步骤

### 1. Fork 本仓库

点击右上角 **Fork** 按钮，将仓库 Fork 到你的 GitHub 账号下。

### 2. 配置 Secret

1. 进入你 Fork 的仓库 → **Settings** → **Secrets and variables** → **Actions**
2. 点击 **New repository secret**
3. Name 填 `TOKENS`，Value 粘贴你的 Token
4. 多个账号用英文分号 `;` 分隔，例如：`token1;token2;token3`
5. 保存

### 3. 启用 Actions

进入 **Actions** 标签页，如果提示禁用，点击 **I understand my workflows, go ahead and enable them**。

### 4. 手动测试

在 Actions 页面选择 **自动任务** workflow，点击 **Run workflow** 手动触发一次，检查是否正常运行。

## 定时执行

- 每天北京时间 **10:30** 自动执行（cron: `30 02 * * *`，UTC 时间）
- 也可随时手动触发

## 执行结果示例

```
🚖【早高峰折扣券】9折、最高抵扣20元
🚖【晚高峰折扣券】8.8折、最高抵扣10元
🚖【特惠快车午后券】9.5折、最高抵扣20元
🚖【白平峰折扣券】9.5折、最高抵扣10元
🚖【晚平峰立减券】5元、满60减5元
🐷【花小猪折扣券】3折、最高抵扣8元
⛽【超值优惠券】10元、满200减10元
😺【福利中心】福利金：94 ≈ 0.94元
🍩【滴滴果园】签到成功，2化肥
🚿【滴滴果园】浇水完成
```

## 注意事项

- 🫵 滴滴果园必须手动完成新手任务，脚本无法自动完成
- Token 过期后需重新获取并更新 GitHub Secret
- 建议每天运行1-2次即可，频繁运行可能导致账号异常
