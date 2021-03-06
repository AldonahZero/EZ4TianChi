# EZ4TianChi
2021全国数字生态创新大赛 智能算法赛：生态资产智能分析
0.赛事背景

大赛名称：全国数字生态创新大赛-智能算法赛
大赛地址：
https://tianchi.aliyun.com/s/92ccdd364891b9e559a10e1df10079de（或文末阅读原文）
大赛类型：计算机视觉、语义分割
1. 赛题分析

赛题基于不同地形地貌的高分辨率遥感影像资料，要求参赛队伍利用遥感影像智能解译技术识别提取土地覆盖和利用类型，实现生态资产盘点、土地利用动态监测、水环境监测与评估、耕地数量与监测等应用。
地表类型(初赛)包括：
{
  1: "耕地",
  2: "林地",
  3: "草地",
  4: "道路",
  5: "城镇建设用地",
  6: "农村建设用地",
  7: "工业用地",
  8: "构筑物"
  9: "水域"
  10: "裸地"
 }


2. 赛题数据

赛题设置

初赛：利用算法对遥感影像进行10大类地物要素分类，主要考察算法地物分类的准确性；
复赛：利用AI算法对遥感影像进行10大类地物要素地物分类。同时考察算法地物分类的准确性及模型推理效率。
数据介绍

数据简介：数据为覆盖0.8m-2m分辨率的高分系列遥感多光谱影像，成像波段包括R、G、B、Nir波段，数据覆盖地貌包括：山地、丘陵地区、河湖（水库）、平原、城镇等等。感谢浙江大学环境与资源学院为本赛题提供数据支持。
数据规格：4万+张遥感影像及对应地物分类标记样本，影像大小为256*256像素。
初赛：16017张高分遥感影像和标注文件训练集，A榜测试集3000张测试数据，B榜测试集4366张测试数据。
复赛：15904张高分遥感影像和标注文件，6000张测试数据。
训练测试数据说明：影像保存格式为tif文件，包括R、G、B、Nir四个波段，训练测试集影像尺寸均为256 * 256像素。标签数据格式为单通道的png。
评价标准

初赛指标

使用通用指标平均交并比mIoU，计算每个类别的交并比的平均值，仅对算法效果进行评价，具体计算公式为：

其中，是目标类别数，是真值类别为i的像素被分为第j类的个数。
复赛指标

在初赛指标基础上，综合考虑算法效果、模型推理效率。具体如下：在mIoU的技术上引入模型效率评价指标，模型效率得分Fe，衡量模型推理时间得分，Fe的计算方式待复赛阶段公布。
最终成绩计算公式为：



3. 建模方法

首先可以对赛题的数据进行分析，下图所示左边为对应的标注，右边为原图。
从中大致看出，原始图片是比较模糊的，也表明赛题难度比较大。
图片
数据集案例
根据对赛题任务的理解，可以将赛题任务视为语义分割任务，则可以使用语义分割的流程来完成。
输入四通道图片，完成10通道输出。
具体的流程可以分为：
构建赛题数据集，数据&标签读取；
构建分割模型；
完成模型训练并提交；
