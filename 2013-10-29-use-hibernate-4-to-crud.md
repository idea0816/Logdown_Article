---
layout: post
title: 'Use Hibernate 4 to C.R.U.D.'
date: 2013-10-29 11:08
comments: true
categories: [hibernate, eclipse]
---
首先要說明： Hibernate Tools 只是減少設定的步驟，若要開發仍然是需要導入 Hibernate jars 才能繼續接下來的步驟。首先在 [Hibernate jars](http://www.hibernate.org/downloads) 下載後解壓縮；在一般無特別情況下解壓縮後只需取 \lib\required 資料夾中的 jar 即可完成以下的動作、其中所導入的 jars 如下(檔案依版本可能會有所不同)：

	antlr-2.7.7.jar
	dom4j-1.6.1.jar
	ibernate-commons-annotations-4.0.2.Final.jar
	hibernate-core-4.2.7.Final.jar
	hibernate-jpa-2.0-api-1.0.1.Final.jar
	javassist-3.18.1.GA.jar
	jboss-logging-3.1.0.GA.jar
	jboss-transaction-api_1.1_spec-1.0.1.Final.jar

接下來新增執行程式 \TestPackage\Main.class 。
![螢幕快照 2013-10-31 上午11.02.52.jpg](http://user-image.logdown.io/user/4050/blog/4101/post/155043/Jud10uToS8qqFnXZVetZ_%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202013-10-31%20%E4%B8%8A%E5%8D%8811.02.52.jpg)

``` java Main.class
package TestPackage;

import org.hibernate.Session;
import org.hibernate.SessionFactory;
import org.hibernate.Transaction;
import org.hibernate.cfg.Configuration;
import org.hibernate.service.ServiceRegistry;
import org.hibernate.service.ServiceRegistryBuilder;

public class Main {
	public static void main(String[] args) {
		
		//讀取hibernate.cfg.xml
		Configuration cfg = new Configuration();
		cfg.configure();
		
		//Hibernate 4.X 和 Hibernate 3.X 最大的修正差別處
		ServiceRegistry sr = new ServiceRegistryBuilder().
									applySettings(cfg.getProperties()).buildServiceRegistry();
		
		//打開與資料庫的工作階段並開始交易
		SessionFactory sf = cfg.buildSessionFactory(sr);
		Session session = sf.openSession();
		Transaction tx = session.beginTransaction();
		
		//C-第一個蘋果
		Apple apple = new Apple();
		apple.setId("1234");
		apple.setColor("red");
		apple.setSize(11.0d);
		apple.setWeight(0.5d);
		session.save(apple);
		
		//C-第二個蘋果
		Apple apple2 = new Apple();
		apple2.setId("2234");
		apple2.setColor("blue");
		apple2.setSize(22.0d);
		apple2.setWeight(1.0d);
		session.save(apple2);
		
		//得到蘋果的 ID
		String id = apple.getId();
		String id2 = apple2.getId();
		
		Apple newapple = null;
		
		//R-取得 Apple1 資料
		newapple = (Apple)session.get(Apple.class, id);
		System.out.println("Apple1 ID:" + newapple.getId()+
				",Color:"+ newapple.getColor()+
				",Size:"+ newapple.getSize()+
				",Weight:"+ newapple.getWeight());
		
		//R-取得 Apple2 資料
		newapple = (Apple)session.get(Apple.class, id2);
		System.out.println("Apple2 ID:" + newapple.getId()+
				",Color:"+ newapple.getColor()+
				",Size:"+ newapple.getSize()+
				",Weight:"+ newapple.getWeight());
		
		//U-修改 Apple2 顏色
		newapple.setColor("yellow");
		session.update(newapple);
		newapple = (Apple)session.get(Apple.class, id2);
		System.out.println("New Apple2 ID:" + newapple.getId()+
				",Color:"+ newapple.getColor()+
				",Size:"+ newapple.getSize()+
				",Weight:"+ newapple.getWeight());
		
		//D-刪除 Apple1 資料
		newapple = (Apple)session.get(Apple.class, id);
		session.delete(newapple);
		
		//完成交易
		tx.commit();
		
		//關閉工作階段
		session.close();
		
	}
}
```
在按下執行後會發現以下的狀況：
![螢幕快照 2013-11-01 上午9.24.12.jpg](http://user-image.logdown.io/user/4050/blog/4101/post/155043/b8W42OELRAydJexvc45H_%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202013-11-01%20%E4%B8%8A%E5%8D%889.24.12.jpg)

**第一個錯誤是：Error parsing JNDI name [HibernateTest]**
這個是 Hibernate Tools of Eclipse 還是依詢 3.X 時的設定，切換到 hibernate.cfg.xml 中將 session-factory 當中的 name 刪掉即可。
![螢幕快照 2013-11-01 上午9.24.53.jpg](http://user-image.logdown.io/user/4050/blog/4101/post/155043/HstTFbIWSBqA6ZcLZIpD_%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202013-11-01%20%E4%B8%8A%E5%8D%889.24.53.jpg)
**第二個錯誤是：Unknown entity: TestPackage.Apple**
這個錯誤就是前一篇所講的在 /session-factory 前要增加以下程式碼以對應所產出的資料庫對應檔

	<mapping resource="TestPackage/Apple.hbm.xml" />

以上就完成最簡單的 CRUD 了。