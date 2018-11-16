---
title: 函式檢視 - 取樣資料 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- sampling profiling method,Functions View
- Functions view
ms.assetid: 029d5ebb-e551-46b0-b64e-2c553d9dbb8e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d74ed306c2e8396b1b7bc06910105552fc7d5873
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733033"
---
# <a name="functions-view---sampling-data"></a>函式檢視 - 取樣資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

取樣方法的函式報表檢視會列出程式碼剖析執行期間取樣的函式。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 Windows 市集應用程式也需要新的資料收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
|資料行|描述|  
|------------|-----------------|  
|**處理序 ID**|分析執行的處理序 ID (PID)。|  
|**處理序名稱**|處理序的名稱。|  
|**模組名稱**|包含該函式的模組名稱。|  
|**模組路徑**|包含該函式的模組路徑。|  
|**原始程式檔**|含有這個函式定義的原始程式檔。|  
|**函式名稱**|函式的完整格式名稱。|  
|**函式行號**|原始程式檔中這個函式的開頭行號。|  
|**函式位址**|函式的位址。|  
|**內含樣本**|執行此函式時所收集的樣本總數；亦即此函式在呼叫堆疊上時所收集的樣本數目。 此數目包含此函式所呼叫的函式執行時收集的樣本。|  
|**內含樣本 %**|分析執行的所有樣本中，屬於此函式之內含樣本的百分比。|  
|**專有樣本**|此函式主體中的程式碼執行時 (亦即此函式在呼叫堆疊最上方時) 所收集的樣本總數。 不包含此函式所呼叫之函式中所收集的樣本。|  
|**專有樣本 %**|分析執行的所有樣本中，屬於此函式之專有樣本的百分比。|  
  
## <a name="see-also"></a>另請參閱  
 [如何：自訂報表檢視資料行](../profiling/how-to-customize-report-view-columns.md)   
 [函式檢視 - 檢測](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [函式檢視 - 取樣](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [函式檢視](../profiling/functions-view-instrumentation-data.md)



