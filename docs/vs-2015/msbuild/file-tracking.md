---
title: 檔案追蹤 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d8d999d65b207f72542b732842f6eb984df40764
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156463"
---
# <a name="file-tracking"></a>檔案追蹤
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

檔案追蹤會記錄對 Windows 檔案系統處理序及其子處理序的呼叫。 呼叫下列函式，程式可以控制此記錄開啟和關閉的時間，並指定要使用的記錄檔。  
  
## <a name="in-this-section"></a>本節內容  
 [EndTrackingContext](../msbuild/endtrackingcontext.md)  
 停止追蹤目前的內容。  
  
 [ResumeTracking](../msbuild/resumetracking.md)  
 呼叫 [SuspendTracking](../msbuild/suspendtracking.md) 後繼續追蹤。  
  
 [SetThreadCount](../msbuild/setthreadcount.md)  
 設定用於追蹤的執行緒數目。  
  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)  
 開始新的追蹤內容。  
  
 [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md)  
 使用指定的根目錄開始新的追蹤內容。  
  
 [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md)  
 結束追蹤並釋出使用的資源。  
  
 [SuspendTracking](../msbuild/suspendtracking.md)  
 暫時停止追蹤。  
  
 [WriteAllTLogs](../msbuild/writealltlogs.md)  
 寫出所有內容的追蹤記錄。  
  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)  
 寫出目前內容的追蹤記錄。
