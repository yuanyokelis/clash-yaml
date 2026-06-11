# Clash 配置使用说明（口语化）

欢迎！这里把仓库里的三份配置讲清楚，并额外给出 OpenClash（路由器）和 Clash Verge（Android）导入的逐步示意图，方便你一步步操作。下面是更通俗易懂的版本，适合刚接触的朋友按着做。

仓库里的三份文件：

- clashverge全局扩展覆写配置dns防泄漏自动去除广告.txt — 给手机端（Clash Verge/Clash Meta）用的覆写模块，自动去广告、做 DNS 防泄漏。建议改后缀为 .yaml 导入更稳。 
- openclash覆写模块dns防泄漏去广告.txt — 给路由器上跑的 OpenClash 用的覆写模块，路由器层面统一防护。也建议改成 .yaml。
- 多订阅合并模板dns防泄漏自动去除广告.yaml — 多个订阅合并成一份配置的模板，带 DNS 防泄漏和广告去除。把模板里的占位订阅换成你的链接就能用了。

我把 README 改成了更加口语化的说明，并做了两个功能：

1) OpenClash（LuCI）导入示意：4 步截图，图里标注了常按的位置（示意图，不是你设备的真实截图）。
2) Clash Verge 导入示意：4 步截图，教你怎么在手机上导入本地文件。 

下面直接给出快速步骤（按图操作）：

---

OpenClash（路由器）导入示意

快速步骤：
1. 登录路由器的 LuCI 管理界面（通常是 http://192.168.1.1）。
   - 看图：images/openclash_step1.svg
2. 进入 Services → OpenClash，找到“配置管理/覆写配置”或“自定义配置”。粘贴或上传本仓库的 `openclash-overwrite.yaml` 内容。 
   - 看图：images/openclash_step2.svg
3. 保存并应用（Apply），等待 OpenClash 重新加载。确认日志无错误。 
   - 看图：images/openclash_step3.svg
4. 确认 DNS 模式（fake-ip 或 redir-host）和上游 DNS 已设置为可信的（例如 1.1.1.1 / 8.8.8.8）。
   - 看图：images/openclash_step4.svg

小提示：
- 上传前先备份当前配置（OpenClash 通常有历史快照）。
- 如果网络异常，先回退到备份并检查本覆写是否与主配置有冲突（同名 proxy-group 等）。

---

Clash Verge（手机）导入示意

快速步骤：
1. 把需要的文件（比如 `clashverge-覆盖.yml` 或合并模板）传到手机。可以用网盘、邮件或 USB 传输。
   - 看图：images/clashverge_step1.svg
2. 打开 Clash Verge / Clash Meta，进入 Profiles（配置）或导入页面，选择“从文件导入”或类似按钮，选中刚才的文件。 
   - 看图：images/clashverge_step2.svg
3. 导入成功后在 Profiles 列表里启用该配置（或把它作为覆写模块启用）。确认没有导入报错。 
   - 看图：images/clashverge_step3.svg
4. 确认 DNS 模式（fake-ip / redir-host）与本地 DNS 设置配合使用，测试常用网站是否被正确代理/直连。 
   - 看图：images/clashverge_step4.svg

小提示：
- 手机端对大文件解析可能慢，导入后耐心等待。若出现语法错误，使用 UTF-8 无 BOM 保存并重试。
- 如果想随时回退，记得导出原本的配置文件保存。

---

其他补充（口语化建议）

- 新手优先：如果你只是想用节点，优先把多订阅模板里的订阅链接替换为你的链接，导入后启动“自动选择”或“轮询”代理组就行。不要随意改复杂的 proxy-groups 配置，先跑起来再慢慢调。 
- 更新规则：广告/域名会变，建议定期刷新订阅或把规则来源换成常更新的 provider。 
- 出问题先看日志：路由器/客户端都有日志，导入失败或生效异常先看日志里第一条错误信息就能快定位。 

---

我已经在仓库里添加了这些示意图片（SVG），以及把 README 替换为口语化版本。你可以直接在仓库查看：
https://github.com/yuanyokelis/clash-yaml/blob/main/README.md

需要我接着做的事（选其一）：
- 把 README 改回更“技术化”的风格；
- 把示意图替换为你上传的真实截图（你选 A 并上传图片），我来替换并标注；
- 把仓库里的 .txt 文件批量改成 .yaml，并在文件里加入更明确的文件名建议和注释。

告诉我接下来的步骤就行，我来执行。