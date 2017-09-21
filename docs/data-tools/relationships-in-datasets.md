---
title: "資料集中的關聯性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbData.Microsoft.VSDesigner.DataSource.DesignRelation"
  - "vbdata.Microsoft.VSDesigner.DataSource.DesignRelation"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "資料集 [Visual Basic], 關聯性"
  - "關聯性, 關於關聯性"
  - "關聯性, 資料集"
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
caps.latest.revision: 15
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料集中的關聯性
如同關聯式資料庫一樣，資料集可以包含關聯資料表。  增進資料表之間的關聯性之物件是 **DataRelation** 物件。  下列主題將提供有關 ADO.NET **DataRelation** 物件的資訊、建立這些物件的方法，以及如何運用這些物件來處理關聯資料表中的資料。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 在本節中  
 [DataRelation 物件簡介](../Topic/Introduction%20to%20DataRelation%20Objects.md)  
 針對資料集如何允許您指定資料表之間的關聯性，以及使用這些關聯性的優點來提供概觀。  
  
 [如何：以 DataSet 設計工具建立 DataRelation](../Topic/How%20to:%20Create%20DataRelations%20with%20the%20Dataset%20Designer.md)  
 說明如何使用 \[**DataSet 設計工具**\] 將 <xref:System.Data.DataRelation> 物件加入至資料集。  
  
 [如何：存取關聯 DataTable 中的資料錄](../Topic/How%20to:%20Access%20Records%20in%20Related%20DataTables.md)  
 說明如何以程式設計方式從具型別資料集的一對多關聯性資料表傳回相關資料錄。  
  
 [逐步解說：建立資料表之間的關聯性](../Topic/Walkthrough:%20Creating%20a%20Relationship%20between%20Data%20Tables.md)  
 提供以 \[**DataSet 設計工具**\] 建立兩個資料表並加入關聯的逐步指示。  
  
## 參考  
 <xref:System.Data.DataRelation>  
 表示兩個 T:System.Data.DataTable 物件之間的父子關聯性。  
  
 <xref:System.Data.DataRow.GetChildRows%2A>  
 取得 T:System.Data.DataRow 的子資料列。  
  
 <xref:System.Data.DataRow.GetParentRow%2A>  
 取得 T:System.Data.DataRow 的父資料列。  
  
 <xref:System.Data.Rule>  
 指示當強制使用 <xref:System.Data.ForeignKeyConstraint> 時發生的動作。  
  
 <xref:System.Data.DataColumn.Unique%2A>  
 取得或設定數值，指出資料行每個資料列的值是否必須是唯一。  
  
 <xref:System.Data.Constraint>  
 表示可以在一或多個 <xref:System.Data.DataColumn> 物件上強制使用的條件約束。  
  
## 相關章節  
 [加入 DataRelations](../Topic/Adding%20DataRelations.md)  
 說明如何在 <xref:System.Data.DataSet> 的資料表之間建立關聯。  
  
 [瀏覽 DataRelation](../Topic/Navigating%20DataRelations.md)  
 說明如何使用 <xref:System.Data.DataSet> 內資料表之間的關聯，傳回父\-子關係的子資料列或父資料列。  
  
 [巢狀 DataRelation](../Topic/Nesting%20DataRelations.md)  
 討論以 XML 資料表示 <xref:System.Data.DataSet> 內容時，巢狀 <xref:System.Data.DataRelation> 物件的重要性，並說明建立它們的方法。