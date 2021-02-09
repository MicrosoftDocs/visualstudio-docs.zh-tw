---
title: 呼叫端 - 被呼叫端檢視 - 取樣資料 | Microsoft Docs
description: 閱讀呼叫端/被呼叫端的視圖如何顯示所選函式的程式碼剖析資訊，以及其在效能總管中的父系和子函數。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Caller/Callee view
- Caller/Callee view
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 376475d2a392b86b14a73ba45c5669eaaf338898
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886401"
---
# <a name="callercallee-view---sampling-data"></a>呼叫端/被呼叫端檢視 - 取樣資料
[呼叫端/被呼叫端] 檢視會顯示所選取函式及其父函式和子函式的分析資訊。 [呼叫端/被呼叫端] 檢視包含三個方格。

 **目前的函式** 會顯示在中間方格中，顯示所選取函式的分析資訊。 這些值包括對函式的所有取樣呼叫。

 **呼叫目前函式的函式** 會顯示在上方方格中，顯示呼叫端 (父) 函式對所選取 (目前) 函式之值的個別貢獻。

 **目前的函式所呼叫的函式** 會顯示在下方方格中，顯示所選取函式之被呼叫端 (子) 函式 (由目前函式所呼叫) 的分析資訊。

> [!NOTE]
> Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 UWP App 也需要新的收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。

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
|**型別**|函式的內容︰<br /><br /> -   **0** -目前的函式<br />-   **1** -呼叫目前函式的函式<br />-   **2** -目前的函式所呼叫的函式|
|**根函式名稱**|目前函數的名稱。|
|**內含樣本**|- 若為目前的函式，這是所收集的樣本數目，即使此函式或其中一個子函式正在執行。<br />- 若為呼叫端函式，這是當此函式呼叫目前函式時所收集，目前函式的內含樣本數目。<br />- 若為被呼叫端函式，這是當目前函式呼叫此函式時所收集，此函式的內含樣本數目。|
|**內含樣本 %**|分析執行的所有樣本中，屬於此函式之內含樣本的百分比。|
|**專有樣本**|- 若為目前的函式，這是當此函式直接執行時，亦即此函式在呼叫堆疊最上方時，在分析執行中所收集的樣本數目。 當此函式的子函式正在執行時所收集的樣本不會計入專有計數。<br />- 若為呼叫端函式，這是當此函式呼叫目前函式時所收集，目前函式的專有樣本數目。<br />- 若為被呼叫端函式，這是當目前函式呼叫此函式時所收集，此函式的專有樣本數目。|
|**專有樣本 %**|分析執行的所有樣本中，屬於此函式之專有樣本的百分比。|

## <a name="see-also"></a>另請參閱
- [呼叫端/被呼叫端視圖-.NET 記憶體取樣資料](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [呼叫端/被呼叫端視圖-.NET 記憶體檢測資料](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [呼叫端/被呼叫端視圖-檢測資料](../profiling/caller-callee-view-instrumentation-data.md)
