---
title: 磁碟作業報告 (執行緒檢視) | Microsoft Docs
description: 磁碟作業報告顯示磁碟通道中的磁碟 I/O 作業。 查看針對每個磁片存取所報告的資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.diskoperations
helpviewer_keywords:
- Concurrency Visualizer, File Operations Report (Threads View)
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a6b0e15257d67e1d7ff1aaef14c2ebfff3775d6a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923725"
---
# <a name="disk-operations-report-threads-view"></a>磁碟作業報告 (執行緒檢視)
磁碟作業報告顯示磁碟通道中的磁碟 I/O 作業。

 代表在目前可見的時間範圍中正在進行程式碼剖析的處理序所發生每次磁碟存取，都會報告這項資訊︰

- 執行磁碟存取之處理序的名稱和 PID

- 存取磁碟的執行緒識別碼

- 已存取的檔案名稱

- 每個檔案的讀取次數

- 讀取的位元組數目

- 讀取延遲 (以毫秒為單位)

- 寫入次數

- 寫入的位元組數目

- 寫入延遲 (以毫秒為單位)

## <a name="see-also"></a>另請參閱
- [執行緒檢視](../profiling/threads-view-parallel-performance.md)