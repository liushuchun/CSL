# A Dataset of Chinese Scientific Literature

**中文科学文献数据集(CSL)**

数据集目前包含 140k 条计算机相关学术论文的标题及摘要信息，更多学术领域的摘要信息正在整理中。

## Files

```
---------------------------------
abstract_cs.zip |  140K texts |
---------------------------------
csl_public.zip  |  26K texts  |
---------------------------------
TOTAL           |  166K texts |
---------------------------------
```

<a href="#download">Download</a> 

### abstract_cs

字段：
+ title -- 论文标题
+ content -- 论文摘要

```
数据量：140183
示例：
{
	{
		"index": 48
		"title": "自组网中基于自适应波束天线的拓扑控制算法",
		"content": "定向天线自组网拓扑的构建问题比全向天线网络复杂.基于自适应波束定向天线模型提出一种分布式拓扑控制算法,通过调整节点发射功率,改变天线波束的朝向、宽度和增益来构建拓扑.网络中每个节点收集其邻居节点信息,采用功率控制调度策略选择最优相邻节点,并选取覆盖所有最优相邻节点的最小发射功率为此节点的发射功率.算法在保证网络连通性与无向性的同时,降低了节点的发射功率,减小了节点的平均度数,从而降低节点能耗,减少了节点间干扰,提高了网络吞吐量.仿真结果表明,算法显著提高了网络性能."
	},
	{
		"index": 82980
		"title": "基于前馈模糊逻辑的微波功率控制设计与分析",
		"content": "描述和设计了一类生产陶瓷载体的大型微波干燥控制系统;针对微波干燥过程中微波功率控制不准确、产品缺陷率高的问题,分析了过程变量与控制变量之间的关系特点,并在现有算法基础上,设计了一种基于前馈模糊逻辑的微波功率控制模型;最后对此控制模型设计算法,并应用于实际进行实验分析,得出了很好的效果。"
	},
	{
		"index": 123919
		"title": "基于主模型的协同设计软件架构技术研究",
		"content": "运载火箭总体方案论证过程中,由于涉及专业多、专业间迭代交互频繁、设计方案多变等特点,容易造成多专业协同设计时版本与技术状态的不统一,需要研究针对运载火箭产品的通用建模方法,并开发相应的软件系统;基于统一数据源的协同设计理念,结合运载火箭总体设计与数据模型特点,通过定义基础信息模型、概念模型、参数模型、外部定义模型4种数据模型,提出了针对运载火箭产品的通用主模型构建方法;将此通用建模方法软件化,搭建了基于主模型的协同设计软件系统整体架构;此架构包含主模型管理系统、主模型建模工具及应用客户端三部分,实现了多专业协同设计过程中数据与版本的统一管理、技术状态一致性分析、谱系追踪、数据展示与应用等功能;该主模型建模工具与客户端软件系统的实现,为运载火箭的总体协同设计提供了工具支撑。"
	},
}

```
### csl_public

取自中文论文摘要及其关键词，论文选自部分中文社会科学和自然科学核心期刊。使用tf-idf生成伪造关键词与论文真实关键词混合，构造摘要-关键词对，机器学习模型的任务目标是根据摘要判断关键词是否全部为真实关键词。

数据量：训练集(20,000)，验证集(3,000)，测试集(3,000)
每一条数据有四个属性，从前往后分别是 数据ID，论文摘要，关键词，真假标签。
示例：
```
    {"id": 1, "abst": "为解决传统均匀FFT波束形成算法引起的3维声呐成像分辨率降低的问题,该文提出分区域FFT波束形成算法.远场条件下,以保证成像分辨率为约束条件,以划分数量最少为目标,采用遗传算法作为优化手段将成像区域划分为多个区域.在每个区域内选取一个波束方向,获得每一个接收阵元收到该方向回波时的解调输出,以此为原始数据在该区域内进行传统均匀FFT波束形成.对FFT计算过程进行优化,降低新算法的计算量,使其满足3维成像声呐实时性的要求.仿真与实验结果表明,采用分区域FFT波束形成算法的成像分辨率较传统均匀FFT波束形成算法有显著提高,且满足实时性要求.", "keyword": ["水声学", "FFT", "波束形成", "3维成像声呐"], "label": "1"}
    
    
```

## Example

