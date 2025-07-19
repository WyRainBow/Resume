# 韦宇

<img alt="avatar" src="yuawei.jpg">

> <span alt="icon">&#xe60f;</span> `18933549212`&emsp;&emsp; <span alt="icon">&#xe7ca;</span> `3658043236@qq.com`&emsp;&emsp; 年龄: 22岁&emsp;&emsp; **求职意向:** **后端开发**

## 教育经历

<div alt="entry-title">
    <h3>广东药科大学　　　　　　　　计算机科学与技术　　　　　　　　本科　　　　　2022.9-2026.6</h3>
</div>
## 工作经验

<table style="width: 100%; border: none; margin-bottom: 2mm;">
<tr style="border: none;">
<td style="border: none; padding: 0; font-weight: bold; font-size: 11pt; color: #2c5aa0;">腾讯云 - 后端开发实习生　　　　　　　　　　　　　　　　　　　　　　　　　　</td>
<td style="border: none; padding: 0; text-align: right; font-weight: normal; font-size: 11pt; color: #353a42;">2025.6-至今</td>
</tr>
</table>
<div>
<p><i><b>实习描述:</b> 负责腾讯云域名注册业务的开发，包括像域名的注册、敏感词过滤、续费、用户身份模版认证、域名生命周期的状态管理等。</i></p>
<p><b>主要工作成果:</b></p>
<ul>
    <li><b>风险SQL治理:</b> 负责域名注册业务中 SQL 性能优化工作，针对扫描超百万行的高风险 SQL，采用解决索引失效、强制索引、游标分页、代码层解耦、UNION 优化等多种手段进行优化，累计优化 60 余条 SQL，成功将50条+SQL的扫描行数降至 10 万以下，执行时间提升 80%。</li>
    <li><b>敏感词过滤性能优化:</b> 负责域名搜索敏感词过滤功能性能优化，针对现有AC自动机算法在处理批量关键词时性能瓶颈问题，优化敏感词检查逻辑，实现三级过滤机制（最高敏感词、合规敏感词、域名敏感词）的短路检查，采用Go协程并发处理机制，将原有的串行敏感词检查改为并行执行，通过sync.WaitGroup和sync.Mutex保证线程安全，将批量关键词检查性能提升60%+，系统响应时间从800ms优化至200ms以内。</li>
</ul>
</div>

<table style="width: 100%; border: none;">
<tr style="border: none;">
<td style="border: none; padding: 0; font-weight: bold; font-size: 11pt; color: #2c5aa0;">美的集团 - 后端开发实习生</td>
<td style="border: none; padding: 0; text-align: right; font-weight: normal; font-size: 11pt; color: #353a42;">2024.12-2025.4</td>
</tr>
</table>
<div>
<p><i><b>实习描述:</b> 参与开发数据供应链部门APS系统(高级计划与排程系统)，与美的集团iPass(集成化生产管理平台)、以及 MES(制造执行系统)深度集成，实现供应链计划→生产排程→车间执行全链路数据协同。</i></p>
<p><b>工作职责:</b></p>
<ul>
    <li>主要参与项目核心链路开发、负责如工单下达、工艺路线管理、车间排产全链路模块开发、完成核心代码编写工作。</li>
    <li>协助推进接口性能优化工作，参与技术方案评审并针对线程安全问题提出优化建议。</li>
</ul>
<p><b>主要工作成果:</b></p>
<ul>
    <li><b>多线程异步任务开发:</b> 基于 CompletableFuture结合分页机制(PageSize=1000)实现数据拉取的并发处理，实现了单批次1200条数据平均处理时间从7s优化至1.8秒。</li>
    <li><b>优化慢SQL:</b> 通过慢查询日志和 EXPLAIN 分析，针对生产计划的执行依赖于任务的优先级排序，建立时间和任务优先级的联合索引，消除了file sort的影响，解决了需要频繁进行SQL查询的性能问题，查询时间从秒级优化到毫秒级。</li>
</ul>
</div>

