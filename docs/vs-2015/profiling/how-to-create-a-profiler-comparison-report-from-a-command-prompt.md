---
title: 如何：從命令提示字元建立分析工具比較報表 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8c6dabbae5f2d3758aebe0562f99767ee6993d80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179565"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>如何：從命令提示字元建立程式碼剖析工具比較報表
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以產生 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 分析工具報表，以比較兩個分析資料 (.VSP 或 .VSPS) 檔案的效能資料。 這份報表會顯示兩個分析工作階段所發生的差異、效能衰退和改善。 報表中的值呈現與您所指定之第一個檔案的基準線的差異或變更。 這項差異的計算是透過判斷舊值 (即基準值) 與新分析中結果值之間的差異。 程式碼剖析工具資料的比較可以根據程式碼中的函式、應用程式中的模組、程式行、指令指標 (IP) 及型別。  
  
 若要列出比較類別和欄位的識別碼，請鍵入下列命令列：  
  
 **VSPerfReport /querydifftables**  *VspFileName1* *VspFileName2*  
  
 使用下列語法來建立比較報表：  
  
 **VSPerfReport/diff** `VspFileName1`*VspFileName2* [ **/** `Options` ]    
  
 您可以將下表中的選項新增至 **VSPerfReport /diff** 命令列。  
  
|選項|描述|  
|------------|-----------------|  
|**DiffThreshold:**[*值*]|如果低於這個百分比臨界值，則忽略差異。 此外，將不會顯示值低於此臨界值的新資料。|  
|**DiffTable:** *TableName*|使用此資料表來比較檔案。 預設會使用函式資料表。 指定 **VSPerfReport /querydifftables** 中所列的識別碼。|  
|**DiffColumn:** *ColumnName*|使用此資料行來比較值。 預設會使用專有樣本百分比資料行。 指定 **VSPerfReport /querydifftables** 中所列的識別碼。|
