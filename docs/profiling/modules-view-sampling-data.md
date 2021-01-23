---
title: 模組檢視 - 取樣資料 | Microsoft Docs
description: 瞭解取樣資料的模組視圖如何顯示依分析資料中取樣的模組分組的效能資料。
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
- sampling profiling method,Modules view
ms.assetid: 816f5633-65d7-41e5-aee1-033628d4e2df
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0de246e5ecdc51ff6471eeed242d638fee261c8c
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722954"
---
# <a name="modules-view---sampling-data"></a>模組檢視 - 取樣資料
取樣資料的模組檢視，依據分析資料中取樣的模組來分組顯示效能資料。 每個模組都是階層式樹狀結構的根。 模組的取樣函式列在模組節點之下。

> [!NOTE]
> Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 UWP App 也需要新的收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。

 如果收集樣本的時候正在執行函式 (即函式在呼叫堆疊最上方)，則執行中的原始程式行和指令位址會列在函式節點之下。 因為資料是在執行程式行或指令時，針對原始程式行或指令指標來收集資料，所以程式行資料和指令資料的內含值和專屬值一律相同。

|資料行|描述|
|------------|-----------------|
|**名稱**|模組、函式、行號或指令指標位址的名稱。|
|**處理序識別碼**|分析執行的處理序 ID (PID)。|
|**進程名稱**|處理序的名稱。|
|**模組名稱**|包含該函式、程式行或指令指標的模組名稱。|
|**模組路徑**|包含該模組、函式、程式行或指令指標的模組路徑。|
|**來源檔案**|含有這個函式定義的原始程式檔。|
|**函式行號**|原始程式檔中這個函式的開頭行號。|
|**內含樣本**|-   對於函式，這是執行中的此函式或此函式呼叫之函式的樣本數，亦即包含此函式的呼叫堆疊樣本。<br />-   對於模組，這是至少有一個該模組的函式正在其中執行的樣本數量。<br />-   對於程式行或指令，這是此程式行或指令正在其中執行的樣本數量。|
|**內含樣本 %**|-   對於函式或模組，這是分析執行中此函式或模組的內含樣本佔所有樣本的百分比。<br />-   對於程式行或指令，這是分析執行中，其中正在執行此程式行或指令之所有樣本的百分比。|
|**專有樣本**|-   對於函式，這是此函式直接在其中執行的呼叫堆疊樣本數，亦即此函式在呼叫堆疊最上方的樣本數量。<br />-   對於模組，這是模組中函式之專有樣本的總和。<br />-   對於程式行或指令，這是此程式行或指令正在其中執行的樣本數量。|
|**專有樣本 %**|-   對於函式或模組，這是分析執行中此函式或模組的專有樣本佔所有樣本的百分比。<br />-   對於程式行或指令，這是分析執行中，其中正在執行此程式行或指令之所有樣本的百分比。|

## <a name="see-also"></a>另請參閱
- [模組檢視 - 取樣](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [模組視圖-檢測](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [模組檢視](../profiling/modules-view-instrumentation-data.md)
