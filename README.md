# The-BlackHAT-Roadmap-CN (黑帽路线图中文本地化版)

> **本项目基于原作者 `SagarBiswas-MultiHAT` 的开源神作进行深度本地化重构。**
> 🔗 **原项目地址：** [https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap)
> 📜 **开源协议：** 本项目严格遵循原作者的 [CC BY-SA 4.0](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap/blob/main/LICENSE-DOCS) 协议，所有内容保持开源共享。

---

### 💡 为什么不用浏览器自带翻译？（本项目存在的意义）

因为原版 4 万多行的硬核文档里，包含了大量网络安全专业术语（如 OPSEC、IoC、C2、ANPR 等），机翻不仅词不达意，更致命的是**无法处理文档内数百张英文架构图与流程图**。

本项目致力于提供：
1. **图表全量汉化重绘**：将原版全英文的流程图、金字塔图，用 PPT/Draw.io 重新绘制为纯中文高清版，彻底打通阅读障碍。
2. **国内网络环境优化（规划中）**：针对原版中因 GFW 导致无法访问的链接、无法拉取的镜像，提供国内平替方案或加速渠道指引。

---

### 🚧 当前汉化进度与共建指南

*   **当前进度：** 核心目录已翻译，图表重绘与正文精翻正在持续爆肝中...
*   **需要帮忙？** 项目还剩下100多张英文图表需要重绘。如果你精通 PPT/Draw.io，或者想帮忙校对机翻术语，欢迎加入！
*   **如何提交 PR：** 
    1. Fork 本仓库。
    2. 新建你的分支(`git checkout -b feature/你的名字`)
    3. 提交你的修改`(git commit -m '汉化：翻译了XX章节')`
    4. 推送(`git push origin feature/你的名字`)
    5. 在本仓库发起 Pull Request。

🤝 **欢迎国内安全爱好者一起建设，打造最适合中国极客的安全路线图！**

---
（以下保留原作者原本的内容与致谢）

<div align="center">
</div>


<div align="center">

<p align="center">
  <img src="assets/banner.svg" alt="The BlackHAT Roadmap v1.2.2" width="850" />
</p>

### 从零到操作员。不设上限，不作退让。

从底层硬件起步、零基础直达顶尖水准的权威进攻性安全工程课程体系、底层系统教学大纲与作战安全汇编。

<p align="center">
  <a href="https://github.com/SagarBiswas-MultiHAT"><img src="https://img.shields.io/badge/Author-Sagar%20Biswas-red.svg?style=for-the-badge&logo=github" alt="Author" /></a>
  <a href="#"><img src="https://img.shields.io/badge/Version-v1.2.2-00ff66.svg?style=for-the-badge&logo=target" alt="Version" /></a>
  <a href="#"><img src="https://img.shields.io/badge/Curriculum-44%2C900%2B%20Lines-blue.svg?style=for-the-badge&logo=gitbook" alt="Curriculum Volume" /></a>
  <a href="#"><img src="https://img.shields.io/badge/Phases-8%20Phases%20(--1%20to%206)-orange.svg?style=for-the-badge&logo=target" alt="Phases" /></a>
  <a href="#"><img src="https://img.shields.io/badge/Offensive%20Tools-300%2B%20Cataloged-red.svg?style=for-the-badge&logo=gnubash" alt="Tools" /></a>
  <a href="#"><img src="https://img.shields.io/badge/MITRE%20ATT%26CK-Enterprise%20v15%20%7C%20ICS%20%7C%20ATLAS-yellow.svg?style=for-the-badge&logo=matrix" alt="MITRE ATT&CK" /></a>
  <a href="payloads/"><img src="https://img.shields.io/badge/Payloads-C%20%7C%20Rust-purple.svg?style=for-the-badge&logo=rust" alt="Offensive Payloads" /></a>
  <a href=".github/CONTRIBUTING.md"><img src="https://img.shields.io/badge/Contributions-Welcome-brightgreen.svg?style=for-the-badge&logo=git" alt="PRs Welcome" /></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/Code%20License-MIT-purple.svg?style=for-the-badge&logo=opensourceinitiative" alt="Code License: MIT" /></a>
  <a href="LICENSE-DOCS"><img src="https://img.shields.io/badge/Docs%20License-CC%20BY--SA%204.0-blue.svg?style=for-the-badge&logo=creative-commons" alt="Docs License: CC BY-SA 4.0" /></a>
</p>

<p align="center">
  <img src="https://img.shields.io/github/stars/SagarBiswas-MultiHAT/The-BlackHAT-roadmap?style=flat-square&logo=github&color=ffcc00" alt="Stars" />
  <img src="https://img.shields.io/github/forks/SagarBiswas-MultiHAT/The-BlackHAT-roadmap?style=flat-square&logo=git-fork&color=orange" alt="Forks" />
  <img src="https://img.shields.io/github/watchers/SagarBiswas-MultiHAT/The-BlackHAT-roadmap?style=flat-square&logo=eye&color=blue" alt="Watchers" />
  <img src="https://img.shields.io/github/repo-size/SagarBiswas-MultiHAT/The-BlackHAT-roadmap?style=flat-square&logo=database&color=green" alt="Repo Size" />
  <img src="https://img.shields.io/github/last-commit/SagarBiswas-MultiHAT/The-BlackHAT-roadmap?style=flat-square&logo=clock" alt="Last Commit" />
</p>

<p align="center">
  <a href="#master-curriculum--navigation-hub">课程索引</a> •
  <a href="#可视化学习路径与进阶路线图">可视化学习路径</a> •
  <a href="#可编译的进攻性工程载荷">武器化载荷</a> •
  <a href="#2025-2027-操作员模块">前沿模块</a> •
  <a href=".github/TRACKER.md">进度追踪表</a> •
  <a href="#引用与学术署名">引用</a> •
  <a href="#法律免责声明">法律声明</a> •
  <a href="#许可证与署名">许可证</a>
</p>

</div>

<div align="center">

```
44,900+ 行  ·  8 个阶段  ·  300+ 工具  ·  200+ ATT&CK 技术  ·  1,080+ 代码块  ·  150+ 图示  ·  325+ 行（载荷）
```

</div>

> 如果这套课程对你的进攻性安全之路有价值，欢迎**[点个 Star](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap/stargazers)**，帮助更多研究者和操作员发现它。

---

### 与众不同之处

- **从底层硬件起步。** 每个阶段都先讲透系统内部机制，再讲攻击技术，绝不提供“直接跑这个工具”之类的捷径。
- **可编译的进攻性代码。** 不是纸上谈兵。附带真实可用的 C 与 Rust 载荷，涵盖 PEB 遍历、DJB2 哈希与内存加载器。
- **先作战安全，后入侵。** 阶段 -1 排在阶段 0 之前。作战安全、威胁建模与匿名基础设施都是必修前提。
- **全面对齐 MITRE ATT&CK。** 200+ 项技术映射至 Enterprise v15、ICS 与 ATLAS。每一节都回扣这套框架。
- **覆盖别人跳过的内容。** 物理红队、无人机侦察、社会工程话术、量子 SNDL 与后量子密码学。

---

<a id="table-of-contents"></a>
<a id="master-curriculum--navigation-hub"></a>

### 从哪里开始

| 你的背景 | 推荐起点 | 模块数 | 预计用时 | 并行学习 |
| :--- | :--- | :---: | :---: | :--- |
| 所有人都从这里开始 | [阶段 -1：作战安全与基础设施](phases/PHASE_-1.md) | 24 | 4-6 周 | [最大匿名工作流](black-bag/Max_Anonymity_Workflow.md) · [生存战术](black-bag/BlackHat_Long-Term_Survival_Tactics.md) · [思维模式](field-guides/Philosophy_The_BlackHat_Mindset.md) · [常见问题](field-guides/FAQ.md) |
| 完全零基础 | [阶段 0：基础](phases/PHASE_0.md) | 23 | 12-16 周 | [实验环境搭建指南](field-guides/Lab_Setup_Guide.md) |
| Web 开发者 / 漏洞赏金猎人 | [阶段 1：Web 安全](phases/PHASE_1.md) | 39 | 8-12 周 | - |
| 系统管理员 / 网络工程师 | [阶段 2：网络与基础设施](phases/PHASE_2.md) | 23 | 10-14 周 | - |
| 逆向工程师 / CTF 选手 | [阶段 3：二进制利用与逆向工程](phases/PHASE_3.md) | 21 | 12-16 周 | [MITRE 参考](field-guides/MITRE_ATT&CK_Quick_Reference.md) · [工具（300+）](field-guides/Tools_Inventory.md) · [资源](field-guides/Resources_Aggregated.md) |
| 有经验的渗透测试人员 | [阶段 4：专项分支（4A-4I）](phases/PHASE_4.md) | 16 | 任选分支 | 选 1 个主修 + 1 个辅修 |
| 研究员 / 漏洞利用开发者 | [阶段 5：GREATEST](phases/PHASE_5.md) | 22 | 长期进行 | [结语](field-guides/Final_Word.md) |
| 特种操作员 | [阶段 6：特种作战](phases/PHASE_6.md) | 39 | 长期进行 | 与阶段 5 并行 · [结语](field-guides/Final_Word.md) |

Fork [进度追踪表](.github/TRACKER.md)，即可跟踪你在各阶段的进展情况。

<details>
<summary><strong>阅读指南</strong></summary>

<br/>

- 建议用手机阅读：全书 150+ 张高清图，在手机上可以轻松放大缩小。
- 手机端不要用 GitHub App，请改用浏览器并以桌面模式访问 GitHub。
- 所有图表均按浅色模式测试，因此不建议使用深色模式。
- 遇到问题？有哪里看不懂？有建议想提？欢迎到 [GitHub Discussions](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap/discussions/1) 参与讨论、留言。始终欢迎社区的反馈与贡献。
- 发现失效链接、错别字、载荷错误或 Bug，请[提交 issue](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap/issues)。

