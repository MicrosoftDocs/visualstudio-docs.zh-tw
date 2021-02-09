---
title: 呼叫樹狀圖檢視 - 爭用資料 | Microsoft Docs
description: 查看 [呼叫樹狀檢視]，其會顯示在已分析之應用程式中所執行之函式執行路徑的爭用資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: 9bd4bde2-2ca3-446c-9ccc-7421522e03ae
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d6c444bba23ca216b058544d0ceae0d3d312fd4d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892368"
---
# <a name="call-tree-view---contention-data"></a>呼叫樹狀圖檢視 - 爭用資料
[呼叫樹狀圖] 檢視顯示在分析的應用程式中周遊的函式執行路徑。 樹狀圖的根是應用程式或元件的進入點。 每個函式節點都會列出它呼叫的所有函式，以及因函式與其他執行緒或處理序爭用資源而遭封鎖的次數和時間長度。

 [呼叫樹狀圖] 檢視中的值，適用於呼叫樹狀圖中父函式所呼叫的函式執行個體。 百分比值的計算方式是比較函式執行個體值與執行程式碼剖析期間的爭用總數。

## <a name="highlight-the-execution-hot-path"></a>反白顯示執行最忙碌路徑
 [呼叫樹狀圖] 檢視可以展開並反白顯示建立了大部分爭用的處理序或函式的執行路徑。

- 若要顯示最常使用的路徑，以滑鼠右鍵按一下處理序或函式，然後按一下 [展開最忙碌路徑]。

## <a name="set-the-call-tree-root-node"></a>設定呼叫樹狀圖根節點
 執行程式碼剖析期間的每個處理序都會顯示為根節點。 若要設定 [呼叫樹狀圖] 檢視的開始節點，以滑鼠右鍵按一下要設為開始節點的節點，然後按一下 [設定根目錄]。

 設定根節點時，除了所選取節點的樹狀子目錄以外，會從檢視中排除所有其他的項目。 若要將根節點重設回原始節點，在 [呼叫樹狀圖] 檢視上按一下滑鼠右鍵，然後按一下 [重設根目錄]。

|資料行|描述|
|------------|-----------------|
|**專有封鎖時間**|在此執行路徑中，此函式的執行個體遭到封鎖而無法在執行程式碼剖析期間執行的時間。 此時間不包括函式所呼叫的子函式封鎖時間。|
|**專有封鎖時間 %**|執行程式碼剖析期間，屬於此執行路徑中此函式的專有封鎖時間佔所有封鎖時間的百分比。|
|**專有爭用**|在此執行路徑中，於此函式的執行個體中發生的爭用數目。 此數目不包括函式所呼叫之子函式的爭用。|
|**專有爭用 %**|執行程式碼剖析期間，當樹狀圖中的父函式呼叫此函式時，屬於此函式執行個體的專用爭用佔所有爭用的百分比。|
|**函數位址**|函式的位址。|
|**函數名稱**|函式的完整格式名稱。|
|**內含封鎖時間**|在此執行路徑中，此函式的執行個體遭到封鎖而無法在執行程式碼剖析期間執行的時間總計。 此時間包括函式所呼叫的子函式封鎖時間。|
|**內含封鎖時間 %**|執行程式碼剖析期間，屬於此執行路徑中此函式執行個體的內含封鎖時間佔所有封鎖時間的百分比。|
|**內含爭用**|在此執行路徑中，封鎖此函式執行個體的爭用總數。 此數目包括函式所呼叫之子函式的爭用。|
|**內含爭用 %**|執行程式碼剖析期間，屬於此執行路徑中此函式執行個體的內含爭用佔所有爭用的百分比。|
|**Level**|函式在呼叫樹狀圖中的層級。 只存在於 VSReport 命令列報表中。 如需詳細資訊，請參閱 [VSPerfReport](../profiling/vsperfreport.md)。|
|**函式行號**|原始程式檔中這個函式的開頭行號。|
|**模組名稱**|包含該函式的模組名稱。|
|**模組路徑**|包含該函式的模組路徑。|
|**處理序識別碼**|分析執行的處理序 ID (PID)。|
|**進程名稱**|處理序的名稱。|
|**來源檔案**|含有這個函式定義的原始程式檔。|

## <a name="see-also"></a>另請參閱
- [如何：自訂報表檢視資料行](../profiling/how-to-customize-report-view-columns.md)
- [呼叫樹狀檢視](../profiling/call-tree-view.md)
- [呼叫樹狀檢視-檢測](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [呼叫樹狀檢視-取樣](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
- [呼叫樹狀檢視](../profiling/call-tree-view-instrumentation-data.md)
- [呼叫樹狀檢視](../profiling/call-tree-view-sampling-data.md)