### abstract_cs
**使用 [seq2seq 模型](https://spaces.ac.cn/archives/6933) 生成标题效果如下：**

**论文摘要**：首先介绍了激光增材制造中残余应力的产生和危害,指出高的温度梯度和不均匀相变是高残余应力的原因,列举了残余应力造成的热裂纹、翘曲和疲劳失效等危害。然后,从残余应力的试验测定、数值模拟以及调控消减三个方面总结了相关研究现状。残余应力试验测定部分包括表面和内部残余应力的测试,方法有X射线衍射法、中子衍射法和压痕法等。数值模拟部分主要评述了工艺参数和扫描策略对应力场的影响。残余应力调控指的是在成形过程中,通过工艺控制减少应力的产生,主要介绍了采用热处理、超声冲击降低已成形构件残余应力的相关研究。最后提出应开展微观残余应力到大型构件宏观残余应力的多尺度表征,表面残余应力和内部残余应力相结合的多手段定量测定等专题研究,为开展残余应力与工件失效的关联性研究打下基础。

**原标题**：激光增材制造残余应力研究现状  
**生成标题**：激光增材制造中残余应力试验研究现状  

------

**论文摘要**：传统的压缩跟踪算法使用不考虑目标位移的搜素机制和固定大小的跟踪窗口跟踪目标,且每帧更新分类器,容易造成目标的漂移和丢失.该文提出了结合目标估计的自适应压缩跟踪算法,该算法采用ORB算法将先前帧和当前帧的目标区域进行特征点匹配,通过建立关系模型实现候选目标的估计定位,从而解决了搜索区域受目标运动速度影响的问题;其次,提出了基于匹配点间方差的尺度自适应方法,实现了跟踪窗口的自适应变化;最后,引入遮挡判断因子,并结合匹配点的数量调整分类器的更新策略,实现抗遮挡的处理.实验结果表明:该算法具有较高的重叠率和成功率,对目标跟踪中的相机晃动、快速运动、尺度变化、遮挡等因素具有较强的抗干扰能力,且在多个测试视频上平均帧率为32帧/s,能满足实时性的要求,较好的解决了传统压缩跟踪算法的缺陷.

**原标题**：结合目标估计的自适应压缩跟踪  
**生成标题**：结合自适应压缩跟踪算法的目标跟踪  

------

**论文摘要**：决策粗糙集理论中,三种单调性的代价目标函数被用来评价三支决策的风险.然而,在实际应用中,其中的延迟代价目标函数经常存在着非单调现象.针对这种现象,本研究首先提出了一种基于三支决策代价目标函数间逻辑关系的阈值计算方法.然后,提出了双量化延迟代价目标函数的策略,并且分别讨论了相应的三支决策阈值推导,重点阐述了延迟代价双量化的乐观视角和悲观视角.最后,通过一组典型的实例证明了上述代价双量化三支决策的设计和推理的可行性.

**原标题**：延迟代价双量化三支决策  
**生成标题**：延迟代价双量化三支决策的阈值推理  

### csl_public

**CSL 关键词识别  Keyword Recognition (Accuracy)：**

|         模型          | 开发集（dev) | 测试集（test) |              训练参数              |
| :-------------------: | :----------: | :-----------: | :--------------------------------: |
|     ALBERT-xlarge     |    80.23     |     80.29     | batch_size=16, length=128, epoch=2, lr=5e-6  |
|     ALBERT-tiny       |    74.36     |     74.56     | batch_size=4, length=256, epoch=5, lr=1e-5 |
|       BERT-base       |    79.63     |     80.23     | batch_size=4, length=256, epoch=5, lr=1e-5 |
|   BERT-wwm-ext-base   |    80.60     |     81.00     | batch_size=4, length=256, epoch=5, lr=1e-5 |
|      ERNIE-base       |    79.43     |     79.10     | batch_size=4, length=256, epoch=5, lr=1e-5 |
|     RoBERTa-large     |    81.87     |     81.36     | batch_size=4, length=256, epoch=5, lr=5e-6 |
|       XLNet-mid       |    82.06     |     81.26     | batch_size=4, length=256, epoch=3, lr=1e-5 |
|    RoBERTa-wwm-ext    |    80.67     |     80.63     | batch_size=4, length=256, epoch=5, lr=1e-5 |
| RoBERTa-wwm-large-ext |    82.17     |     82.13     | batch_size=4, length=256, epoch=5, lr=1e-5 |

详细评测可见 [CLUE benchmark](https://github.com/CLUEbenchmark/CLUE)

## Download

+ 计算机科学领域 140K (abstract_cs.zip) [百度网盘](https://pan.baidu.com/s/1nYM1rMHLNW0o7gGwV_dEiA)  (提取码: s967)
+ CSL 关键词识别任务 26k (csl_public.zip)    [Google](https://storage.googleapis.com/cluebenchmark/tasks/csl_public.zip) | [百度网盘](https://pan.baidu.com/s/1SuKGTRD3ZwFihn7q0uNgsA) (提取码: sxm5)

## Reference

[1] 苏剑林. (2018, Sep 01). 《玩转Keras之seq2seq自动生成标题 》[Blog post]. Retrieved from https://spaces.ac.cn/archives/5861

[2] bert4keras https://github.com/bojone/bert4keras
## License

本数据集仅供个人研究学习使用，如需其它用途请[联系作者](mailto:liyudong123@hotmai.com)