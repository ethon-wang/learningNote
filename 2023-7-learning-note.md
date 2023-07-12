- [任务1.学习Apex,Trigger,以及对象字段的简单使用](#任务1学习apextrigger以及对象字段的简单使用)
  - [Trigger](#trigger)
- [任务2.学习Visualforce 页面的开发,能够做出与后台交互的Visualforce页面](#任务2学习visualforce-页面的开发能够做出与后台交互的visualforce页面)
  - [apex:pageBlockButtons 样式调整,修改前：](#apexpageblockbuttons-样式调整修改前)
  - [修改后](#修改后)
    - [代码](#代码)
  - [官网解释：](#官网解释)
- [任务3.学习Salesforce内的一些配置功能,如Flow、验证规则、重复\&匹配规则、审批流的配置等](#任务3学习salesforce内的一些配置功能如flow验证规则重复匹配规则审批流的配置等)
  - [三种常规类型的流(Flow)](#三种常规类型的流flow)
  - [三种类型的触发器(Trigger)](#三种类型的触发器trigger)
- [任务4.学习Apex中的主要异步操作 1.定时作业（Scheduled Job）、2.批处理(Batch)、3.异步方法(Future) 等](#任务4学习apex中的主要异步操作-1定时作业scheduled-job2批处理batch3异步方法future-等)
  - [1.ScheduledApex](#1scheduledapex)
  - [2.实现批处理类步骤明确，只需要执行以下的步骤：](#2实现批处理类步骤明确只需要执行以下的步骤)
  - [3.Future方法用于异步处理，常用于Web service callout操作.](#3future方法用于异步处理常用于web-service-callout操作)
    - [QA](#qa)
      - [什么是 Batch？Batch 能用来处理什么问题？](#什么是-batchbatch-能用来处理什么问题)
      - [为什么处理大批量数据就要用 Batch？](#为什么处理大批量数据就要用-batch)
      - [如何启用 Batch？如何设置批次？](#如何启用-batch如何设置批次)
      - [Batch 分哪几个模块？分别实现什么功能？](#batch-分哪几个模块分别实现什么功能)
      - [Database.query() 最多只能查询 50000 条数据，如果我要处理的数据超出 50000 条怎么办？](#databasequery-最多只能查询-50000-条数据如果我要处理的数据超出-50000-条怎么办)
- [任务5.学会日志打印,根据日志排查与问题](#任务5学会日志打印根据日志排查与问题)

# 任务1.学习Apex,Trigger,以及对象字段的简单使用
##  Trigger
 > 可以在事件发生之前或之后对Salesforce中的记录（例如插入，更新或删除）执行自定义操作。就像数据库系统支持触发器一样，Apex也提供触发器支持来管理记录。

1.before被用于更新或验证记录值之前，将其保存到数据库之前

2.after用于访问系统设置的字段值，并影响其他记录中的更改。触发after触发器的记录是只读的
# 任务2.学习Visualforce 页面的开发,能够做出与后台交互的Visualforce页面
## apex:pageBlockButtons 样式调整,修改前：
![image](https://img2023.cnblogs.com/blog/1963362/202307/1963362-20230710102956569-1139849077.png)
## 修改后
![image](https://img2023.cnblogs.com/blog/1963362/202307/1963362-20230710103017554-2042442221.png)
### 代码
```xml
<apex:pageBlockButtons location="bottom">
```
## 官网解释：
> location	String	The area of the page block where the buttons should be rendered. Possible values include "top", "bottom", or "both". If not specified, this value defaults to "both".
应呈现按钮的页面块区域。可能的值包括“顶部”、“底部”或“两者”。如果未指定，则此值默认为“两者”。
Note: If a pageBlock header facet is defined, the facet overrides the buttons that would normally appear at the top of the page block. Likewise, if a pageBlock footer facet is defined, the facet overrides the buttons that would normally appear at the bottom of the page block.
注： 如果定义了页面块标题分面，则该分面将覆盖通常显示在页面块顶部的按钮。同样，如果定义了 pageBlock 页脚分面，则该分面将覆盖通常显示在页块底部的按钮。

# 任务3.学习Salesforce内的一些配置功能,如Flow、验证规则、重复&匹配规则、审批流的配置等
## 三种常规类型的流(Flow)
| Flow Type         | Launched By                     | Description                                                                                                            |
|-------------------|---------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Screen Flow       | Quick action                    | Screen Flows provide a UI that guides users through a business process\.                                               |
|                   | Lightning page                  | 屏幕流提供指导用户完成业务流程的 UI。                                                                                                   |
|                   | Experience Cloud site, and more |                                                                                                                        |
|                   |                                 |                                                                                                                        |
| Autolaunched Flow | Another flow                    | Autolaunched Flows automate business processes that have no UI\. They have no trigger and they run in the background\. |
|                   | Apex code                       | 自动启动的流程可自动执行没有 UI 的业务流程。它们没有触发器，在后台运行。                                                                                 |
|                   | REST API                        |                                                                                                                        |
|                   |                                 |                                                                                                                        |
| Triggered Flow    | Time                            | Triggered Flows are autolaunched by a trigger you specify\. They run in the background\.                               |
|                   | Data change                     | 触发的流由您指定的触发器自动启动。它们在后台运行。                                                                                              |
|                   | Platform event                  |

## 三种类型的触发器(Trigger)
| Trigger Type   | When It Runs                                         | How To Use It                              |
|----------------|------------------------------------------------------|--------------------------------------------|
| Schedule       | At A Time And Frequency You Specify                  | Running Nightly Batch Jobs                 |
| Platform Event | When A Particular Platform Event Message Is Received | Subscribing To Events                      |
| Record         | When A Record Is Created, Updated, Or Deleted        | Updating Records And Sending Notifications |

official reference：
> https://trailhead.salesforce.com/zh-CN/content/learn/modules/record-triggered-flows/get-started-with-triggered-flows?trailmix_creator_id=strailhead&trailmix_slug=wt23-automate-with-flow

# 任务4.学习Apex中的主要异步操作 1.定时作业（Scheduled Job）、2.批处理(Batch)、3.异步方法(Future) 等
##   1.ScheduledApex
通过以下步骤即可完成操作：

　　1.实现Schedulable接口，并重写execute方法，此方法体内实现需要定时执行的操作;

　　2.使用System.schedule()方法实现定时任务的调用。

　　Schedulable接口代码举例如下：
```java
public class GoodsSchedule implements Schedulable {
    //execute方法内为需要执行的定时任务
    public void execute(SchedulableContext sc) {
        String queryString = 'select Id,GOODSNAME__c from GOODS__c';
        SimpleBatchUtil batchUtil = new SimpleBatchUtil(queryString);
        Database.executeBatch(batchUtil);
    }
}
```

##   2.实现批处理类步骤明确，只需要执行以下的步骤：

1.实现Database.Batchable接口;

2.实现start()方法，此方法中通常写查询语句，并将数据通过Database.getQueryLocator(queryString)方法将数据传递到execute()形参中。此方法定义：

```java
global (Database.QueryLocator | Iterable<sObject>) start(Database.BatchableContext bc) {} ;
```

3.实现execute()方法，此方法对数据进行DML操作。此方法定义：
```java
global void execute(Database.BatchableContext BC, list<P>){} ;
```
4.实现finish方法(),此方法进行后期处理，如果无需要处理，可以不进行处理。
  
##   3.Future方法用于异步处理，常用于Web service callout操作.
###  QA
#### 什么是 Batch？Batch 能用来处理什么问题？

答：Batch 即批处理，用来处理大批量数据。

#### 为什么处理大批量数据就要用 Batch？

答：
1. 因为 Salesforce 对每个事务有 SQL 的 DML 限制，CPU Time Out，内存超限等限制，直接处理大批量数据会导致超限。
2. Batch 分批次处理时，每个批次是不同的事务，单独计算 DML 数量等，所以可以很大程度上避免超限。

#### 如何启用 Batch？如何设置批次？

```java
Database.executeBatch(new TestBatch());// 不设置批次数量时，默认按每批次 200 条记录执行
Database.executeBatch(new TestBatch(), 3000);// 设置每批次执行 3000 条记录，但实际上每批次只会执行 2000 条，因为批次最多只能设为 2000，超过 2000 按 2000 计算
```

#### Batch 分哪几个模块？分别实现什么功能？

1. start：用来查询要处理的数据总数（只执行一次）
2. execute：批处理核心方法，执行主体逻辑（执行多次）
3. finish：批处理全部运行完后执行的方法，一般用来把 Batch 错误信息发送邮件给指定用户，如把 Batch 中的错误信息发送给管理员，或把 Batch 执行完毕的消息发动给当前用户（只执行一次）

#### Database.query() 最多只能查询 50000 条数据，如果我要处理的数据超出 50000 条怎么办？

可以使用 `Database.getQueryLocator()` 方法，最多返回 5000 万条记录。

  Future方法需要有几个规范：

   1).方法必须是静态static的;

　　2).方法上方需要使用@Future标签;

　　3).方法返回类型必须是void类型;

　　4).方法参数必须是模块私有的变量，不能使public等;

　　5).方法参数不允许使用标准的Object或sObject类型，可以使用基本类型或者集合类型;

　　6).不能再一个future方法调用另一个future方法，当future方法运行的时候也不可以在trigger中调用;

　　7).future方法中不能使用getContent()和getContentAsPDF()方法。
>getContent() 和 getContentAsPDF() 方法在 Salesforce Apex 中属于同步调用，这意味着在请求处理过程中，执行会暂停，直到这些方法完成操作并返回结果。这种行为可能导致阻塞和性能问题，特别是在处理大量请求或需要较长时间才能完成的操作时。
future 方法被设计为处理异步操作，它允许将操作放入队列以在后台执行，从而避免阻塞或影响其他进程。因此，future 方法不支持同步调用，如 getContent() 和 getContentAsPDF()，因为这些方法可能导致阻塞或延迟，违反了 future 方法的异步设计原则。

    测试future方法在Test类中执行，和普通的方法测试区别的是，future方法执行需要在Test.startTest()和Test.stopTest()方法中进行.以下为测试代码：

```java
@isTest
private class Test_FutureSample {
    static testMethod void myUnitTest() {
        Test.startTest();
        List<ID> ids= new ID[]{'0012800000Hz6ozAAB','0012800000Hz6oxAAB'};
        FutureSample.futuremethod(ids);
        Test.stopTest();
    }
}
```
# 任务5.学会日志打印,根据日志排查与问题
