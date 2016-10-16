# gl3527
作业要求：
1.使用power designer实现数据ER图 2.生成SQL语句 3.将ER截图和SQL直接整理成一个报告直接提交作业（不要使用附件），或者发布一个网页提交网页URL 4.使用Axure建立系统原型，要求至少实现设备巡检录入，设备保养情况查询，设备到期预警模块。要求原型有一定交互功能和设计说明（Axure使用参见附件或参考资料模块，Axure软件可从百度网盘--工具文件夹下载） 
------------------------------------------------------------------------------------------- 
owner需求：
1.保障生产正常进行，减少因设备故障导致的停产 2.系统能够制定合理的检修计划，降低检修成本 3.能够随时了解设备检修情况 4.设备到期提前预警 5.提高设备检修的规范性 user需求： 1.能够应对不同检修类型：年检，月检，季检，周检 2.同种类型设备很多，对于检查正常的设备是否可以不录入或快速录入 3.每种设备的检修（保养）项目不同，但同种设备项目基本固定 4.对于需要修理的设备，应该记录具体的修理内容和消耗的材料配件数量 5.系统能够打印出每台设备的检修报告 数据库应该实现的查询： 1.根据当前时间预警所有该检修的设备 2.根据设备编号，查询出设备检修报告（包括历史检修情况和材料消耗情况） 

设备保养数据库er图：
  ![image]（https://github.com/q3527/gl3527/blob/4edb745a5c7a3f44d64c952df1a5eab3398c5d17/er图.png）

设备保养记录/record通过e_id、s_id和设备表/equipment、保养人员表/staff形成一对多关系；
设备表/equipment通过ET_id和设备类型表/equipment_type形成多对一关系；；
而设备类型表/equipment_type可以通过M_id和保养表/maintain形成一对一关系；
保养表/maintain通过MI_id和保养项目形成一对多关系；
消耗记录/consume通过R_id以及MI_id和保养记录/record、保养项目/maintain_iterms分别形成一对一关系和一对多关系。

2.axure原型

设备保养情况录入:
![image]
（https://github.com/q3527/gl3527/blob/4edb745a5c7a3f44d64c952df1a5eab3398c5d17/home.png）
 
录入相关情况后点击提交后跳转到成功页面/失败页面，录入成功则将相关信息录入至相关数据库中：
  ![image]
（https://github.com/q3527/gl3527/blob/4edb745a5c7a3f44d64c952df1a5eab3398c5d17/%E8%AF%A6%E6%83%85%E5%BD%95%E5%85%A5.png）
 

  ![image](https://github.com/q3527/gl3527/blob/4edb745a5c7a3f44d64c952df1a5eab3398c5d17/%E5%BD%95%E5%85%A5%E6%88%90%E5%8A%9F.png)

查询设备的历史维修情况：
 ![image](https://github.com/q3527/gl3527/blob/4edb745a5c7a3f44d64c952df1a5eab3398c5d17/%E6%9F%A5%E8%AF%A2.png)
 
输入设备号，单击查询，从数据库中读出相关信息:

 ![image](https://github.com/q3527/gl3527/blob/4edb745a5c7a3f44d64c952df1a5eab3398c5d17/%E6%9F%A5%E8%AF%A2%E7%BB%93%E6%9E%9C.png)
 
 
相关查询sql语句：
查询设备保养情况：
select * FROM equipment_maintain.equipment, equipment_maintain.consume, equipment_maintain.record WHERE     equipment.E_id=001 and equipment.E_id=record.E_id =consume.E_id;


 

