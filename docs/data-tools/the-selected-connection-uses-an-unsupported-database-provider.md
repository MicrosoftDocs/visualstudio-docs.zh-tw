---
title: "選取的連接使用不支援的資料庫提供者 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 選取的連接使用不支援的資料庫提供者
當您將不使用 .NET Framework Data Provider for SQL Server 的項目從 \[**伺服器總管**\]\/\[**資料庫總管**\] 拖曳至[物件關聯式設計工具 \(O\/R 設計工具\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md) 時，就會出現這則訊息。  
  
 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]只支援使用 .NET Framework Provider for SQL Server 的資料連接。只有與 Microsoft SQL Server 或 Microsoft SQL Server 資料庫檔案的連接才是有效的連接。  
  
### 若要更正這個錯誤  
  
-   只將使用 .NET Framework Data Provider for SQL Server 的資料連接中的項目加入至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。  
  
## 請參閱  
 <xref:System.Data.SqlClient>   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [How to: Create Connections to SQL Server Databases](http://msdn.microsoft.com/zh-tw/360c340d-e5a6-4a7e-a569-e95d500be43d)   
 [.NET Framework 資料提供者](../Topic/.NET%20Framework%20Data%20Providers.md)   
 [逐步解說：建立 LINQ to SQL 類別 \(O\/R 設計工具\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [建立資料應用程式](../data-tools/creating-data-applications.md)