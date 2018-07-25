---
title: 檔案追蹤 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 394b40a304d2aba3b79c5878befe33a8a1aaf8b8
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37945555"
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