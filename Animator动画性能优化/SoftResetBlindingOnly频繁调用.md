# SoftResetBlindingOnly频繁调用

## 问题

上马之后频繁触发SoftResetBlindingOnly

![1719815023922](image/SoftResetBlindingOnly频繁调用/1719815023922.png)

## 原因：

![1719815047379](image/SoftResetBlindingOnly频繁调用/1719815047379.png)

对于AnimatorControllerPlayable加了后处理ik的ScriptPlayable后，没有将标记置为false的地方，导致进出state的时候，会频繁触发
