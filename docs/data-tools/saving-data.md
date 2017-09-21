---
title: "儲存資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataRow.RowState"
  - "DataSet.GetChanges"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "資料 [Visual Studio], 儲存"
  - "資料 [Visual Studio], 更新"
  - "資料庫, 更新"
  - "DBDirect 方法"
  - "儲存資料"
  - "TableAdapter DBDirect 方法"
  - "TableAdapter.Update 方法"
  - "更新資料"
  - "更新資料庫"
ms.assetid: 21d2b115-62e4-4ac9-a873-dcbb535b8af8
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 儲存資料
儲存資料是將應用程式之資料模型中已變更的資料維持在原始資料存放區 \(通常是關聯式資料庫，例如 SQL Server\) 中的程序。  
  
 透過資料模型更新資料來源的程序一般需要兩個步驟。  第一個步驟是以新資訊 \(新增的記錄、變更的記錄或刪除的記錄\) 來更新資料模型。  第二個步驟是將您資料模型中的變更存回資料庫。  
  
 下列主題描述與儲存資料相關聯的概念和工作。  
  
## 相關主題  
 [儲存資料集中的資料](../data-tools/save-data-back-to-the-database.md)  
 概述如何在資料集進行變更，以及資料集如何追蹤變更資訊，以將那些變更儲存至資料庫。  
  
 [儲存實體資料](../data-tools/saving-entity-data.md)  
 描述如何在 [ADO.NET Entity Framework](../Topic/ADO.NET%20Entity%20Framework.md) 和 [WCF Data Services 4.5](../Topic/WCF%20Data%20Services%204.5.md)應用程式中儲存變更。