---
title: " (Ip 的指令指標) view-.NET 記憶體取樣資料"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 6f02c2cea714b6c9688efff217ed546490f61764
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809946"
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>指令指標 (IP) 檢視 - .NET 記憶體取樣資料
使用取樣方法所收集之 .NET 記憶體配置分析資料的 IP 檢視，會列出已在分析回合期間配置記憶體的組件指令。 檢視的資料行也會列出配置的大小和數目。

 只會列出專有值。

|資料行|描述|
|------------|-----------------|
|**處理序識別碼**|分析執行的處理序 ID (PID)。|
|**進程名稱**|處理序的名稱。|
|**模組名稱**|包含該指令的模組名稱。|
|**模組路徑**|包含該指令的模組路徑。|
|**來源檔案**|包含此指令的原始程式檔。|
|**函數名稱**|函式的名稱。|
|**函式行號**|原始程式檔中這個函式的開頭行號。|
|**函數位址**|函式的開始位址。|
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
- [指令指標 (IP) 檢視](../profiling/instruction-pointers-ips-view-sampling-data.md)
