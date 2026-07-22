---
标签: [硬件设计, 方案家族, QDD, 准直驱, backdrivability, TESOLLO]
状态: 占位（从路线1-关节内置驱动.md拆分出来，内容已迁移，尚待按议题清单补充齿槽力矩等细节）
更新日期: 2026-07-22
关联文档:
  - 路线1-关节内置驱动.md
  - 00-技术路线地图.md
  - ../../05-术语词汇表/术语词汇表.md
---

# 方案家族：QDD 极低比 —— "力控透明党"

> 本文档从 [路线1：关节内置驱动](路线1-关节内置驱动.md) 拆分出来，是关节内置驱动路线里"减速比谱线"上极低比这一个点的独立深挖页。目前内容是从路线1原有段落迁移过来的，尚未按更细的议题清单展开，先占位。

## 一句话结论

代表：**TESOLLO DG-5F**。QDD 用大直径薄饼型电机 + 低减速比（约 5–20:1），电机仍在关节处，但省掉了高比例减速齿轮，直接获得好的 backdrivability 和力控透明度，代价是电机较重、成本高、体积大。

## 原理：为什么"直驱"能解决关节内置的核心问题

高减速比方案（[路线1：关节内置驱动](路线1-关节内置驱动.md)里的行星中等比/谐波极高比家族）的根本问题是，减速比 N≈300 时反向效率极低，外力很难传回电机轴，力矩估算误差高达 20–50%。QDD 把减速比降到 N≈5–20，外力几乎原封不动地传到电机轴，电机电流直接反映关节力矩，估算误差降到 5–15%。这种能力叫**本体感觉力控（proprioceptive force sensing）**——不需要外置力传感器，就能通过电机电流知道关节受到多大的力。MIT Cheetah 团队把这个概念推广到主流认知。

## 哪些任务非 backdrivability 不可

1. **碰撞吸收与安全性**：高减速比关节遇到硬性碰撞时，动能被结构件吸收；准直驱关节等效刚度低一到两个量级，碰撞更安全。实际排名：腱绳 ≈ 准直驱 > 关节内置高减速。
2. **接触丰富的装配任务**：拧螺丝、press-fit 插件等任务本质是阻抗控制（沿某方向施加精确力矩，同时沿其他方向顺从跟随约束），高减速比系统的力感知太差，这类控制器要么不稳定，要么需要昂贵的外置六维力传感器。
3. **物理演示学习**：人类手把手教机器人时，关节需要能被轻松拖动，高减速比关节的静摩擦相当于每个关节加了个"楔子"，示范动作会因此变形。

## 代表产品参数

TESOLLO DG-5F-S 为 20 DOF，机长约 21cm（掌到指尖），重量约 880g，最大负载 12kg，直接驱动配合 500Hz 控制频率，标称特点是消除齿隙、高定位精度，同时保留反驱关节以吸收外部冲击。每根手指 4 个独立驱动关节。【规格随型号有版本差异，建议以厂商最新资料为准】

## 参考来源

- [Tesollo unveils compact and lightweight humanoid robotic hand](https://roboticsandautomationnews.com/2026/01/28/tesollo-unveils-compact-and-lightweight-humanoid-hand/98315/)
- [Tesollo DG-5F-S Humanoid Robotic Hands: 20 DoF, Backdrivable Joints & 12kg Grip](https://www.geeky-gadgets.com/tesollo-dg-5f-s-robotic-hand/)
- [TESOLLO uses own actuator in DG-5F-S humanoid robotic hand - The Robot Report](https://www.therobotreport.com/tesollo-uses-own-actuator-dg-5f-s-humanoid-robotic-hand/)

## 待补充

- TESOLLO DG-5F 具体重量、DOF、控制频率等参数存在版本差异，建议核实厂商最新发布的规格表。【待核实】
- 齿槽力矩（cogging torque）对 QDD 低速/近静态操作的具体影响：QDD 电机常年运行在低速/近静态区间，齿槽力矩相对惯性和负载力矩的占比比高速运行时更明显，具体量级和应对方式（如力矩前馈补偿）尚未展开。【待补充】
- 是否有除 TESOLLO 之外的准直驱灵巧手代表案例（如学术界的原型），本文尚未覆盖。【待补充】
