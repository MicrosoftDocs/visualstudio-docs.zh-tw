---
title: 檔案追蹤 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 878d4d7e56c51d8a41a0e3cf3e78d6c83ed5d0b5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027668"
---
# <a name="file-tracking"></a>檔案追蹤
檔案追蹤會記錄對 Windows 檔案系統處理序及其子處理序的呼叫。 呼叫下列函式，程式可以控制此記錄開啟和關閉的時間，並指定要使用的記錄檔。  
  
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