---
layout: post
title: 'Hibernate Tools Generate Pojo Classes from DB Tables'
date: 2013-10-23 14:34
comments: true
categories: [hibernate]
---
**在反向生成 Pojo Classes 之前必需要先確認欲連結的資料表是否已有 主索引鍵/Primary Key 。**

	CREATE TABLE Apple(
  		id VARCHAR(32) NOT NULL PRIMARY KEY,
    	color VARCHAR(50),
    	size FLOAT,
    	weight FLOAT
	);

1. 右鍵 -> New -> Other -> Hibernate -> Hibernate Configuration File(cfg.xml)
![螢幕快照 2013-10-28 上午10.33.32.jpg](http://user-image.logdown.io/user/4050/blog/4101/post/154006/yt4hVSNQQC6S221NII5l_%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202013-10-28%20%E4%B8%8A%E5%8D%8810.33.32.jpg)
![螢幕快照 2013-10-28 上午10.33.57.jpg](http://user-image.logdown.io/user/4050/blog/4101/post/154006/kKicYXyRM2QRDOrgq6Eg_%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202013-10-28%20%E4%B8%8A%E5%8D%8810.33.57.jpg)
	將檔案放置在 src 資料夾下
![螢幕快照 2013-10-28 上午10.34.07.jpg](http://user-image.logdown.io/user/4050/blog/4101/post/154006/Trlv3XlSFeDyR0E8H6oN_%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202013-10-28%20%E4%B8%8A%E5%8D%8810.34.07.jpg)  
	依自己的環境設定資料庫連線
 ![螢幕快照 2013-10-28 上午10.35.22.jpg](http://user-image.logdown.io/user/4050/blog/4101/post/154006/DCKkaA41TV277Qqd3sWy_%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202013-10-28%20%E4%B8%8A%E5%8D%8810.35.22.jpg) 
	基本上這裡依照預設值不需去修改
![螢幕快照 2013-10-28 上午10.39.44.jpg](http://user-image.logdown.io/user/4050/blog/4101/post/154006/eM173BQfThqk3CcWdWuV_%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202013-10-28%20%E4%B8%8A%E5%8D%8810.39.44.jpg)  
	比較要注意的是要切換到 Classpath 頁籤去引入你的資料庫連結 Drivers(這裡不做也沒關係、在後續仍可再引用)
![螢幕快照 2013-10-28 上午10.42.28.jpg](http://user-image.logdown.io/user/4050/blog/4101/post/154006/OzrUW7QAyJckmWuPywq1_%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202013-10-28%20%E4%B8%8A%E5%8D%8810.42.28.jpg)  
	按下 Finish 後自動產生出 hibernate.cfg.xml (內容部份後續再另外解釋)

2. 顯示 Hibernate Configuration 窗口

	在預設狀況之下很有可能會沒有 Hibernate Configuration ，此窗口主要在看連結資料庫的狀況；若無出現依以下步驟：

	Window -> Show View -> Other -> Hibernate -> Hibernate Configurations
![螢幕快照 2013-10-28 上午10.49.17.jpg](http://user-image.logdown.io/user/4050/blog/4101/post/154006/0JkfZkoWRfqrCL1Vop4f_%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202013-10-28%20%E4%B8%8A%E5%8D%8810.49.17.jpg)  
![螢幕快照 2013-10-28 上午10.49.34.jpg](http://user-image.logdown.io/user/4050/blog/4101/post/154006/YP8iYmu2Qgq1EVpayRGs_%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202013-10-28%20%E4%B8%8A%E5%8D%8810.49.34.jpg)
	若之前無設定資料庫連結 Drivers ，這裡會無法顯示資料庫；在此將 Drivers 加入即可。
![螢幕快照 2013-10-28 上午10.50.10.jpg](http://user-image.logdown.io/user/4050/blog/4101/post/154006/4GGqjhG5QtmpTFwELgER_%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202013-10-28%20%E4%B8%8A%E5%8D%8810.50.10.jpg)
3. 產出 Hibernate Reverse Engineering File(reveng.xml)

	右鍵 -> New -> Other -> Hibernate -> Hibernate Reverse Engineering File(reveng.xml)	
![螢幕快照 2013-10-28 上午11.12.07.jpg](http://user-image.logdown.io/user/4050/blog/4101/post/154006/ENDrhNi5RXG0syZKA87K_%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202013-10-28%20%E4%B8%8A%E5%8D%8811.12.07.jpg)  
	一樣將檔案放置在 src 資料夾下
![螢幕快照 2013-10-28 上午11.13.23.jpg](http://user-image.logdown.io/user/4050/blog/4101/post/154006/GKyAwnbSaWnwt3lyxuRQ_%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202013-10-28%20%E4%B8%8A%E5%8D%8811.13.23.jpg)
	Console configuration 選剛剛建出來的設定檔
	點選 Refresh 就會出現資料庫
	點選資料庫的下拉選單出現資料表
	這時可以按 Shift 點選多個資料表再按 Include
![螢幕快照 2013-10-28 上午11.16.17.jpg](http://user-image.logdown.io/user/4050/blog/4101/post/154006/CS2o51ZTRaySgZGRebTd_%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202013-10-28%20%E4%B8%8A%E5%8D%8811.16.17.jpg)  
	最後按下 Finish 後自動產生出 hibernate.eveng.xml (內容部份一樣後續再另外解釋)


4. Reverse Engineering And Code Generation

	先將模式改成 Hibernate 模式。 Window -> Open Perspective -> Other -> Hibernate
![螢幕快照 2013-10-28 上午11.32.41.jpg](http://user-image.logdown.io/user/4050/blog/4101/post/154006/k89cxZ1DTsGUtrTE3Vpg_%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202013-10-28%20%E4%B8%8A%E5%8D%8811.32.41.jpg)  
	點選上方工具列 Run hibernate.reveng.xml -> Hbernate Code Generation Configufations...
![螢幕快照 2013-10-28 上午11.34.01.jpg](http://user-image.logdown.io/user/4050/blog/4101/post/154006/xZ9lr5zGRsWD0bHSBWcQ_%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202013-10-28%20%E4%B8%8A%E5%8D%8811.34.01.jpg)  
	右鍵點選 Hibernate Code Generation -> New
![螢幕快照 2013-10-28 上午11.35.08.jpg](http://user-image.logdown.io/user/4050/blog/4101/post/154006/5wZSw9X8SASnqmeFGr9q_%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202013-10-28%20%E4%B8%8A%E5%8D%8811.35.08.jpg)  
	**Main 頁籤**
	Name: HibernateConfiguration(可自行取名、不可和上方 Configuration 同名)
	Console configuration: 選擇剛建出的 Configuration
	Output directory 選擇專案的src資料夾
	將Reverse engineer from JDBC Connection 打勾
	Package 輸入要放置 entity 的資料夾
	reveng.xml 選擇剛建立出來的 hibernate.eveng.xml (Setup -> Use existing)
![螢幕快照 2013-10-28 上午11.48.54.jpg](http://user-image.logdown.io/user/4050/blog/4101/post/154006/Xu8N98nQNKJAUHCYgFuO_%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202013-10-28%20%E4%B8%8A%E5%8D%8811.48.54.jpg)  	
	**Exporters 頁籤**
	將 Use Java 5 syntax 、Domain code(.java)、Hibernate XML Mappings(.hbm.xml) 三項打勾
![螢幕快照 2013-10-28 上午11.50.06.jpg](http://user-image.logdown.io/user/4050/blog/4101/post/154006/dotJMufyRMS6ohnfqSeX_%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202013-10-28%20%E4%B8%8A%E5%8D%8811.50.06.jpg)
	**Common 頁籤**
	Encoding -> Other -> UTF-8
![螢幕快照 2013-10-28 上午11.51.24.jpg](http://user-image.logdown.io/user/4050/blog/4101/post/154006/W28myUuSHSz2tnEYJlBb_%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202013-10-28%20%E4%B8%8A%E5%8D%8811.51.24.jpg)  
	點選 Run 後就會出現反向生成的 Java 檔案
![螢幕快照 2013-10-28 上午11.52.36.jpg](http://user-image.logdown.io/user/4050/blog/4101/post/154006/k712KOeTUChEaHRPSk80_%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202013-10-28%20%E4%B8%8A%E5%8D%8811.52.36.jpg)