---
title: 標記檢視 | Microsoft Docs
description: 瞭解標記視圖如何顯示插入應用程式的取樣和 ETW 事件。
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.marks
helpviewer_keywords:
- profiling tools, Marks view
- profiling tools reports, Marks view
ms.assetid: b2773344-8081-4116-85a1-58f770448f6a
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b5b7eedaf7aac4a22ca10580395e085243f831ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851968"
---
# <a name="marks-view"></a>標記檢視
[標記] 檢視會顯示插入應用程式中的取樣和 ETW 事件。

 在報告中預先填入的預設標記會標示程式的開始和結束。

 此檢視也會顯示來自自動產生之標記的 Windows 計數器資料。 如需詳細資訊，請參閱 [如何：收集 Windows 計數器資料](../profiling/how-to-collect-windows-counter-data.md)。

 若要在兩個標記之間建立篩選，請選取標記，按一下滑鼠右鍵，然後按一下 [依標記加入篩選條件] 或 [依時間戳記加入篩選條件]。

 下表提供 [標記] 檢視中可用資料行的定義。

 **標記 ID** 分析標記的唯一識別碼。

 **標記名稱** 事件的名稱。

 **時間戳記** 從分析開始的時間到事件記錄完成的時間。

 Windows 效能計數器資料 收集 Windows 效能計數器資料時，值會顯示在含有計數器名稱的資料行中。

## <a name="see-also"></a>另請參閱
- [效能報告總覽](../profiling/performance-report-overview.md)
- [如何：收集 Windows 計數器資料](../profiling/how-to-collect-windows-counter-data.md)
- [&#91;筆尖&#93; 資料收集控制視窗](/previous-versions/bb385767(v=vs.110))