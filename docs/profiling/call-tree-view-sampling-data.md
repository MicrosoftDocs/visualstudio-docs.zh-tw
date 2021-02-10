---
title: 呼叫樹狀圖檢視 - 取樣資料 | Microsoft Docs
description: 閱讀 [呼叫樹狀檢視] 如何顯示效能總管中已分析之應用程式中所執行之函式執行路徑的取樣資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Call Tree view
- Call Tree view
ms.assetid: 5c4e8ec3-d0d3-485a-93bd-9060df4eb739
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c3a2f54f9cdd576a5c4d90c3a471febe516e6549
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950269"
---
# <a name="call-tree-view---sampling-data"></a>呼叫樹狀圖檢視 - 取樣資料
[呼叫樹狀圖] 檢視顯示在分析的應用程式中周遊的函式執行路徑。

> [!NOTE]
> Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 UWP App 也需要新的收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。

 樹狀圖的根是應用程式或元件的進入點。 每個函式節點會列出它所呼叫的所有函式，以及這些函式呼叫的相關效能資料。

 [呼叫樹狀圖] 檢視中的值，適用於呼叫樹狀圖中父函式所呼叫的函式執行個體。 百分比值的計算方式是比較函式執行個體值與分析執行中的樣本總數。

## <a name="highlight-the-execution-hot-path"></a>反白顯示執行最忙碌路徑
 [呼叫樹狀圖] 檢視可以展開並反白顯示最常取樣的處理序或函式的執行路徑。 若要顯示最常使用的路徑，請以滑鼠右鍵按一下進程或函式，然後按一下 [展開最忙碌 **路徑**]。

## <a name="set-the-call-tree-root-node"></a>設定呼叫樹狀圖根節點
 分析執行中的每個處理序都會顯示為根節點。 若要設定 [呼叫樹狀圖] 檢視的開始節點，請以滑鼠右鍵按一下您想要設定為開始節點的節點，然後選取 [設定根目錄]。

 設定根節點時，除了所選取節點的樹狀子目錄以外，請從檢視中排除所有其他的項目。 若要將根節點重設回原始節點，請在 [呼叫樹狀圖檢視] 視窗上按一下滑鼠右鍵，然後選取 [重設根目錄]。

|資料行|描述|
|------------|-----------------|
|**處理序識別碼**|分析執行的處理序 ID (PID)。|
|**進程名稱**|處理序的名稱。|
|**模組名稱**|包含該函式的模組名稱。|
|**模組路徑**|包含該函式的模組路徑。|
|**來源檔案**|含有這個函式定義的原始程式檔。|
|**函數名稱**|函式的完整格式名稱。|
|**函式行號**|原始程式檔中這個函式的開頭行號。|
|**函數位址**|函式的位址。|
|**Level**|此函式在呼叫樹狀圖中的深度。 只在[VSPerfReport](../profiling/vsperfreport.md) 命令列的報表中。|
|**專有樣本**|在呼叫樹狀圖中父函式呼叫此函式時，在此函式中所收集的樣本數目。 此數目不包含在此函式所呼叫之函式中所收集的樣本。|
|**專有樣本 %**|在呼叫樹狀圖中父函式呼叫此函式時，屬於此函式之專有樣本佔分析執行中所有樣本的百分比。|
|**內含樣本**|在呼叫樹狀圖中父函式呼叫此函式時，在此函式中所收集的樣本數目。 此數目包含在此函式所呼叫之函式中所收集的樣本。|
|**內含樣本 %**|在呼叫樹狀圖中父函式呼叫此函式時，屬於此函式之內含樣本佔分析執行中所有樣本的百分比。|

## <a name="see-also"></a>另請參閱
- [如何：自訂報表檢視資料行](../profiling/how-to-customize-report-view-columns.md)
- [呼叫樹狀結構檢視 - 分析工具取樣資料](../profiling/call-Tree-view-sampling-data.md)
- [呼叫樹狀檢視-取樣](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
- [呼叫樹狀檢視-檢測](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [呼叫樹狀檢視](../profiling/call-tree-view-instrumentation-data.md)
