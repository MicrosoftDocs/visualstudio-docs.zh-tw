---
title: Status | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: debc70294bf0b513f22ed1cc06b9f0790da7b778
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="status"></a>狀態
VSPerfCmd.exe **Status** 選項會顯示分析工具和任何目前已分析處理序的狀態資訊。  
  
 **Status** 選項必須是命令列上指定的唯一選項。 必須先使用 VSPerfCmd.exe **Start** 選項來初始化分析工具，才能顯示任何狀態。  
  
## <a name="syntax"></a>語法  
  
```  
VSPerfCmd.exe /Status  
```  
  
#### <a name="parameters"></a>參數  
 無  
  
## <a name="remarks"></a>備註  
 **Status** 選項會顯示分析工具的下列狀態資訊。  
  
 **輸出檔名稱**  
 目前分析工具資料檔案的路徑和檔案名稱。  
  
 **收集模式**  
 SAMPLE 或 TRACE  
  
 **處理序最大數目**  
 可一次分析的處理序數目上限以及目前使用中處理序數目。  
  
 **執行緒最大數目**  
 可一次分析的執行緒數目上限。  
  
 **緩衝區數目**  
 專用來撰寫分析資料的記憶體緩衝區數目。  
  
 **緩衝區大小**  
 記憶體緩衝區的大小 (以位元組為單位)。  
  
 **Status** 選項會顯示每個目前正在分析之處理序的下列狀態資訊。  
  
 **Process**  
 已分析處理序的名稱。  
  
 **處理序 ID**  
 處理序的系統識別碼。  
  
 **Num 執行緒**  
 目前執行中的執行緒數目。  
  
 **開始/停止計數**  
 控制此處理序之資料收集的主要內部分析工具計數。 計數必須等於一，才能收集資料。 分析工具 API 以及 VSPerfCmd 選項 **GlobalOn**、**GlobalOff**、**ProcessOn**、**ProcessOff**、**ThreadOn** 和 **ThreadOff** 都可以操控開始/停止計數。  
  
 **暫止/繼續計數**  
 控制此處理序之資料收集的次要內部分析工具計數。 計數必須小於或等於零，才能收集資料。 只有分析工具 API 才能操控**暫止/繼續**計數。  
  
 **具有監視器存取權的使用者**  
 列出可存取分析工具的使用者名稱。 使用 VSPerfCmd.exe **Admin** 選項，其他使用者就可以獲授與存取權  
  
## <a name="see-also"></a>另請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [對 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)