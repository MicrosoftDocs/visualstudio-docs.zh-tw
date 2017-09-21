---
title: "如何：從命令提示字元建立程式碼剖析工具比較報表 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# 如何：從命令提示字元建立程式碼剖析工具比較報表
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以產生 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具報表，比較兩個程式碼剖析資料檔案 \(.VSP 或 .VSPS\) 的效能資料。  報告會顯示兩個程式碼剖析工作階段之間的差異、效能衰退和改善。  報告中的值會呈現與所指定第一個檔案之基準的差異 \(Delta\) 或變更。  這項差異的計算方法是找出舊的值 \(也就是基準值\) 以及新的分析結果值兩者之間的差異。  分析工具資料的比較基準可以是程式碼中的函式、應用程式中的模組、程式行、指定指標 \(IP\) 以及型別。  
  
 若要列出比較分類和欄位的識別項，請輸入下列命令列：  
  
 **VSPerfReport \/querydifftables**  *VspFileName1* *VspFileName2*  
  
 使用下列語法可以建立比較報告：  
  
 **VSPerfReport \/diff**  `VspFileName1` *VspFileName2* \[**\/**`Options`\]  
  
 您可以從下表將選項加入至 **VSPerfReport \/diff**  命令列。  
  
|選項|描述|  
|--------|--------|  
|**DiffThreshold:**\[*Value*\]|如果差異低於這個百分比臨界值，則忽略其差異。  此外，值低於此臨界值的新資料將不會顯示。|  
|**DiffTable:** *TableName*|使用此資料表可以比較檔案。  預設會使用函式資料表。  指定 **VSPerfReport \/querydifftables** 中列出的識別項。|  
|**DiffColumn:** *ColumnName*|使用此資料行可以比較值。  預設會使用專有樣本百分比資料行。  指定 **VSPerfReport \/querydifftables** 中列出的識別項。|