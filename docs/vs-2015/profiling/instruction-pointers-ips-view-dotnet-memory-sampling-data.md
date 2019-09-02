---
title: 指令指標 (IP) 檢視 - .NET 記憶體取樣資料 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dd06bc09114785c4359d05e3cda70c3ce7646c9e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68143685"
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>指令指標 (IP) 檢視 - .NET 記憶體取樣資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用取樣方法所收集之 .NET 記憶體配置分析資料的 IP 檢視，會列出已在分析回合期間配置記憶體的組件指令。 檢視的資料行也會列出配置的大小和數目。  
  
 只會列出專有值。  
  
|資料行|說明|  
|------------|-----------------|  
|**處理序 ID**|分析執行的處理序 ID (PID)。|  
|**處理序名稱**|處理序的名稱。|  
|**模組名稱**|包含該指令的模組名稱。|  
|**模組路徑**|包含該指令的模組路徑。|  
|**原始程式檔**|包含此指令的原始程式檔。|  
|**函式名稱**|函式的名稱。|  
|**函式行號**|原始程式檔中這個函式的開頭行號。|  
|**函式位址**|函式的開始位址。|  
|**原始程式碼開頭行**|發生配置的原始程式檔中的起始行號。|  
|**原始程式碼結尾行**|發生配置的原始程式檔中的結尾行號。|  
|**原始程式碼開頭字元**|發生配置的原始程式檔行中，起始字元的位移。|  
|**原始程式碼結尾字元**|發生配置的原始程式檔行中，結尾字元的位移。|  
|**指令位址**|指令的位址。|  
|**專有配置**|指令所建立的物件總數。|  
|**專有配置 %**|指令所配置之分析回合中所建立的所有物件百分比。|  
|**專有位元組**|指令所配置之分析回合中所配置記憶體的位元組數目。|  
|**專有位元組 %**|指令所配置之分析回合中所配置記憶體的所有位元組百分比。|  
  
## <a name="see-also"></a>另請參閱  
 [指令指標 (IP) 檢視](../profiling/instruction-pointers-ips-view-sampling-data.md)
