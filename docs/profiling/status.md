---
title: Status | Microsoft Docs
description: 瞭解 VSPerfCmd.exe Status 選項如何顯示程式碼剖析工具狀態的相關資訊，以及目前正在分析的任何處理程式。
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c77c78258b5ddef486dc35ed6a620003864254cc
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722707"
---
# <a name="status"></a>狀態
*VSPerfCmd.exe* **Status** 選項會顯示分析工具和任何目前已分析處理序的狀態資訊。

 **Status** 選項必須是命令列上指定的唯一選項。 必須先使用 *VSPerfCmd.exe* **Start** 選項來初始化分析工具，才能顯示任何狀態。

## <a name="syntax"></a>語法

```cmd
VSPerfCmd.exe /Status
```

#### <a name="parameters"></a>參數
 None

## <a name="remarks"></a>備註
 **Status** 選項會顯示分析工具的下列狀態資訊。

 **輸出檔名稱** 目前分析工具資料檔案的路徑和檔案名稱。

 **收集模式** SAMPLE 或 TRACE

 **處理序最大數目** 可一次分析的處理序數目上限，以及目前使用中的處理序數目。

 **執行緒最大數目** 可一次分析的執行緒數目上限。

 **緩衝區數目** 專用來撰寫分析資料的記憶體緩衝區數目。

 **緩衝區大小** 記憶體緩衝區的大小 (以位元組為單位)。

 **Status** 選項會顯示每個目前正在分析之處理序的下列狀態資訊。

 **處理序** 已分析處理序的名稱。

 **處理序識別碼** 處理序的系統識別碼。

 **執行緒數目** 目前執行中的執行緒數目。

 **開始/停止計數** 主要內部分析工具計數，用來控制此處理序的資料收集。 計數必須等於一，才能收集資料。 分析工具 API 以及 VSPerfCmd 選項 **GlobalOn**、**GlobalOff**、**ProcessOn**、**ProcessOff**、**ThreadOn** 和 **ThreadOff** 都可以操控開始/停止計數。

 **暫停/繼續計數** 主要內部分析工具計數，用來控制此處理序的資料收集。 計數必須小於或等於零，才能收集資料。 只有分析工具 API 才能操控 **暫止/繼續** 計數。

 **具有監視存取權的使用者** 列出可存取分析工具的使用者名稱。 使用 VSPerfCmd.exe **Admin** 選項，其他使用者就可以獲授與存取權

## <a name="see-also"></a>另請參閱
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [分析 ASP.NET web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [分析服務](../profiling/command-line-profiling-of-services.md)
