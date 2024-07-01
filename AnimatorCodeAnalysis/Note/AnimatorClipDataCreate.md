# Animator的Clip数据缓存

## ClipMuscleConstant

Script：clipmuscle.cpp

功能：用于存储runtime时候的Clip的数据，从序列化数据加载到内存对象中

### 流程

#### * 构建MecanimClipBuilder clipBuilder

![1719820803626](image/AnimatorClipDataCreate/1719820803626.png)

一般在动画的导入的时候，或者load的时候会去调用

![1719820842842](image/AnimatorClipDataCreate/1719820842842.png)

构建MecanimClipBuilder clipBuilder，

遍历m_FloatCurves、m_PositionCurves、m_QuaternionCurves、m_EulerCurves、m_ScaleCurves，存到MecanimClipBuilder中，

并且![1719825634730](image/AnimatorClipDataCreate/1719825634730.png)，按照3种类型的curve进行缓存。

**并且每一个curve构建一个GenericBinding**。

所以是![1719827246717](image/AnimatorClipDataCreate/1719827246717.png)大类，

每个都会细分![1719827283154](image/AnimatorClipDataCreate/1719827283154.png)

#### * 构建ClipMuscleConstant

![1719827542063](image/AnimatorClipDataCreate/1719827542063.png)

将所有的gengericbinding存到outClipBindings。

然后在allocator上创建一个clip，在将

![1719847564343](image/AnimatorClipDataCreate/1719847564343.png)

只有steamed clip 创建一个临时的builder