## 项目经历

<div alt="entry-title">
    <h3>AsyncScheduler (多阶段异步调度框架)</h3>
</div>
<div>
<p><b>项目背景:</b> 学校实验室的医学AI训练场景需要对收集到的图像进行数据采集、清洗、特征提取、分布式存储等多个步骤。 为了提高开发效率，我抽象为多个异步任务并开发了一个基于Java的多阶段异步任务框架。</p>
<p><b>个人职责:</b></p>
<ul>
    <li><b>负责架构设计:</b> 采用生产者-消费者模式。整体框架分为Flow Server(服务层)和 Worker(执行层)。Flow Server层通过web接口 向外部提供主要服务，包括查询任务、创建任务、占据任务等。Worker层提供HTTP服务。主要接口有创建任务、拉取任务、轮询任务状态等。Worker层负责消费任务。</li>
    <li><b>数据库表设计:</b> 设计主要的三张数据库表:任务信息表、配置表、位置表。方便任务快速注册和进行任务管理，实现低耦合。</li>
    <li><b>任务调度设计:</b> 支持按相对优先级来调度任务。综合创建时间、更新时间、重试间隔(采用渐进式间隔重试策略)进行相对优先级排序。</li>
    <li><b>服务治理设计:</b> 服务治理通过轮询的方式来发现超时任务并重置其状态，支持通过轮询的方式来判断是否达到分表的阈值并实现分表逻辑。</li>
    <li><b>架构优化设计:</b> 多机竞争由Mysql行级锁优化为Redis分布式锁，下阶段考虑引入MQ，将任务拉取和执行解耦交给MQ。</li>
</ul>
<p><b>技术难点:</b></p>
<ul>
    <li><b>任务排序规则设置:</b> 框架抽象出了一个 order_time 排序字段来对任务进行排序，受到任务创建时间(基础排序)、任务修改时间、任务优先级、任务失败次数的影响。实现逻辑统一并解决了排序规则和多个字段耦合的问题。</li>
    <li><b>分表方案设计:</b> 实现基于记录数量进行分表的方案:任务治理服务会定时检查任务中的记录数量，超过阈值之后触发分表。此时新的任务创建中新表中，但是仍然从旧表中调度任务、直到旧表任务调度完成。</li>
    <li><b>多机竞争方案及优化问题:</b> 多个Worker去拉取任务容易拉到同一批任务。一开始这里在Worker侧引入Redis分布式锁来解决，任务冲突率解决90%，但Worker拉取和执行任务偶尔可能会CPU飙高至80%左右的问题。考虑引入MQ进行水平扩展效果。</li>
</ul>
</div>

## 专业技能
- **Java基础:** 熟悉Java编程语言，有两年使用经验，掌握集合框架、异常、多线程、反射等核心机制。
- **Golang基础:** 熟悉Golang语言，有一年使用经验，掌握Map、Channel、Select实现原理，熟悉Gin、GORM组件。
- **JVM:** 熟悉JVM，掌握内存结构，垃圾回收机制，类加载机制，GC算法等，了解过JVM调优方法。
- **MySQL:** 熟悉MySQL基础原理、存储引擎、索引原理、MVCC、事务等机制、具备一定的SQL性能调优能力。
- **Redis:** 熟悉Redis底层数据结构、分布式锁、线程模型、内存淘汰策略等机制，熟悉缓存击穿、穿透、雪崩概念。
- **计算机网络:** 熟悉TCP、UDP、HTTP、HTTPS等网络协议，掌握TCP三次握手、四次挥手、流量控制等机制。
- **操作系统:** 熟悉进程、线程、虚拟内存、I/O多路复用等，掌握进程间通信和多线程同步技术。
- **AI:** 了解AI Agent、RAG、FunctionCall、LLM(如阿里百炼、DeepSeek)Promot管理和编排的基本概念及原理。
- **AI Conding工具:** 熟练运用如Cursor、通义灵码、ChatGPT、Claude等AI开发大模型工具。