</details>

---

<a id="curricular-progression-map"></a>
## 可视化学习路径与进阶路线图

<div align="center">
<table><tr><td>

<img src="assets/diagrams/Final_Word/1._THE_ROADMAP_AT_A_GLANCE.png" alt="THE ROADMAP AT A GLANCE" width="1600"/>

</td></tr></table>
</div>

---

## 目录

<a id="phase--1"></a>
#### [阶段 -1：强化作战安全与匿名基础设施](phases/PHASE_-1.md)

<details>
<summary><strong>展开阶段 -1 教学大纲（24 个模块）</strong></summary>

<br/>

1. [为什么它排在一切之前](phases/PHASE_-1.md#1-为什么这一阶段必须放在最前面)
2. [真实的操作员、真实的失败、真实的教训](phases/PHASE_-1.md#2-真实操作者真实失败真实教训)
3. [法律框架：先读这一节](phases/PHASE_-1.md#3-法律框架先读这一节)
4. [反 OSINT：动手前先摸清自己的暴露面](phases/PHASE_-1.md#4-反-osint动手之前先弄清自己的暴露面)
5. [威胁建模：行动前先思考](phases/PHASE_-1.md#5-威胁建模想清楚再动手)
6. [通信安全：头号被捕风险点](phases/PHASE_-1.md#6-通讯安全最常见的被捕原因)
7. [手机与移动端作战安全](phases/PHASE_-1.md#7-手机与移动端-opsec)
8. [匿名基础设施搭建](phases/PHASE_-1.md#8-匿名基础设施搭建)
9. [匿名化栈：VPN、Tor 与链式串联](phases/PHASE_-1.md#9-匿名化链路vpntor-与层层串联)
10. [浏览器指纹：你正在被识别](phases/PHASE_-1.md#10-浏览器指纹你正在被识别)
11. [加密货币：为何选 Monero，以及它真实的运作方式](phases/PHASE_-1.md#11-加密货币为什么用-monero它是怎么运作的)
12. [身份隔离与文体计量分析](phases/PHASE_-1.md#12-身份隔离与文体学)
13. [安全研究操作系统](phases/PHASE_-1.md#13-安全研究操作系统)
14. [物理作战安全：多数指南忽略的一层](phases/PHASE_-1.md#14-物理-opsec大多数指南忽略的一层)
15. [时间与行为模式作战安全：隐形指纹](phases/PHASE_-1.md#15-时间与行为模式-opsec看不见的指纹)
16. [元数据：无声的杀手](phases/PHASE_-1.md#16-元数据无声的杀手)
17. [安全删除：不留任何痕迹](phases/PHASE_-1.md#17-安全删除不留痕迹)
18. [你接触的每套系统上都有哪些日志](phases/PHASE_-1.md#18-你碰过的每个系统上都有哪些日志)
19. [自己机器上的取证痕迹](phases/PHASE_-1.md#19-你自己机器上的取证痕迹) *（v5.5 新增）*
20. [冷启动攻击与 Evil Maid：具体缓解措施](phases/PHASE_-1.md#20-冷启动与邪恶女佣具体缓解措施) *（v5.5 扩充）*
21. [出事之后：焚毁协议](phases/PHASE_-1.md#21-出了事怎么办燃烧协议) *（v5.5 新增）*
22. [团队作战安全与小组结构](phases/PHASE_-1.md#22-小组-opsec-与细胞结构) *（v5.5 新增）*
23. [阶段 -1 里程碑清单](phases/PHASE_-1.md#23-阶段--1-里程碑清单)
24. [资源](phases/PHASE_-1.md#24-资源)

</details>

<div align="right"><a href="#table-of-contents">↑ 返回目录</a></div>

---

<a id="phase-0"></a>
#### [阶段 0：底层基础与系统内部机制](phases/PHASE_0.md)

<details>
<summary><strong>展开阶段 0 教学大纲（23 个模块）</strong></summary>

<br/>

1. [目标与理念](phases/PHASE_0.md#1-目标与理念)
2. [如何使用这一阶段](phases/PHASE_0.md#2-如何使用这一阶段)
3. [前置要求](phases/PHASE_0.md#3-前置要求)
4. [检查点：结束时你必须掌握什么](phases/PHASE_0.md#4-检查点结束时你必须掌握的内容)
5. [时间轴与并行轨道架构](phases/PHASE_0.md#5-时间线与并行轨道架构)
6. [第 1 节：操作系统基础](phases/PHASE_0.md#6-第1节操作系统基础)
7. [第 1B 节：Bash 脚本基础](phases/PHASE_0.md#7-第1b节bash-脚本基础)
8. [第 2 节：C 语言编程](phases/PHASE_0.md#8-第2节c-编程)
9. [第 3 节：Python 脚本编程](phases/PHASE_0.md#9-第3节python-脚本)
10. [第 4 节：网络基础](phases/PHASE_0.md#10-第4节网络基础)
11. [第 5 节：x86-64 汇编](phases/PHASE_0.md#11-第5节x86-64-汇编)
12. [第 6 节：逆向工程基础](phases/PHASE_0.md#12-第6节逆向工程基础)
13. [第 7 节：密码学入门](phases/PHASE_0.md#13-第7节密码学入门)
14. [第 8 节：ARM64 体系结构认知](phases/PHASE_0.md#14-第8节arm64-架构认知)
15. [第 9 节：glibc 内部机制入门](phases/PHASE_0.md#15-第9节glibc-内部机制入门)
16. [里程碑项目：完整规格卡](phases/PHASE_0.md#16-里程碑项目完整规格卡)
17. [实验环境搭建](phases/PHASE_0.md#17-实验室搭建)
18. [GDB 配置与命令速查](phases/PHASE_0.md#18-gdb-设置与命令参考)
19. [CTF 平台指南](phases/PHASE_0.md#19-ctf-平台指南)
20. [常见失败点与修复方法](phases/PHASE_0.md#20-常见失败点与修复)
21. [阶段 0 总清单](phases/PHASE_0.md#21-阶段-0-总清单)
22. [接下来做什么](phases/PHASE_0.md#22-接下来是什么)
23. [资源汇总](phases/PHASE_0.md#23-资源汇总)

</details>

<div align="right"><a href="#table-of-contents">↑ 返回目录</a></div>

---

<details>
<summary><strong>与阶段 0 并行的学习：作战安全、思维模式与常见问题（4 本主指南）</strong></summary>

<br/>

<a id="blackhat-long-term-survival-tactics"></a>
#### [BlackHat 长期生存战术](black-bag/BlackHat_Long-Term_Survival_Tactics.md)

1. [写给初学者：从这里开始](black-bag/BlackHat_Long-Term_Survival_Tactics.md#写给初学者从这里开始)
2. [威胁建模框架](black-bag/BlackHat_Long-Term_Survival_Tactics.md#威胁建模框架)
3. [第 1 节：数字身份与人设架构](black-bag/BlackHat_Long-Term_Survival_Tactics.md#第-1-节数字身份与人设架构)
4. [第 2 节：设备安全 - 操作系统与硬件](black-bag/BlackHat_Long-Term_Survival_Tactics.md#第-2-节设备安全---操作系统与硬件)
5. [第 3 节：网络层作战安全](black-bag/BlackHat_Long-Term_Survival_Tactics.md#第-3-节网络层作战安全)
6. [第 4 节：通信安全](black-bag/BlackHat_Long-Term_Survival_Tactics.md#第-4-节通信安全)
7. [第 5 节：加密货币与资金安全](black-bag/BlackHat_Long-Term_Survival_Tactics.md#第-5-节加密货币与资金安全)
8. [第 6 节：物理位置安全](black-bag/BlackHat_Long-Term_Survival_Tactics.md#第-6-节物理位置安全)
9. [第 7 节：外貌伪装与反监视](black-bag/BlackHat_Long-Term_Survival_Tactics.md#第-7-节外貌与反监视)
10. [第 8 节：社会工程防御（自我保护）](black-bag/BlackHat_Long-Term_Survival_Tactics.md#第-8-节社会工程防御自我保护)
11. [第 9 节：AI 驱动的监视规避（2027）](black-bag/BlackHat_Long-Term_Survival_Tactics.md#第-9-节ai-驱动的监视规避2027)
12. [第 10 节：区块链取证威胁模型（2027）](black-bag/BlackHat_Long-Term_Survival_Tactics.md#第-10-节区块链取证威胁建模2027)
13. [第 11 节：暗网作战安全](black-bag/BlackHat_Long-Term_Survival_Tactics.md#第-11-节暗网作战安全)
14. [第 12 节：法律层面的反情报](black-bag/BlackHat_Long-Term_Survival_Tactics.md#第-12-节法律反情报)
15. [第 13 节：长期生存规划](black-bag/BlackHat_Long-Term_Survival_Tactics.md#第-13-节长期生存规划)
16. [第 14 节：紧急撤离协议](black-bag/BlackHat_Long-Term_Survival_Tactics.md#第-14-节紧急撤离预案)
17. [第 15 节：反执法（Counter-LE）意识](black-bag/BlackHat_Long-Term_Survival_Tactics.md#第-15-节反执法le意识)
18. [第 16 节：2027 年国际司法辖区](black-bag/BlackHat_Long-Term_Survival_Tactics.md#第-16-节2027-年国际司法辖区)
19. [第 17 节：作战安全黄金法则](black-bag/BlackHat_Long-Term_Survival_Tactics.md#第-17-节作战安全黄金法则)
20. [第 18 节：案例研究](black-bag/BlackHat_Long-Term_Survival_Tactics.md#第-18-节案例研究)
21. [第 19 节：高级硬件攻击抗性](black-bag/BlackHat_Long-Term_Survival_Tactics.md#第-19-节高级硬件攻击防护)
22. [第 20 节：内存取证与冷启动防御](black-bag/BlackHat_Long-Term_Survival_Tactics.md#第-20-节内存取证与冷启动防御)
23. [第 21 节：服务端检测与 eBPF 认知](black-bag/BlackHat_Long-Term_Survival_Tactics.md#第-21-节服务端检测与-ebpf-意识)
24. [作战速查清单](black-bag/BlackHat_Long-Term_Survival_Tactics.md#快速参考行动清单)

<div align="right"><a href="#table-of-contents">↑ 返回目录</a></div>

---

<a id="maximum-anonymity-workflow"></a>
#### [最大匿名工作流](black-bag/Max_Anonymity_Workflow.md)

1. [核心链路：从本机到目标](black-bag/Max_Anonymity_Workflow.md#1-核心链路从本地机器到目标)
2. [每类对手各自看到什么](black-bag/Max_Anonymity_Workflow.md#2-每个对手能看到什么)
3. [作战安全失效金字塔：为什么光有链路还不够](black-bag/Max_Anonymity_Workflow.md#3-作战安全失效金字塔为什么只有链路还不够)
4. [最大匿名的七层结构](black-bag/Max_Anonymity_Workflow.md#4-最大匿名的七层结构)
5. [三重身份模型](black-bag/Max_Anonymity_Workflow.md#5-三身份模型)
6. [Whonix：架构级的防泄漏保障](black-bag/Max_Anonymity_Workflow.md#6-whonix架构级的防泄漏保证)
7. [威胁模型分级：校准你的技术栈](black-bag/Max_Anonymity_Workflow.md#7-威胁模型分级校准你的技术栈)
8. [技术栈验证清单](black-bag/Max_Anonymity_Workflow.md#8-技术栈验证清单)
9. [会击穿链路的常见错误](black-bag/Max_Anonymity_Workflow.md#9-会让链路断裂的常见错误)
10. [下一步往哪走](black-bag/Max_Anonymity_Workflow.md#10-接下来去哪里)

<div align="right"><a href="#table-of-contents">↑ 返回目录</a></div>

---

<a id="philosophy-the-blackhat-mindset"></a>
#### [理念：BlackHat 思维模式](field-guides/Philosophy_The_BlackHat_Mindset.md)

1. [这不是什么](field-guides/Philosophy_The_BlackHat_Mindset.md#1-what-this-is-not)
2. [BlackHat 究竟是什么](field-guides/Philosophy_The_BlackHat_Mindset.md#2-what-a-blackhat-actually-is)
3. [认知进阶路径](field-guides/Philosophy_The_BlackHat_Mindset.md#3-the-cognitive-progression)
4. [真正重要的区分：学生、操作员、研究员](field-guides/Philosophy_The_BlackHat_Mindset.md#4-真正重要的分野)
5. [GREATEST 与「好」- 2027 版](field-guides/Philosophy_The_BlackHat_Mindset.md#5-greatest-vs-good-the-2027-edition)
6. [BlackHat 思维模式的七大支柱](field-guides/Philosophy_The_BlackHat_Mindset.md#6-the-seven-pillars-of-the-blackhat-mindset)
   - [支柱一：猎捕对抗性假设](field-guides/Philosophy_The_BlackHat_Mindset.md#pillar-i-adversarial-assumption-hunting)
   - [支柱二：先理解防御方，再发起攻击](field-guides/Philosophy_The_BlackHat_Mindset.md#pillar-ii-understand-the-defender-before-you-attack)
   - [支柱三：原语思维重于工具思维](field-guides/Philosophy_The_BlackHat_Mindset.md#pillar-iii-primitive-thinking-over-tool-thinking)
   - [支柱四：耐心与行动静默](field-guides/Philosophy_The_BlackHat_Mindset.md#pillar-iv-patience-and-operational-silence)
   - [支柱五：无声地失败](field-guides/Philosophy_The_BlackHat_Mindset.md#pillar-v-fail-silently)
   - [支柱六：自负就是作战安全失误](field-guides/Philosophy_The_BlackHat_Mindset.md#pillar-vi-ego-is-an-opsec-failure)
   - [支柱七：研究姿态](field-guides/Philosophy_The_BlackHat_Mindset.md#pillar-vii-the-research-posture)
7. [2027 年的格局现实](field-guides/Philosophy_The_BlackHat_Mindset.md#7-the-2027-landscape-reality)
8. [心理框架](field-guides/Philosophy_The_BlackHat_Mindset.md#8-the-psychological-framework)
9. [现实校准 - 2027 更新](field-guides/Philosophy_The_BlackHat_Mindset.md#9-reality-check-updated-2027)
10. [最后的真相](field-guides/Philosophy_The_BlackHat_Mindset.md#10-the-closing-truth)

<div align="right"><a href="#table-of-contents">↑ 返回目录</a></div>

---

<a id="faq"></a>
#### [常见问题全解](field-guides/FAQ.md)

1. [入门](field-guides/FAQ.md#第一部分入门)
2. [硬件、操作系统与环境](field-guides/FAQ.md#第二部分硬件操作系统与环境)
3. [学习路径与方法论](field-guides/FAQ.md#第三部分学习路径与方法)
4. [认证与课程](field-guides/FAQ.md#第四部分认证与课程)
5. [技术问题](field-guides/FAQ.md#第五部分技术问题)
6. [AI、工具与 2027 年格局](field-guides/FAQ.md#第六部分ai工具与-2027-年的格局)
7. [漏洞赏金与实战练习](field-guides/FAQ.md#第七部分漏洞赏金与真实世界实践)
8. [心态、倦怠与保持作战状态](field-guides/FAQ.md#第八部分心态倦怠与保持作战状态)
9. [授权、作战安全与法律现实](field-guides/FAQ.md#第九部分授权opsec-与法律现实)
10. [没人问但该问的问题](field-guides/FAQ.md#第十部分没人问但该问的问题)
11. [2027 特种作战与前沿问题](field-guides/FAQ.md#第十一部分2027-特种作战与研究前沿问答)

<div align="right"><a href="#table-of-contents">↑ 返回目录</a></div>

</details>

---

<a id="phase-1"></a>
#### [阶段 1：现代 Web 与 API 攻击面](phases/PHASE_1.md)

<details>
<summary><strong>展开阶段 1 教学大纲（39 个模块）</strong></summary>

<br/>

1. [如何使用这一阶段](phases/PHASE_1.md#如何使用本阶段)
2. [难度地图](phases/PHASE_1.md#难度地图)
3. [开发者思维](phases/PHASE_1.md#开发者思维模式)
4. [逐周主线](phases/PHASE_1.md#逐周主线)
5. [卡住的时候怎么办](phases/PHASE_1.md#卡住的时候怎么办)
6. [第 0 节：实验环境搭建](phases/PHASE_1.md#第-0-节实验环境搭建)
7. [第 1 节：HTTP 基础](phases/PHASE_1.md#第-1-节http-基础)
8. [第 2 节：侦察与目标测绘](phases/PHASE_1.md#第-2-节信息收集与目标测绘)
9. [第 3 节：SQL 注入](phases/PHASE_1.md#第-3-节sql-注入)
10. [第 3.5 节：命令注入](phases/PHASE_1.md#第-35-节命令注入)
11. [第 4 节：跨站脚本（XSS）](phases/PHASE_1.md#第-4-节跨站脚本xss)
12. [第 5 节：CSRF 与 CORS 配置错误](phases/PHASE_1.md#第-5-节csrf-与-cors-配置错误)
13. [第 6 节：服务端请求伪造（SSRF）](phases/PHASE_1.md#第-6-节服务端请求伪造ssrf)
14. [第 7 节：XML 外部实体注入（XXE）](phases/PHASE_1.md#第-7-节xml-外部实体注入xxe)
15. [第 8 节：身份认证攻击](phases/PHASE_1.md#第-8-节身份认证攻击)
16. [第 8.5 节：NoSQL 注入](phases/PHASE_1.md#第-85-节nosql-注入)
17. [第 9 节：访问控制与 IDOR](phases/PHASE_1.md#第-9-节访问控制与-idor)
18. [第 10 节：业务逻辑缺陷](phases/PHASE_1.md#第-10-节业务逻辑漏洞)
19. [第 11 节：路径遍历 / LFI / RFI](phases/PHASE_1.md#第-11-节路径穿越--lfi--rfi)
20. [第 12 节：文件上传漏洞](phases/PHASE_1.md#第-12-节文件上传漏洞)
21. [第 13 节：服务端模板注入（SSTI）](phases/PHASE_1.md#第-13-节服务端模板注入ssti)
22. [第 14 节：HTTP 请求走私与 H2C 攻击](phases/PHASE_1.md#第-14-节http-请求走私与-h2c-攻击)
23. [第 15 节：竞争条件](phases/PHASE_1.md#第-15-节竞态条件)
24. [第 16 节：WebSocket 攻击](phases/PHASE_1.md#第-16-节websocket-攻击)
25. [第 17 节：GraphQL 攻击](phases/PHASE_1.md#第-17-节graphql-攻击)
26. [第 18 节：API 安全（OWASP API Top 10：2023）](phases/PHASE_1.md#第-18-节api-安全owasp-api-top-102023)
27. [第 19 节：原型链污染](phases/PHASE_1.md#第-19-节原型污染)
28. [第 20 节：Web 缓存投毒与欺骗](phases/PHASE_1.md#第-20-节web-缓存投毒与欺骗)
29. [第 21 节：OAuth2 与 OIDC 攻击](phases/PHASE_1.md#第-21-节oauth2-与-oidc-攻击)
30. [第 22 节：反序列化攻击](phases/PHASE_1.md#第-22-节反序列化攻击)
31. [第 23 节：点击劫持](phases/PHASE_1.md#第-23-节点击劫持)
32. [第 24 节：现代 SPA 与框架攻击](phases/PHASE_1.md#第-24-节现代-spa-与框架攻击)
33. [第 25 节：LLM 集成攻击面](phases/PHASE_1.md#第-25-节llm-集成攻击面)
34. [第 26 节：漏洞链式组合](phases/PHASE_1.md#第-26-节漏洞串联)
35. [里程碑项目](phases/PHASE_1.md#里程碑项目)
36. [工具参考与决策树](phases/PHASE_1.md#工具参考与决策树)
37. [Web 测试方法论框架](phases/PHASE_1.md#web-测试方法论框架)
38. [阶段 1 终期里程碑清单](phases/PHASE_1.md#阶段-1-最终里程碑清单)
39. [资源汇总](phases/PHASE_1.md#资源汇总)

</details>

<div align="right"><a href="#table-of-contents">↑ 返回目录</a></div>

---

<details>
<summary><strong>与阶段 1 并行的学习：企业级攻击实验（1 本主指南）</strong></summary>

<br/>

<a id="lab-setup-guide"></a>
#### [实验环境搭建指南](field-guides/Lab_Setup_Guide.md)

1. [概述与理念](field-guides/Lab_Setup_Guide.md#1-概述与理念)
2. [硬件要求](field-guides/Lab_Setup_Guide.md#2-硬件需求)
3. [虚拟机管理程序选型](field-guides/Lab_Setup_Guide.md#3-虚拟化层选择)
4. [实验网络架构](field-guides/Lab_Setup_Guide.md#4-实验网络架构)
5. [核心虚拟机库](field-guides/Lab_Setup_Guide.md#5-核心虚拟机库)
6. [攻击机：Kali Linux 2024+](field-guides/Lab_Setup_Guide.md#6-攻击机kali-linux-2024)
7. [开发机：Ubuntu 22.04 LTS](field-guides/Lab_Setup_Guide.md#7-开发机ubuntu-2204-lts)
8. [Windows 目标机与植入体开发机](field-guides/Lab_Setup_Guide.md#8-windows-目标机与植入物开发机)
9. [Active Directory 实验环境：GOAD](field-guides/Lab_Setup_Guide.md#9-active-directory-实验环境goad)
10. [恶意软件分析环境](field-guides/Lab_Setup_Guide.md#10-恶意软件分析环境)
11. [内核调试环境](field-guides/Lab_Setup_Guide.md#11-内核调试环境)
12. [容器攻击实验](field-guides/Lab_Setup_Guide.md#12-容器攻击实验环境)
13. [云上实验替代方案](field-guides/Lab_Setup_Guide.md#13-云端实验环境替代方案)
14. [作战安全层：Whonix + Qubes](field-guides/Lab_Setup_Guide.md#14-作战安全层whonix--qubes)
15. [检测可见性层：DetectionLab](field-guides/Lab_Setup_Guide.md#15-检测可见性层detectionlab)
16. [ICS/SCADA 实验](field-guides/Lab_Setup_Guide.md#16-icsscada-实验环境)
17. [硬件破解实验](field-guides/Lab_Setup_Guide.md#17-硬件破解实验环境)
18. [漏洞研究与模糊测试实验（阶段 5：GREATEST）](field-guides/Lab_Setup_Guide.md#18-漏洞研究与模糊测试实验环境阶段-5greatest)
19. [特种作战实验：物理、社会工程与量子（阶段 6）](field-guides/Lab_Setup_Guide.md#19-特种作战实验环境物理社会工程与量子阶段-6)
20. [快照纪律](field-guides/Lab_Setup_Guide.md#20-快照纪律)
21. [逐阶段实验环境演进](field-guides/Lab_Setup_Guide.md#21-逐阶段实验环境演进)
22. [环境验证清单](field-guides/Lab_Setup_Guide.md#22-环境验证清单)
23. [维护计划](field-guides/Lab_Setup_Guide.md#23-维护计划)

<div align="right"><a href="#table-of-contents">↑ 返回目录</a></div>

</details>

---

<a id="phase-2"></a>
#### [阶段 2：网络跳板与 Active Directory 精通](phases/PHASE_2.md)

<details>
<summary><strong>展开阶段 2 教学大纲（23 个模块）</strong></summary>

<br/>

1. [这一阶段要建立什么](phases/PHASE_2.md#1-本阶段建立什么)
2. [前置条件检查](phases/PHASE_2.md#2-先修要求检查)
3. [阶段 2 杀伤链](phases/PHASE_2.md#3-阶段-2-攻击链)
4. [实验拓扑](phases/PHASE_2.md#4-实验环境拓扑)
5. [时间轴概览](phases/PHASE_2.md#5-时间线概览)
6. [如何使用这一阶段](phases/PHASE_2.md#6-如何使用本阶段)
7. [第 1 节：侦察与 OSINT](phases/PHASE_2.md#第-1-节侦察与-osint)
8. [第 2 节：服务漏洞利用](phases/PHASE_2.md#第-2-节服务漏洞利用)
9. [第 3 节：提权 - Linux](phases/PHASE_2.md#第-3-节权限提升---linux)
10. [第 4 节：提权 - Windows](phases/PHASE_2.md#第-4-节权限提升---windows)
11. [第 5 节：凭据投毒与中继攻击](phases/PHASE_2.md#第-5-节凭据投毒与中继攻击)
12. [第 6 节：后渗透与横向移动](phases/PHASE_2.md#第-6-节后渗透与横向移动)
13. [第 6.6 节：Active Directory - 枚举与攻击](phases/PHASE_2.md#第-66-节active-directory-枚举与攻击)
14. [第 7 节：网络跳板与隧道](phases/PHASE_2.md#第-7-节网络跳板与隧道)
15. [第 8 节：无线攻击](phases/PHASE_2.md#第-8-节无线攻击)
16. [第 9 节：口令攻击方法论](phases/PHASE_2.md#第-9-节密码攻击方法论)
17. [第 10 节：AV/EDR 规避与载荷投递](phases/PHASE_2.md#第-10-节avedr-规避与载荷投递)
18. [第 11 节：C2 框架操作](phases/PHASE_2.md#第-11-节c2-框架操作)
19. [第 12 节：阶段 2 内部的作战安全](phases/PHASE_2.md#第-12-节阶段-2-中的-opsec)
20. [里程碑项目](phases/PHASE_2.md#里程碑项目)
21. [阶段 2 完成清单](phases/PHASE_2.md#阶段-2-完成检查清单)
22. [CTF 实验与练习靶场](phases/PHASE_2.md#ctf-靶场与练习目标)
23. [阶段 2 到阶段 3 的衔接](phases/PHASE_2.md#阶段-2-到阶段-3-的衔接)

</details>

<div align="right"><a href="#table-of-contents">↑ 返回目录</a></div>

---

<a id="phase-3"></a>
#### [阶段 3：系统与内核漏洞利用](phases/PHASE_3.md)

<details>
<summary><strong>展开阶段 3 教学大纲（21 个模块）</strong></summary>

<br/>

1. [这一阶段适合谁](phases/PHASE_3.md#本阶段适合谁)
2. [阶段 3 架构图](phases/PHASE_3.md#阶段-3-架构图)
3. [时间轴](phases/PHASE_3.md#时间线)
4. [目标与检查点](phases/PHASE_3.md#目标与检查点)
5. [里程碑项目](phases/PHASE_3.md#里程碑项目)
6. [模块 0：环境搭建](phases/PHASE_3.md#区块-0环境搭建)
7. [模块 1：二进制利用基础](phases/PHASE_3.md#区块-1二进制漏洞利用基础)
8. [模块 2：shellcode 编写](phases/PHASE_3.md#区块-2shellcode-编写)
9. [模块 3：利用缓解机制与绕过](phases/PHASE_3.md#区块-3漏洞利用缓解与绕过)
10. [模块 4：格式化字符串漏洞](phases/PHASE_3.md#区块-4格式化字符串漏洞)
11. [模块 5：堆利用 -- Linux glibc 现代篇](phases/PHASE_3.md#区块-5堆利用----linux-glibc-现代)
12. [模块 6：Windows 堆利用](phases/PHASE_3.md#区块-6windows-堆利用)
13. [模块 7：Linux 内核漏洞利用](phases/PHASE_3.md#区块-7linux-内核利用)
14. [模块 8：Linux 内核 SLUB/Slab 利用](phases/PHASE_3.md#区块-8linux-内核-slubslab-利用)
15. [模块 9：Windows 内核漏洞利用](phases/PHASE_3.md#区块-9windows-内核利用)
16. [模块 10：ARM64 利用 + PAC 绕过](phases/PHASE_3.md#区块-10arm64-利用--pac-绕过)
17. [模块 11：控制流保护（CFG）绕过](phases/PHASE_3.md#区块-11控制流保护cfg绕过)
18. [模块 12：Linux eBPF rootkit + 反检测](phases/PHASE_3.md#区块-12linux-ebpf-后门--反检测)
19. [模块 13：HVCI、VBS 与内核安全 2026-2027](phases/PHASE_3.md#区块-13hvcivbs-与-2026-2027-内核安全)
20. [模块 14：移动安全 -- Android 与 iOS](phases/PHASE_3.md#区块-14移动安全----android-与-ios)
21. [CTF 进阶与实验资源](phases/PHASE_3.md#ctf-进阶与实验资源)

</details>

<div align="right"><a href="#table-of-contents">↑ 返回目录</a></div>

---

<a id="phase-4"></a>
#### [阶段 4：专项操作员分支（4A-4I）](phases/PHASE_4.md)

<details>
<summary><strong>展开阶段 4 操作员分支与课程（16 个小节）</strong></summary>

<br/>

| 小节 | 主题 | 难度 | 预计用时 |
|---------|-------|------------|---------------|
| [阶段 4 导言](phases/PHASE_4.md#第4阶段高级实战技巧) | 阅读方式、配对关系、衔接清单、架构图 | - | 2 小时 |
| [4A](phases/PHASE_4.md#4a-植入体与恶意软件开发) | 植入体与恶意软件开发 | 专家级 | 8-12 周 |
| [4B](phases/PHASE_4.md#4b-c2-框架开发) | C2 框架开发 | 专家级 | 6-10 周 |
| [4C](phases/PHASE_4.md#4c-edr-规避与防御绕过) | EDR 规避与防御绕过 | 专家级 | 6-8 周 |
| [4D](phases/PHASE_4.md#4d-漏洞研究与-0-day-开发) | 漏洞研究与 0-Day 开发 | 专家级+ | 12-20 周 |
| [4E](phases/PHASE_4.md#4e-apt-持久化rootkit-与反取证) | APT 持久化、rootkit 与反取证 | 专家级 | 8-12 周 |
| [4F](phases/PHASE_4.md#4f-云aitm-钓鱼与高级-web) | 云、AiTM 钓鱼与高级 Web | 专家级 | 6-10 周 |
| [4G](phases/PHASE_4.md#4g-硬件固件与芯片) | 硬件、固件与芯片 | 专家级 | 8-16 周 |
| [4H](phases/PHASE_4.md#4h-供应链与生态系统攻击) | 供应链与生态攻击 | 专家级 | 4-8 周 |
| [4I](phases/PHASE_4.md#4i-active-directory-与身份实战技巧) | Active Directory 与身份作业手法 | 专家级 | 8-12 周 |
| [4J](phases/PHASE_4.md#4j-macos-与-linux-攻防实战技巧) | macOS 与 Linux 进攻性作业手法 | 进阶 | 4-8 周 |
| [4X](phases/PHASE_4.md#4x-物理红队现场实战技巧) | 物理红队（野外作业手法） | 进阶 | 4-8 周 |
| [MITRE 参考](phases/PHASE_4.md#第4阶段-mitre-attck-快速参考) | 阶段 4 全部小节的 ATT&CK 技术映射 | - | 参考 |
| [工具总表](phases/PHASE_4.md#第4阶段工具总表) | 按专项分类整理的全部工具 | - | 参考 |
| [完成关卡](phases/PHASE_4.md#第4阶段完成门槛) | 12 道二选一关卡，用于验证阶段 4 掌握的深度 | - | 检查点 |
| [之后往哪走](phases/PHASE_4.md#第4阶段之后是什么) | 从阶段 4 通往前 0.0001% 的路径 | - | 参考 |

</details>

<div align="right"><a href="#table-of-contents">↑ 返回目录</a></div>

---

<details>
<summary><strong>与阶段 4 并行的学习：战术矩阵、工具与文献（3 本主指南）</strong></summary>

<br/>

<a id="mitre-attck-quick-reference"></a>
#### [MITRE ATT&CK 速查手册](field-guides/MITRE_ATT&CK_Quick_Reference.md)

1. [企业战术概览](field-guides/MITRE_ATT&CK_Quick_Reference.md#1-enterprise-tactic-overview)
2. [TA0043：侦察](field-guides/MITRE_ATT&CK_Quick_Reference.md#2-ta0043-reconnaissance)
3. [TA0042：资源开发](field-guides/MITRE_ATT&CK_Quick_Reference.md#3-ta0042-resource-development)
4. [TA0001：初始访问](field-guides/MITRE_ATT&CK_Quick_Reference.md#4-ta0001-initial-access)
5. [TA0002：执行](field-guides/MITRE_ATT&CK_Quick_Reference.md#5-ta0002-execution)
6. [TA0003：持久化](field-guides/MITRE_ATT&CK_Quick_Reference.md#6-ta0003-persistence)
7. [TA0004：提权](field-guides/MITRE_ATT&CK_Quick_Reference.md#7-ta0004-privilege-escalation)
8. [TA0005：防御规避](field-guides/MITRE_ATT&CK_Quick_Reference.md#8-ta0005-defense-evasion)
9. [TA0006：凭据访问](field-guides/MITRE_ATT&CK_Quick_Reference.md#9-ta0006-credential-access)
10. [TA0007：发现](field-guides/MITRE_ATT&CK_Quick_Reference.md#10-ta0007-discovery)
11. [TA0008：横向移动](field-guides/MITRE_ATT&CK_Quick_Reference.md#11-ta0008-lateral-movement)
12. [TA0009：收集](field-guides/MITRE_ATT&CK_Quick_Reference.md#12-ta0009-collection)
13. [TA0011：命令与控制](field-guides/MITRE_ATT&CK_Quick_Reference.md#13-ta0011-command-and-control)
14. [TA0010：数据外传](field-guides/MITRE_ATT&CK_Quick_Reference.md#14-ta0010-exfiltration)
15. [TA0040：影响](field-guides/MITRE_ATT&CK_Quick_Reference.md#15-ta0040-impact)
16. [路线图阶段与技术映射](field-guides/MITRE_ATT&CK_Quick_Reference.md#16-roadmap-phase-to-technique-mapping)
17. [关键攻击链图示](field-guides/MITRE_ATT&CK_Quick_Reference.md#17-critical-attack-chain-diagrams)
18. [工具与技术映射](field-guides/MITRE_ATT&CK_Quick_Reference.md#18-tool-to-technique-mapping)
19. [MITRE ATLAS：AI/ML 攻击技术](field-guides/MITRE_ATT&CK_Quick_Reference.md#19-mitre-atlas-aiml-attack-techniques)
20. [ICS ATT&CK 速查](field-guides/MITRE_ATT&CK_Quick_Reference.md#20-ics-attck-quick-reference)
21. [检测信号索引](field-guides/MITRE_ATT&CK_Quick_Reference.md#21-detection-signal-index)

<div align="right"><a href="#table-of-contents">↑ 返回目录</a></div>

---

<a id="tools-inventory"></a>
#### [工具清单](field-guides/Tools_Inventory.md)

1. [如何阅读这份清单](field-guides/Tools_Inventory.md#如何阅读本清单)
2. [阶段 -1：作战安全与匿名化](field-guides/Tools_Inventory.md#phase-neg1-opsec)
3. [阶段 0：基础环境](field-guides/Tools_Inventory.md#phase-0-foundation)
4. [阶段 1：Web 应用安全](field-guides/Tools_Inventory.md#phase-1-web)
5. [阶段 2：侦察、网络与基础设施](field-guides/Tools_Inventory.md#phase-2-recon)
6. [阶段 3：二进制与系统漏洞利用](field-guides/Tools_Inventory.md#phase-3-binary)
7. [阶段 4A/B：植入体、C2 与加载器开发](field-guides/Tools_Inventory.md#phase-4ab-implant)
8. [阶段 4C：EDR / AV 规避](field-guides/Tools_Inventory.md#phase-4c-edr)
9. [阶段 4D：漏洞研究与 0-Day](field-guides/Tools_Inventory.md#phase-4d-vr)
10. [阶段 4E：APT 持久化、rootkit 与反取证](field-guides/Tools_Inventory.md#phase-4e-apt)
11. [阶段 4F：云、AiTM 与高级 Web](field-guides/Tools_Inventory.md#phase-4f-cloud)
12. [阶段 4G：硬件、SDR 与嵌入式](field-guides/Tools_Inventory.md#phase-4g-hardware)
13. [阶段 4H：供应链](field-guides/Tools_Inventory.md#phase-4h-supply-chain)
14. [阶段 4I：Active Directory 与身份](field-guides/Tools_Inventory.md#phase-4i-ad)
15. [AI / LLM 攻击面](field-guides/Tools_Inventory.md#ai-llm-attack-surface)
16. [阶段 5：GREATEST - 漏洞研究与 0-Day 挖掘](field-guides/Tools_Inventory.md#phase-5-greatest)
17. [阶段 6：特种作战 - 物理、社会与量子](field-guides/Tools_Inventory.md#phase-6-special-operations)
18. [练习平台](field-guides/Tools_Inventory.md#practice-platforms)
19. [必备资源](field-guides/Tools_Inventory.md#essential-resources)
20. [❌ 已废弃工具栈 - 请勿使用](field-guides/Tools_Inventory.md#deprecated-stack)

<div align="right"><a href="#table-of-contents">↑ 返回目录</a></div>

---

<a id="resources_aggregated"></a>
#### [资源汇总](field-guides/Resources_Aggregated.md)

1. [如何使用这一节](field-guides/Resources_Aggregated.md#1-how-to-use-this-section)
2. [阶段到资源的导航](field-guides/Resources_Aggregated.md#2-phase-to-resource-navigator)
3. [参考数据库](field-guides/Resources_Aggregated.md#3-reference-databases)
4. [YouTube 频道 - 2027 年仍在更新](field-guides/Resources_Aggregated.md#4-youtube-channels-active-2027)
5. [必读书单 - 按阶段排序](field-guides/Resources_Aggregated.md#5-essential-books-phase-ordered)
6. [课程 - 2027 年价格与时间](field-guides/Resources_Aggregated.md#6-courses-2027-pricing-and-timing)
7. [练习平台](field-guides/Resources_Aggregated.md#7-practice-platforms)
8. [博客与研究来源](field-guides/Resources_Aggregated.md#8-blogs-and-research-sources)
9. [恶意软件样本库与沙箱](field-guides/Resources_Aggregated.md#9-malware-sample-repositories-and-sandboxes)
10. [漏洞数据库与利用代码来源](field-guides/Resources_Aggregated.md#10-vulnerability-databases-and-exploit-sources)
11. [AI 与 LLM 安全资源](field-guides/Resources_Aggregated.md#11-ai-and-llm-security-resources)
12. [国家级行为体与 APT 研究](field-guides/Resources_Aggregated.md#12-nation-state-and-apt-research)
13. [社区与人脉网络](field-guides/Resources_Aggregated.md#13-community-and-networking)
14. [已废弃工具栈 - 请勿使用](field-guides/Resources_Aggregated.md#14-deprecated-stack-do-not-use)
15. [MITRE ATT&CK 参考 - 2027](field-guides/Resources_Aggregated.md#15-mitre-attck-reference-2027)
16. [实验环境搭建指南](field-guides/Resources_Aggregated.md#16-lab-setup-guide)
17. [阶段 5：GREATEST - 漏洞研究与 0-Day 资源](field-guides/Resources_Aggregated.md#17-phase-5-greatest-resources)
18. [阶段 6：特种作战资源](field-guides/Resources_Aggregated.md#18-phase-6-special-operations-resources)
19. [按阶段分类的资源矩阵](field-guides/Resources_Aggregated.md#19-resource-by-phase-matrix)

<div align="right"><a href="#table-of-contents">↑ 返回目录</a></div>

</details>

---

<a id="phase-5"></a>
#### [阶段 5：GREATEST（顶尖漏洞研究与 0-Day）](phases/PHASE_5.md)

<details>
<summary><strong>展开阶段 5 教学大纲（22 个模块）</strong></summary>

<br/>

1. [GREATEST 究竟是什么](phases/PHASE_5.md#1-greatest-究竟是什么)
2. [决定是否继续深入](phases/PHASE_5.md#2-继续前行的决定)
3. [GREATEST 不是什么](phases/PHASE_5.md#3-greatest-不是什么)
4. [GREATEST 的真正标志](phases/PHASE_5.md#4-greatest-的真正标志)
5. [你必须从阶段 4 带来的东西](phases/PHASE_5.md#5-你必须从阶段-4-带来的东西)
6. [你的研究环境：从零搭建](phases/PHASE_5.md#6-你的研究环境从零搭建)
7. [阶段 5 的头 30 天](phases/PHASE_5.md#7-阶段-5-的第一个-30-天)
8. [研究闭环：GREATEST 究竟如何找出 0-Day](phases/PHASE_5.md#8-研究循环greatest-究竟如何发现-0-day)
9. [补丁比对：最可教的研究入门路径](phases/PHASE_5.md#9-补丁对比进入研究最易上手的路径)
10. [面向研究的模糊测试：不只是崩溃，而是发现](phases/PHASE_5.md#10-为研究而模糊测试不只是崩溃而是发现)
11. [分诊：从崩溃到确认漏洞](phases/PHASE_5.md#11-分类处置从崩溃到确认漏洞)
12. [漏洞利用开发标准：真正的 PoC 长什么样](phases/PHASE_5.md#12-漏洞利用开发标准真正的-poc-长什么样)
13. [研究领域深度剖析（2026 至 2027 前沿）](phases/PHASE_5.md#13-研究领域深入2026-至-2027-前沿)
14. [漏洞利用市场：BlackHAT 的路径](phases/PHASE_5.md#14-漏洞利用市场blackhat-之路)
15. [公开路径：如果你选择披露](phases/PHASE_5.md#15-发表路径如果你选择披露)
16. [圈子：进入正确的房间](phases/PHASE_5.md#16-社群进入正确的圈子)
17. [完整书单：地上与地下](phases/PHASE_5.md#17-完整阅读清单地表与地下)
18. [思维差距：从阶段 4 操作员到 GREATEST 研究员](phases/PHASE_5.md#18-思维差距从阶段-4-操作者到-greatest-研究者)
19. [衡量你的进展](phases/PHASE_5.md#19-衡量你的进展)
20. [长期停滞：当一切毫无动静](phases/PHASE_5.md#20-长期失败当一切毫无进展)
21. [法律风险：GREATEST 操作员所处的环境](phases/PHASE_5.md#21-法律风险greatest-操作者的全景)
22. [算法](phases/PHASE_5.md#22-算法)

</details>

<div align="right"><a href="#table-of-contents">↑ 返回目录</a></div>

---

<a id="phase-6-parallel-learning-alongside-phase-5"></a>
#### [阶段 6：特种作战与对手模拟](phases/PHASE_6.md) *（与阶段 5 并行学习）*

<details>
<summary><strong>展开阶段 6 教学大纲（39 个模块与子学科）</strong></summary>

<br/>

1. [为什么要有阶段 6](phases/PHASE_6.md#为什么存在第-6-阶段)
2. [第 1 节：物理红队](phases/PHASE_6.md#第-1-部分物理红队)
   - [1.1 开锁：基础技能](phases/PHASE_6.md#11-开锁基础技能)
   - [1.2 撞匙与印模开锁](phases/PHASE_6.md#12-撞匙与压印开锁)
   - [1.3 绕过工具：比开锁更快](phases/PHASE_6.md#13-绕过工具比开锁更快)
   - [1.4 电子门禁绕过（Wiegand + OSDP）](phases/PHASE_6.md#14-电子门禁绕过)
   - [1.5 摄像头绕过与视觉监视反制](phases/PHASE_6.md#15-摄像头绕过与视觉监控反制)
   - [1.6 RFID / HID 克隆（老式 + 现代读卡器）](phases/PHASE_6.md#16-rfid--hid-克隆旧式与现代读卡器)
   - [1.7 证件卡外观克隆](phases/PHASE_6.md#17-证件视觉克隆)
   - [1.8 硬件植入：LAN Turtle + 规避 EDR 的回连](phases/PHASE_6.md#18-硬件植入lan-turtle--规避-edr-的回连)
   - [1.9 尾随进入与话术进入](phases/PHASE_6.md#19-尾随进入与托词进入)
   - [1.10 无人机侦察：完整课程（光学 + 热成像）](phases/PHASE_6.md#110-无人机侦察完整课程光学--热成像)
3. [第 2 节：社会工程](phases/PHASE_6.md#第-2-部分社会工程人的攻击面)
   - [2.1 心理学框架：影响力的六大原则](phases/PHASE_6.md#21-心理学框架影响力的六大原则)
   - [2.2 套话技巧](phases/PHASE_6.md#22-套话技巧)
   - [2.3 语音钓鱼 Vishing（完整话术 + 异议应对）](phases/PHASE_6.md#23-语音钓鱼完整话术--异议处理)
   - [2.4 钓鱼邮件的构造](phases/PHASE_6.md#24-邮件钓鱼构造)
   - [2.5 USB 投放攻击](phases/PHASE_6.md#25-usb-投放攻击)
   - [2.6 面对面社会工程：非语言与肢体语言](phases/PHASE_6.md#26-面对面社会工程非语言与肢体语言)
   - [2.7 话术中止信号与补救](phases/PHASE_6.md#27-托词中止信号与恢复)
   - [2.8 人设构建与身份履历编造](phases/PHASE_6.md#28-人设构建与身份故事)
   - [2.9 社会工程行动规划与度量](phases/PHASE_6.md#29-社会工程行动规划与度量)
4. [第 3 节：2027 年的量子计算](phases/PHASE_6.md#第-3-部分2027-年量子计算)
   - [3.1 威胁模型](phases/PHASE_6.md#31-威胁模型)
   - [3.2 SNDL 收集基础设施](phases/PHASE_6.md#32-sndl-收集基础设施)
   - [3.3 PQC 迁移攻击：降级](phases/PHASE_6.md#33-pqc-迁移攻击降级)
   - [3.4 ML-KEM 时序侧信道分析](phases/PHASE_6.md#34-ml-kem-时序侧信道分析)
   - [3.5 密码资产清点审计脚本](phases/PHASE_6.md#35-密码学资产清点审计脚本)
   - [3.6 操作员的后量子作战安全](phases/PHASE_6.md#36-操作员的-pqc-opsec)
   - [3.7 初学者实验路径](phases/PHASE_6.md#37-初学者实验路径5-周结构)
5. [第 4 节：红队行动](phases/PHASE_6.md#第-4-部分红队行动)
   - [4.1 接单前的范围界定问卷](phases/PHASE_6.md#41-行动前范围界定问卷)
   - [4.2 交战规则](phases/PHASE_6.md#42-交战规则文件)
   - [4.3 报告结构与撰写](phases/PHASE_6.md#43-报告结构与撰写)
   - [4.4 复盘方法论](phases/PHASE_6.md#44-复盘方法论)
   - [4.5 紫队与复测](phases/PHASE_6.md#45-紫队与复测)
   - [4.6 威胁情报驱动的测试：TIBER-EU 与 CBEST](phases/PHASE_6.md#46-威胁情报驱动的测试tiber-eu-与-cbest)
6. [第 5 节：收尾清理](phases/PHASE_6.md#第-5-部分行动后清理)
   - [5.1 数字足迹清除（Windows + Sysmon）](phases/PHASE_6.md#51-数字足迹清除)
   - [5.2 Active Directory 清理](phases/PHASE_6.md#52-active-directory-清理)
   - [5.3 物理清理清单](phases/PHASE_6.md#53-物理清理清单)
   - [5.4 日志清除决策树](phases/PHASE_6.md#54-日志清除决策树)
7. [第 6 节：TSCM：找出窃听器，也是为了安放窃听器](phases/PHASE_6.md#第-6-部分tscm发现窃听器以植入窃听器)
   - [6.1 监视设备的类型与特征信号](phases/PHASE_6.md#61-监控设备类型与特征)
   - [6.2 检测方法论：一步一步来](phases/PHASE_6.md#62-检测方法论分步指南)
   - [6.3 RF Explorer 实操演练](phases/PHASE_6.md#63-rf-explorer-实操演练)
   - [6.4 实验练习](phases/PHASE_6.md#64-实验练习搭建与检测)
   - [6.5 进攻性安放原则](phases/PHASE_6.md#65-攻击性植入原则)
8. [第 7 节：ADCS 攻击路径](phases/PHASE_6.md#第-7-部分adcs-攻击路径)
   - [7.1 ADCS 是什么，为何重要](phases/PHASE_6.md#71-adcs-是什么以及为何重要)
   - [7.2 ESC1：配置错误的证书模板](phases/PHASE_6.md#72-esc1配置错误的证书模板)
   - [7.3 ESC4：模板写权限滥用](phases/PHASE_6.md#73-certipy-完整工作流esc1--esc4--esc8)
   - [7.4 ESC8：将 NTLM 中继到 ADCS HTTP 端点](phases/PHASE_6.md#73-certipy-完整工作流esc1--esc4--esc8)
   - [7.5 Certipy 完整工作流](phases/PHASE_6.md#73-certipy-完整工作流esc1--esc4--esc8)
9. [第 8 节：完整作战场景：静默账本行动 v2](phases/PHASE_6.md#第-8-部分寂静账本行动-v2)
10. [阶段 6 资源参考](phases/PHASE_6.md#第-6-阶段资源参考)
11. [阶段 6 能力清单](phases/PHASE_6.md#第-6-阶段能力清单)

</details>

<div align="right"><a href="#table-of-contents">↑ 返回目录</a></div>

---

<a id="final-word"></a>
#### [结语：毕业项目与前沿路线图](field-guides/Final_Word.md)

<details>
<summary><strong>展开结语各节（毕业项目与验证）</strong></summary>

<br/>

1. [文档统计 - 2027 年核实](field-guides/Final_Word.md#文档统计2027-年核验)
2. [主课程与配套目录](field-guides/Final_Word.md#主课程与配套指南目录)
3. [路线图速览](field-guides/Final_Word.md#路线图一览)
4. [研究者署名索引](field-guides/Final_Word.md#构建本文档技术的那些研究者)
5. [本文件给不了你的东西](field-guides/Final_Word.md#本文档给不了你的东西)
6. [GREATEST 在实战中是什么样](field-guides/Final_Word.md#greatest-在实战中是什么样子)
7. [新兴前沿：v6.0 之外 / 研究视野（2027-2028）](field-guides/Final_Word.md#新兴前沿超越-v60--研究视野2027-2028)
8. [作者与版本](field-guides/Final_Word.md#结语)

</details>

<div align="right"><a href="#table-of-contents">↑ 返回目录</a></div>

---

## 执行摘要

网络安全行业充斥着流于表面的认证指南、选择题小抄和自动化工具教程，一旦撞上现代防御遥测，它们立刻失效。

**The BlackHAT Roadmap v1.2.2 · GREATEST 版** 建立在一条根本不同的原则上：**从硬件底层开始，彻底理解系统。**

本仓库包含 **44,900 多行** 经受过实战检验的技术文档、武器化代码架构、规避机制与作战安全信条，横跨 16 个主模块。它填补了「只会跑自动化一键工具」与「能像一线安全研究员、红队工程师或漏洞利用开发者那样作业」之间的鸿沟。

```
+-----------------------------------------------------------------------------+
| 仓库一览（v1.2.2 · 2027 版）                                                |
+-----------------------------------------------------------------------------+
| 总内容量             : 44,900+ 行高密度攻防工程内容                         |
| 文档总量             : 约 1.80 MB Markdown 源文件，横跨 16 个主模块         |
| 进阶深度             : 8 个核心阶段（阶段 -1 至阶段 6）                     |
| 章节数量             : 440+ 个主章节（H2）、1,120+ 个小节（H3）             |
| 代码实现             : 1,080+ 个已验证代码块，覆盖 13+ 种语言               |
| 攻击工具             : 收录 300+ 款独有攻击性工具                           |
| MITRE 对齐           : 200+ 项 ATT&CK 技术（Enterprise、ICS、ATLAS）        |
| 可编译实验           : 原生 C API 解析器与进攻性 Rust 内存加载开发          |
| 特种作战             : 物理红队、社会工程、无人机侦察、量子 / SNDL          |
+-----------------------------------------------------------------------------+
```

---

## 这个仓库为什么存在

大多数教学资源讲的是软件*理应*如何工作。而真正的进攻性安全，要求你理解软件在遭遇边界情况、错误假设和内存破坏时*实际*是如何工作的。

### 对比

| 维度 | 常规信息安全课程 | The BlackHAT Roadmap v1.2.2 |
| :--- | :--- | :--- |
| **核心目标** | 通过选择题考试（CEH、PenTest+） | 从零打造原创能力 |
| **工具路线** | 运行公开扫描器（Nmap、Metasploit、Nikto） | 自己编写植入体、加载器与 C2 代理 |
| **防御规避** | 基础的载荷编码与混淆 | Ekko/Foliage 休眠混淆、间接系统调用、栈伪造 |
| **Active Directory** | 基础口令喷洒与简单的 BloodHound 采集 | ADCS ESC1-15、认证强制、影子凭据、Entra ID PRT 窃取 |
| **二进制利用** | 在过时的 Linux 虚拟机里做经典栈溢出 | 现代 Windows 堆利用、ROP 链、V8 浏览器利用 |
| **特种作战** | 不涉及，或拆成独立领域 | 物理隐蔽潜入、无人机侦察、社会工程话术、量子 SNDL |
| **持久化与内核**| 计划任务与常规注册表 Run 键 | eBPF rootkit、COM 劫持、HVCI 绕过、hypervisor ring -1 |
| **作战安全**| “打开某个商业 VPN 服务” | 硬件剥离、Tails/Whonix 链路、Monero 循环、内存擦洗 |

---

## 主仓库架构

```text
The-BlackHAT-roadmap/
├── .github/                      <- 项目元数据、议题模板、PR 模板与进度追踪表
├── assets/
│   ├── README.md                 <- 视觉素材清单与 CC BY-SA 4.0 声明
│   ├── banner.svg                <- 赛博 HUD 风格 SVG 横幅（v1.2.2）
│   └── diagrams/                 <- 模块化 Mermaid 图表与高分辨率渲染图
├── black-bag/                    <- 隐蔽行动作业手法与生存载荷
│   ├── BlackHat_Long-Term_Survival_Tactics.md <- 3,000+ 行的作战安全与反监视主手册
│   └── Max_Anonymity_Workflow.md <- 匿名架构速查与 7 层验证蓝图
├── field-guides/                 <- 作战手册、战术矩阵与基础设施
│   ├── FAQ.md                    <- 职业现实与转型作战常见问题
│   ├── Final_Word.md             <- 验证统计、署名信息与 2027-2028 路线图
│   ├── Lab_Setup_Guide.md        <- 多层企业 AD 与虚拟机管理程序蓝图
│   ├── MITRE_ATT&CK_Quick_Reference.md <- Enterprise v15、ICS 与 ATLAS 战术矩阵
│   ├── Philosophy_The_BlackHat_Mindset.md <- 认知信条与原语思维模型
│   ├── Resources_Aggregated.md   <- 权威文献、白皮书与存档
│   └── Tools_Inventory.md        <- 300+ 款按阶段编排的进攻工具目录
├── payloads/                     <- 可编译的武器化源码实现
│   ├── README.md                 <- 载荷总索引、工具链与实验前置条件
│   ├── 01_dynamic_api_resolver/  <- C 语言实现的内存 PEB 遍历与 DJB2 导出表哈希
│   └── 02_offensive_rust_loader/ <- Rust 实现的内存 RW -> RX 状态翻转与二进制加固
├── phases/                       <- 严格按时间顺序排列的 8 个课程阶段
│   ├── PHASE_-1.md               <- 强化作战安全与匿名基础设施
│   ├── PHASE_0.md                <- 底层基础与系统内部机制
│   ├── PHASE_1.md                <- 现代 Web 与 API 攻击面
│   ├── PHASE_2.md                <- 网络跳板与 Active Directory 精通
│   ├── PHASE_3.md                <- 系统与内核漏洞利用
│   ├── PHASE_4.md                <- 专项操作员分支（4A-4I）
│   ├── PHASE_5.md                <- GREATEST（顶尖漏洞研究与 0-Day）
│   └── PHASE_6.md                <- 特种作战与对手模拟
├── CHANGELOG.md                  <- 版本历史与公开发布说明
├── CITATION.cff                  <- GitHub 原生引用元数据
├── LICENSE                       <- MIT 许可证（源代码与载荷）
├── LICENSE-DOCS                  <- CC BY-SA 4.0 许可证（课程与图表）
└── README.md                     <- 主课程中枢与导航起点
```

---

## 可编译的进攻性工程载荷

为了填平「理论理解」与「二进制执行」之间的鸿沟，仓库在 [payloads/](payloads/) 中提供了可直接编译的武器化代码库：

```
payloads/
|-- README.md                  # 载荷总索引、工具链与实验前置条件
|-- 01_dynamic_api_resolver/   # Windows PEB 遍历、C 语言实现的内存 API 导出表哈希（DJB2）
`-- 02_offensive_rust_loader/  # 内存保护属性翻转（RW -> RX）、Rust 实现的原生 API 封装
```

- **[载荷 01：C 语言动态 API 解析器](payloads/01_dynamic_api_resolver/)**：演示如何完全在内存中解析 Windows API 函数——遍历进程环境块（PEB）并对导出表字符串做哈希，从而击破对导入地址表（IAT）的静态分析。
- **[载荷 02：进攻性 Rust 内存加载器](payloads/02_offensive_rust_loader/)**：演示如何在内存中暂存加密的 shellcode，避免直接使用 RWX 分配标志，并在派发线程前一刻把内存权限翻转为可执行（`PAGE_EXECUTE_READ`）。

---

## 2025-2027 操作员模块

课程整合了击穿现代安全栈所需的最新进攻范式：

### 1. 现代 EDR 规避与休眠混淆
通过基于异步定时器的内存保护属性翻转，击破内存扫描器（Moneta、Hunt-Sleeping-Beacons、Pe-sieve）。
- **Ekko、Foliage 与 Cronos 实现：** 通过 `NtContinue`、`CreateTimerQueueTimer` 加密 ROP 链，并擦除栈帧。
- **调用栈伪造：** 合成栈帧（SilentMoonwalk、Unwinder），以通过返回地址校验。
- **间接系统调用：** 动态解析 SSN，并在合法的 `ntdll.dll` 内存空间内执行 syscall 指令，绕过用户态钩子。

### 2. 企业级 Active Directory 与混合身份
- **ADCS 利用：** 滥用企业证书颁发机构在 ESC1 至 ESC15 上的配置错误。
- **认证强制：** 通过 PetitPotam（MS-EFSR）、DFSCoerce（MS-DFSNM）与影子凭据强制发起 NTLM 认证。
- **Entra ID（Azure AD）：** 主刷新令牌（PRT）提取、条件访问绕过、设备代码钓鱼与 Azure Arc 横向移动。

### 3. 进攻性 Rust 工程
用高性能、静态编译的 Rust 取代传统的 C/C++ 加载器：
- 通过哈希化 PE 导出表实现动态 API 解析。
- 使用安全封装直接调用 Windows 原生 API。
- 在内存中执行 shellcode，不留下 RWX 分配的痕迹。

### 4. AI / ML 利用与自动化武器化
- 对集成 LLM 的企业应用发起利用：间接提示注入、检索增强生成（RAG）投毒与智能体越狱。
- 本地进攻性 LLM 流水线：用微调后的本地模型自动完成漏洞分诊、反编译分析与利用脚本生成。

### 5. 量子计算与 SNDL 威胁建模（阶段 6）
- **先存储、后解密（SNDL）：** 在密码分析相关量子计算机（CRQC）可用之前，提前囤积企业加密流量。
- **后量子密码学（PQC）降级：** 在迁移窗口期强制混合密钥交换协商回退到经典密码算法。

### 6. 隐蔽物理潜入与空中侦察（阶段 6）
- 非破坏性进入：弹子锁开锁、绕过工具、锁舌拨片与门底工具。
- 电子门禁：Wiegand 协议拦截、OSDP 审计与 RFID/NFC 证件卡克隆。
- 无人机侦察：光学巡逻路线测绘，以及暖通空调/机房热分布图分析。

---

## 实验架构与前置条件

要完成本课程中的实操练习，推荐的自建实验环境包括：

1. **虚拟化平台：** Proxmox VE、VMware ESXi 或 VMware Workstation Pro。
2. **Active Directory 靶场：** 两台 Windows Server 域控制器（2019/2022），已安装 Active Directory 证书服务（ADCS），外加 2-3 台已加域的 Windows 10/11 企业工作站。
3. **恶意软件分析沙箱：** 相互隔离的 FlareVM（Windows）与 REMnux（Linux）节点，使用不接路由的仅主机虚拟网卡。
4. **工具环境：** 一台专用的 Kali Linux 或 Debian 实例，装好 Docker、Rust 工具链、MinGW-w64、Clang/LLVM 与 Ghidra。
5. **硬件安全套件（阶段 4G 与阶段 6）：** RTL-SDR blog V4、HackRF One、SouthOrd/Sparrows 开锁工具套装、Proxmark3 RDV4 / Flipper Zero、Hak5 LAN Turtle 以及 CAN 总线收发模块。

---

## 主题标签

`roadmap` · `blackhat-roadmap` · `greatest-roadmap` · `penetration-testing-roadmap` · `cybersecurity-roadmap` · `AI-ML-Jailbreak` · `security` · `cybersecurity` · `reverse-engineering` · `security-tools` · `hacking` · `pentesting` · `osint` · `penetration-testing` · `network-security` · `ctf` · `infosec` · `malware` · `ethical-hacking` · `red-team` · `kali-linux` · `malware-analysis` · `active-directory` · `web-security` · `mitre-attack` · `bug-bounty`

---

## Star 历史曲线

如果这套课程对你的研究或职业有价值，欢迎给仓库点 Star，帮助更多研究者发现它：

<div align="center">

<a href="https://www.star-history.com/?type=date&repos=SagarBiswas-MultiHAT%2FThe-BlackHAT-roadmap">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/chart?repos=SagarBiswas-MultiHAT/The-BlackHAT-roadmap&type=date&theme=dark&legend=top-left" />
    <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/chart?repos=SagarBiswas-MultiHAT/The-BlackHAT-roadmap&type=date&legend=top-left" />
    <img alt="Star History Chart" src="https://api.star-history.com/chart?repos=SagarBiswas-MultiHAT/The-BlackHAT-roadmap&type=date&legend=top-left" />
  </picture>
</a>

</div>

---

## 参与贡献

欢迎能抬高技术门槛的贡献。无论是一个新载荷、一个写得更深的模块，还是修掉一个失效链接，来自社区的真实贡献都让这套课程更强。

- **如何开始：** 先看[贡献指南](.github/CONTRIBUTING.md)，再找带 [`good first issue`](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap/labels/good%20first%20issue) 标签的议题，作为容易上手的切入点。
- **质量门槛：** 只加通用工具清单或入门材料的 PR 不予合并。我们优先看深度，而不是广度。
- **代码标准：** 代码示例必须可用、附带技术原理说明，并且是针对现代工具链编译通过的。请看[武器化载荷](payloads/)目录。
- **格式规则：** 严格遵守干净的 markdown 规范。正文与文档中任何位置都不得出现长破折号（em-dash）。

---

## 引用与学术署名

如果你在学术研究、技术白皮书或机构课程中使用了本课程、其中的进攻性工程架构或实验实现，请按如下方式引用本作品：

```bibtex
@misc{biswas2026blackhat,
  author       = {Sagar Biswas},
  title        = {The BlackHAT Roadmap: From 0 to GREATEST (v1.2.2)},
  year         = {2026},
  publisher    = {GitHub},
  journal      = {GitHub repository},
  howpublished = {\url{https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap}}
}
```

也可以通过 GitHub 的“Cite this repository”界面引用仓库自带的 [CITATION.cff](CITATION.cff) 文件。

---

## 法律免责声明

> [!CAUTION]
> **仅限获得授权的教学、研究与防御用途。**
> 
> 本仓库提供的材料、方法论、代码片段与作战指引，仅面向获得明确、正式书面授权的网络安全专业人员、渗透测试人员、红队工程师与学术研究者。
> 
> 未经明确许可而对网络、服务器或终端进行测试、访问或利用，依据当地、本国及国际法律（包括美国《计算机欺诈与滥用法》、英国《计算机滥用法》及同等法规）均属违法。
> 
> 作者不承担任何责任，也不对因应用本文所含信息而导致的任何滥用、损害或法律后果负责。请负责任地学习。范围界定与漏洞报告请参见 [SECURITY.md](.github/SECURITY.md)。

---

## 许可证与署名

本仓库采用双许可证，以同时保护文字课程与可执行实验代码：

1. **课程、文档与架构图（`*.md`、Volume I、Volume II、Trackers）：**
   依据 [知识共享 署名-相同方式共享 4.0 国际许可证（CC BY-SA 4.0）](https://creativecommons.org/licenses/by-sa/4.0/) 授权（见 [`LICENSE-DOCS`](LICENSE-DOCS)）。
   你可以出于任何目的自由共享与改编本材料，但必须适当署名 **Sagar Biswas（@SagarBiswas-MultiHAT）**、附上指向本原始仓库的直接链接，并以相同的 CC BY-SA 4.0 许可证分发任何演绎作品。

2. **源代码、实验与载荷（`payloads/` 目录，C、C++、Rust、汇编、Python 脚本）：**
   依据 [MIT 许可证](LICENSE) 授权。

删除作者署名、剥离许可证文件，或把本仓库当作自己的作品重新上传，均直接违反著作权法，将招致正式的 GitHub DMCA 下架请求。

---

## 作者与联系方式

**Sagar Biswas**
- **GitHub 账号：** [@SagarBiswas-MultiHAT](https://github.com/SagarBiswas-MultiHAT)
- **机构：** [MultiHAT Dev](https://multihat.dev/)
- **项目：** [作品集与工程项目](https://sagarbiswas-multihat.github.io/projects/)
- **笔记：** [技术研究笔记](https://sagarbiswas-multihat.github.io/notebooks/)
- **文章与博客：** [安全分析与实战复盘](https://sagarbiswas-multihat.github.io/blogs/)

### 相关路线图与精选生态

- [**渗透测试路线图**](https://github.com/SagarBiswas-MultiHAT/penetration-testing-roadmap)：面向真实进攻性评估的实操流程、方法论与工具链。
- [**Awesome Cybersecurity Paths**](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-paths)：覆盖防御、进攻与研究专项的结构化学习路径。
- [**Awesome Cybersecurity Books**](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-books)：面向安全研究者与从业者的必备基础与进阶文献。

---

<div align="right">

*为那些要求从硅片底层开始彻底掌握的人而写。*  
*以纪律维护。没有注水，没有捷径，不作退让。*

</div>

---
