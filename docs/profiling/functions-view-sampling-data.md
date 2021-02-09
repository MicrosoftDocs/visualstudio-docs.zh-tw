---
title: 函式檢視 - 取樣資料 | Microsoft Docs
description: 請參閱取樣設定檔方法的函式報表查看，其中列出分析執行期間所取樣的函式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Functions View
- Functions view
ms.assetid: 029d5ebb-e551-46b0-b64e-2c553d9dbb8e
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 82b48689b6348c7d003f5418224260b7939e907a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907361"
---
# <a name="functions-view---sampling-data"></a>函式檢視 - 取樣資料
取樣方法的函式報表檢視會列出程式碼剖析執行期間取樣的函式。

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
|**內含樣本**|執行此函式時所收集的樣本總數；亦即此函式在呼叫堆疊上時所收集的樣本數目。 此數目包含此函式所呼叫的函式執行時收集的樣本。|
|**內含樣本 %**|分析執行的所有樣本中，屬於此函式之內含樣本的百分比。|
|**專有樣本**|此函式主體中的程式碼執行時 (亦即此函式在呼叫堆疊最上方時) 所收集的樣本總數。 不包含此函式所呼叫之函式中所收集的樣本。|
|**專有樣本 %**|分析執行的所有樣本中，屬於此函式之專有樣本的百分比。|

## <a name="see-also"></a>另請參閱
- [如何：自訂報表檢視資料行](../profiling/how-to-customize-report-view-columns.md)
- [函數視圖-檢測](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [函數視圖-取樣](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [函式檢視](../profiling/functions-view-instrumentation-data.md)
