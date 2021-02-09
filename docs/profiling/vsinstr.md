---
title: VSInstr | Microsoft Docs
description: 瞭解如何使用 VSInstr 工具來檢測二進位檔和其他各種 VSInstr 工具選項。
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- performance tools, instrumentation
- instrumentation, VSInstr tool
- profiling tools,VSInstr
- command-line tools, instrumentation
- command line, tools
- VSInstr
- VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 7b1334f7-f9b0-4a82-a145-d0607bfa8467
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 476822abe665bee18d082b7187bfa657cc360d3e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911648"
---
# <a name="vsinstr"></a>VSInstr
VSInstr 工具是用來檢測二進位檔。 使用下列語法叫用：

```cmd
VSInstr [/U] filename [/options]
```

 下表說明 VSInstr 工具選項：

|選項。|描述|
|-------------|-----------------|
|**Help** 或 **？**|顯示說明。|
|**U**|將重新導向的主控台輸出以 Unicode 寫入。 務必要優先指定此選項。|
|`@filename`|指定回應檔的名稱，此檔中的每一行都包含一個命令選項。  請勿使用引號。|
|**OutputPath**`:path`|指定檢測映像的目的目錄。 如果未指定輸出路徑，會重新命名原始的二進位檔，在相同目錄中將 "Orig" 附加到檔案名稱，然後檢測二進位檔的複本。|
|**排除：**`funcspec`|指定探查時要從檢測中排除的函式規格。 這在分析函式中的探查插入卻造成無法預期或不想要的結果時很有用。<br /><br /> 請勿使用 **Exclude** 和 **Include** 選項來參考相同二進位檔中的函式。<br /><br /> 您可以使用不同的 **Exclude** 選項來指定多個函式規格。<br /><br /> `funcspec` 會定義為：<br /><br /> [命名空間 \<separator1> ][類別 \<separator2> ]功能<br /><br /> \<separator1> 適用 `::` 于原生程式碼和 `.` managed 程式碼。<br /><br /> \<separator2> 一律是 `::`<br /><br /> 程式碼涵蓋範圍支援 **Exclude**。<br /><br /> 支援萬用字元 \*。 例如，要排除命名空間中的所有函式，可使用︰<br /><br /> MyNamespace::\*<br /><br /> 您可以使用 **VSInstr /DumpFuncs**，列出所指定二進位檔中函式的完整名稱。|
|**包含：** `funcspec`|指定二進位檔中的函式規格以使用探查來檢測。 二進位檔中的所有其他函式則不檢測。<br /><br /> 您可以使用不同的 **Include** 選項來指定多個函式規格。<br /><br /> 請勿使用 **Include** 和 **Exclude** 選項來參考相同二進位檔中的函式。<br /><br /> 程式碼涵蓋範圍不支援 **Include**。<br /><br /> `funcspec` 會定義為：<br /><br /> [命名空間 \<separator1> ][類別 \<separator2> ]功能<br /><br /> \<separator1> 適用 `::` 于原生程式碼和 `.` managed 程式碼。<br /><br /> \<separator2> 一律是 `::`<br /><br /> 支援萬用字元 \*。 例如，要包含命名空間中的所有函式，可使用︰<br /><br /> MyNamespace::\*<br /><br /> 您可以使用 **VSInstr /DumpFuncs**，列出所指定二進位檔中函式的完整名稱。|
|**DumpFuncs**|列出指定映像中的函式。 不會執行任何檢測。|
|**ExcludeSmallFuncs**|從檢測中排除小型函式，其為不會進行任何函式呼叫的精簡函式。 **ExcludeSmallFuncs** 選項的檢測負荷較低，因此可改善檢測速度。<br /><br /> 排除小型函式，也會減少 .*vsp* 的檔案大小和分析所需的時間。|
|**Mark:**{**Before**\|**After**\|**Top**\|**Bottom**}`,funcname,markid`|插入設定檔標記 (用來分隔報表中資料的識別碼)，您可以用來識別 .vsp 報告檔中某個資料範圍的開頭或結尾。<br /><br /> **Before** - 緊接在目標函式進入之前。<br /><br /> **After** - 緊跟在目標函式結束之後。<br /><br /> 以 **Top** -緊接在目標函式進入之後。<br /><br /> **Bottom** - 緊接在目標函式中的每個傳回之前。<br /><br /> `funcname` - 目標函式的名稱<br /><br /> `Markid` - 正整數 (長整數)，可用來當做設定檔標記的識別碼。|
|**涵蓋範圍**|執行涵蓋範圍檢測。 只能和下列選項搭配使用：**Verbose**、**OutputPath**、**Exclude** 及 **Logfile**。|
|**詳細資訊**|[詳細資訊] 選項是用來檢視有關檢測處理序的詳細資訊。|
|**NoWarn**`[:[Message Number[;Message Number]]]`|隱藏所有或特定的警告。<br /><br /> `Message Number` - 警告編號。 如果省略 `Message Number`，則會隱藏所有警告。<br /><br /> 如需詳細資訊，請參閱 [VSInstr 警告](../profiling/vsinstr-warnings.md)。|
|**控制項：** `{`**執行緒** \|**進程** \|**全域**`}`|指定下列 VSInstr 資料收集控制選項的程式碼剖析層級︰<br /><br /> **開始**<br /><br /> **StartOnly**<br /><br /> **暫止**<br /><br /> **StopOnly**<br /><br /> **SuspendOnly**<br /><br /> **ResumeOnly**<br /><br /> **Thread** - 指定執行緒層級的資料收集控制函式。 只會針對目前的執行緒啟動或停止程式碼剖析。 不會影響其他執行緒的程式碼剖析狀態。 預設值為 Thread。<br /><br /> **Process** - 指定處理序層級的程式碼剖析資料收集控制函式。 可針對目前處理序中的所有執行緒啟動或停止程式碼剖析。 不會影響其他處理序的程式碼剖析狀態。<br /><br /> **Global** - 指定全域層級 (跨處理序) 的資料收集控制函式。<br /><br /> 如果您沒有指定程式碼剖析層級，就會發生錯誤。|
|**開始：** `{`**內部** \|**外部**`},funcname`|限制只對目標函式和該函式呼叫的子函式收集資料。<br /><br /> **Inside** - 在目標函式進入之後，立即插入 StartProfile 函式。 在目標函式中的每個傳回之前，立即插入 StopProfile 函式。<br /><br /> **Outside** - 在每次呼叫目標函式之前，立即插入 StartProfile 函式。 在每次呼叫目標函式之後，立即插入 StopProfile 函式。<br /><br /> `funcname` - 目標函式的名稱。|
|**暫止：** `{`**內部** \|**外部**`},funcname`|排除對目標函式和該函式呼叫的子函式收集資料。<br /><br /> **Inside** - 在目標函式進入之後，立即插入 SuspendProfile 函式。 在目標函式中的每個傳回之前，立即插入 ResumeProfile 函式。<br /><br /> **Outside** - 在目標函式進入之前，立即插入 SuspendProfile 函式。 在從目標函式離開之後，立即插入 ResumeProfile 函式。<br /><br /> `funcname` - 目標函式的名稱。<br /><br /> 如果目標函式包含 StartProfile 函式，請在它之前插入 SuspendProfile 函式。 如果目標函式包含 StopProfile 函式，請在它之後插入 ResumeProfile 函式。|
|**StartOnly:** `{` **Before** \| **After** \| **Top** \| **Bottom** `},funcname`|在執行程式碼剖析期間開始資料收集。 在指定位置插入 StartProfile API 函式。<br /><br /> **之前** -緊接在目標函式進入之前。<br /><br /> **After** -緊接在目標函式結束之後。<br /><br /> **Top** - 緊跟在目標函式進入之後。<br /><br /> 在目標函式中的每個傳回之前，緊接在最 **下方**。<br /><br /> `funcname` - 目標函式的名稱。|
|**StopOnly:**{**Before**\|**After**\|**Top**\|**Bottom**}`,funcname`|在執行程式碼剖析期間暫止資料收集。 在指定位置插入 StopProfile API 函式。<br /><br /> **之前** -緊接在目標函式進入之前。<br /><br /> **After** -緊接在目標函式結束之後。<br /><br /> **Top** - 緊跟在目標函式進入之後。<br /><br /> 在目標函式中的每個傳回之前，緊接在最 **下方**。<br /><br /> `funcname` - 目標函式的名稱。|
|**SuspendOnly:**{**Before**\|**After**\|**Top**\|**Bottom**}`,funcname`|在執行程式碼剖析期間暫止資料收集。 在指定位置插入 SuspendProfile API。<br /><br /> **之前** -緊接在目標函式進入之前。<br /><br /> **After** -緊接在目標函式結束之後。<br /><br /> **Top** - 緊跟在目標函式進入之後。<br /><br /> 在目標函式中的每個傳回之前，緊接在最 **下方**。<br /><br /> `funcname` - 目標函式的名稱。<br /><br /> 如果目標函式包含 StartProfile 函式，請在它之前插入 SuspendProfile 函式。|
|**ResumeOnly:**{**Before**\|**After**\|**Top**\|**Bottom**}`,funcname`|在執行程式碼剖析期間開始或繼續資料收集。<br /><br /> 其通常是在 **SuspendOnly** 選項已停止程式碼剖析之後，用來啟動程式碼剖析。 在指定位置插入 ResumeProfile API。<br /><br /> **之前** -緊接在目標函式進入之前。<br /><br /> **After** -緊接在目標函式結束之後。<br /><br /> **Top** - 緊跟在目標函式進入之後。<br /><br /> 在目標函式中的每個傳回之前，緊接在最 **下方**。<br /><br /> `funcname` - 目標函式的名稱。<br /><br /> 如果目標函式包含 StopProfile 函式，請在它之後插入 ResumeProfile 函式。|

## <a name="see-also"></a>另請參閱
- [VSPerfMon](../profiling/vsperfmon.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [VSInstr 警告](../profiling/vsinstr-warnings.md)
- [效能報表檢視](../profiling/performance-report-views.md)
