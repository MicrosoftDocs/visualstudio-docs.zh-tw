---
title: 檔案追蹤 | Microsoft Docs
description: 使用 MSBuild 檔案追蹤函式，將進程及其子進程的通話記錄到 Windows 檔案系統。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d61c3478515f2c8fa867666e6ff4ff72a0d4e65b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877118"
---
# <a name="file-tracking"></a>檔案追蹤

檔案追蹤會記錄對 Windows 檔案系統處理序及其子處理序的呼叫。 呼叫下列函式，程式可以控制此記錄開啟和關閉的時間，並指定要使用的記錄檔。

- [EndTrackingContext](../msbuild/endtrackingcontext.md) 停止追蹤目前的內容。

- [ResumeTracking](../msbuild/resumetracking.md) 呼叫 [SuspendTracking](../msbuild/suspendtracking.md) 後繼續追蹤。

- [SetThreadCount](../msbuild/setthreadcount.md) 設定用於追蹤的執行緒數目。

- [StartTrackingContext](../msbuild/starttrackingcontext.md) 開始新的追蹤內容。

- [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md) 使用指定的根目錄開始新追蹤內容。

- [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md) 結束追蹤並釋出使用的資源。

- [SuspendTracking](../msbuild/suspendtracking.md) 暫時停止追蹤。

- [WriteAllTLogs](../msbuild/writealltlogs.md) 寫出所有內容的追蹤記錄。

- [WriteContextTLogs](../msbuild/writecontexttlogs.md) 寫出目前內容的追蹤記錄。
