## 论文记录

| 论文序号 | 论文标题                                                     | 论文类型 | 数据集                                                       | 影响因素 | 使用方法                                                     | 结论                                                         | 其他信息             |
| -------- | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ | ------------------------------------------------------------ | -------------------- |
| 1        | Artificial Intelligence Forecasting of Covid-19 in China     | AI       | 中国2020.1.11-2020.1.20的确诊病例数据来自澎湃新闻（https://www.thepaper.cn/），2020.1.21-2020.2.27的确诊病例数据来自WHO(https://www.who.int/emergencies/diseases/novelcoronavirus-2019/situation-reports)，这两个网址均无法获取数据集，于是从WHO官网找到了相应的数据下载（在该文目录对应的标题文件夹下）<br />除此之外，值得注意的是WHO 将 2020 年 1 月 21 日至 2020 年 2 月 13 日的实验室确诊病例作为确诊病例，并将 2020 年 2 月 14 日之后的临床确诊病例和实验室符合病例数之和作为确诊病例数。  2 月 14 日湖北省临床确诊和实验室确诊病例分别为 15,384 和 36,602。<br />于是2020.2.14之前的湖北确诊病例为<br />![image-20220123141013612](C:\Users\15975\AppData\Roaming\Typora\typora-user-images\image-20220123141013612.png) |          | 1、数据说明，34个地区包括31个省份+港澳台，（tij代表第i个地区总计确诊病例,Zij表示从2020.1.11开始，第j天第i个的地区新确诊的总数）<br />2、Modified auto-encoders（**MAE**)<br />![image-20220123150251078](C:\Users\15975\AppData\Roaming\Typora\typora-user-images\image-20220123150251078.png)<br />结点数输入层、第一隐层、第二隐层、输出层分别为8,32,4,1<br />3、1个segment是连续8天的数据，128个segment作为训练集，一共进行5次训练<br />4、损失函数<br />![image-20220123150743818](C:\Users\15975\AppData\Roaming\Typora\typora-user-images\image-20220123150743818.png)<br />其中Wi为权重，确定方法为如果对(ji/12)向上取整<br />5、除此之外<br />对于每个省份，在第二隐层中可以得到一个34*4的矩阵，对该矩阵进行奇异值分解后可以得到其最大的奇异值，5次训练结束后可以得到5个奇异值将其拼为一个特征向量，最后基于特征向量进行k-means聚类，用聚类结果来反映不同地区的geographic structure、health care resources and economic and social activities<br />![image-20220123153605708](C:\Users\15975\AppData\Roaming\Typora\typora-user-images\image-20220123153605708.png) | MAE模型的预测结果准确性很高(多步预测的准确性高)<br />聚类结果反映geographic and healthcare resource **structure** | 论文中未找到相关代码 |
| 2        | Assessing spread risk of Wuhan novel coronavirus within and beyond China, January-April 2020- a travel network-based modelling study | AI       |                                                              |          |                                                              |                                                              |                      |
|          |                                                              |          |                                                              |          |                                                              |                                                              |                      |


