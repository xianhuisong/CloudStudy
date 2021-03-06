# 3分钟入门GCP之 - Cloud Storage Location

## 什么是location?

官网给出的定义：

A bucket's location defines the physical place where object data in the bucket resides.
（一个桶的位置指的是它里面的对象数据存储的物理地点）

这里面所说的物理地点，有个专有名字叫地区（region）。一个bucket的数据可以保存在：多个地区，两个地区，单独一个地区。

## 几个关键的点：
   1. 地区在创建桶的同时指定，一经指定，后续不可更改，但是数据可以从一个地区移动到不同的地区。
   2. 三种地区选项：
       2.1 单独一个：桶下面的数据只保存在单独一个地区中；
       2.2 成对地区：桶下面的数据保存在两个不同的地区；
       2.3 多个地区：数据保存在多个不同的地区
   3. 不同的地区选项对应着不同的数据冗余性。
   4. 地区下面对应着不同的区（zone），即使创建桶时指定单独地区（region），Cloud Storage也会保证其中的数据至少保存在两个不同的区（zone）。
   5. region之间至少相隔100 miles(英里)
   6. 如果桶设置成多个区域或两个区域，那么Cloud Storage会保证99.9%的新数据会在一个小时内复制完成。Cloud Storage提供了一个快速复制的选项，可以将复制时间控制在15分钟，但该功能仅适用于两个区域的桶。

## 如何选择合适的地区（region）：

    1. 地区的选择涉及到几方面： 延时，可用性，带宽花费
    2. 单独地区，由于不需要数据的复制，所以延时最小，网络数据传输的开销也最小。适合于数据和处理流在同一地区的情况。
    3. 两个地区，提供相对更高的可用性，因为数据是存储在两个不同的地区，数据复制延时也相对较小。适用于高可用的存储架构。
    4. 多个地区，当数据需要在更大的地理空间使用。

本文介绍了关于bucket中的region方面的信息，其主要涉及到数据的存储位置。不同的存储位置，会涉及到花费，可用性等因素。