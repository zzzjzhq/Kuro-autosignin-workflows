# Kuro-AutoSignin-workflows

自动化每日任务，轻松管理库街区论坛与游戏签到 （魔改workflow）.

## 注意

仅供学习交流使用，请勿用于非法用途

## 使用说明
# 库街区 Auto Sign Job

你可以在每天指定的时间自动运行签到脚本(包含社区签到和奖励签到)，而无需手动操作。
注：原仓库[[Kuro-autosignin](https://github.com/mxyooR/Kuro-autosignin)]有消息推送等功能，魔改版注释掉了

## 如何使用

### 1. Fork 仓库

首先，点击右上角的 `Fork` 按钮，将这个仓库 Fork 到你自己的 GitHub 账户下。

### 2. 设置 GitHub Secrets

为了确保签到脚本能够正常运行，你需要将必要的敏感信息([token](https://blog.tomys.top/2023-07/kuro-token/))存储在 GitHub
Secrets 中。

#### 配置示例
```
[{
  "name" : "被签到者的姓名",
  "wwroleId": "可以抓包获取 鸣潮的uid 不签到不填空着",
  "eeeroleId": "可以抓包获取 战双的uid 不签到不填空着",
  "tokenraw": "抓包获取的token",
  "userId": "库街区的id 可以抓包获取",
  "devCode":"设备代码 可以随机生成或者抓包获取",
  "distinct_id": "抓包获取同名字段"
}]
```

1. 进入你 Fork 后的仓库页面。
2. 点击 `Settings` 选项卡。
3. 在左侧菜单中选择 `Secrets and variables` > `Actions`。
4. 点击 `New repository secret` 按钮。
5. 在 `Name` 字段中输入 `CONFIGS`，在 `Value` 字段中输入你的签到脚本所需的配置，注意不需要转义，写入正确的数组JSON即可。
6. 点击 `Add secret` 保存。

### 3. 触发工作流

#### 自动触发

工作流已经配置为每天北京时间早上 8 点（UTC 时间 24:00）自动运行。你无需手动操作，只需确保仓库中的代码和 Secrets 配置正确即可。

#### 手动触发

如果你想立即运行工作流，可以手动触发：

1. 进入你 Fork 后的仓库页面。
2. 点击 `Actions` 选项卡。
3. 在左侧菜单中选择 `Auto Sign Job`。
4. 点击右上角的 `Run workflow` 按钮，选择 `Run workflow` 即可手动触发。

### 4. 查看运行结果

每次工作流运行后，你可以在 `Actions` 选项卡中查看运行结果。如果签到成功，你应该能够看到相应的日志输出。签到失败则会报错。

## 注意事项

- 确保 `CONFIGS` 的安全性，不要将其直接写在代码中。
- 如果需要修改定时任务的执行时间，可以编辑 [`.github/workflows/auto_sign.yaml`](.github/workflows/auto_checkin.yaml) 文件中的
  `cron` 表达式。
- fork仓库actions在仓库没有改动的情况下最多只能白嫖60天，之后actions的workflow功能会被禁用，可以通过定期提交、创建 issue 或自动同步上游仓库来保持活跃，避免 60 天禁用

## 特别感谢

原仓库 [[Kuro-autosignin](https://github.com/mxyooR/Kuro-autosignin)]
workflow参考：[[kurobbs_auto_checkin](https://github.com/leeezep/kurobbs_auto_checkin)]
