---
title: 啟動和結束效能資料收集 | Microsoft Docs
description: 瞭解如何在開始分析之前，將您想要分析的目標二進位檔新增至效能會話。
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.wizard.summarypage
helpviewer_keywords:
- profiling tools, launching sessions
- performance sessions, launching
- performance sessions, ending
- profiling tools, ending sessions
ms.assetid: 9f6eb0d5-d9e9-4bec-b627-445065610bce
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0db420bbc6da16460e599ff8912569f97b506f22
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721719"
---
# <a name="how-to-start-and-end-performance-data-collection"></a>如何：啟動和結束效能資料收集
您必須將要進行程式碼剖析的目標二進位檔加入至效能工作階段，然後才能開始進行程式碼剖析。 若要加入目標，請以滑鼠右鍵按一下 [效能總管] 中的 [目標]，然後按一下 [加入目標二進位檔]。 在 [加入目標二進位檔] 對話方塊中，選取檔案名稱，然後按一下 [開啟]。 新的二進位檔就會加入。

### <a name="to-start-profiling"></a>啟動程式碼剖析

1. 在 [效能總管] 視窗中以滑鼠右鍵按一下效能工作階段的名稱，然後選擇下列其中一個選項：

    - [啟動並啟用程式碼剖析] - 啟動應用程式並立即開始執行程式碼剖析。

    - [啟動並暫停程式碼剖析] - 啟動應用程式，但不會開始執行程式碼剖析。 您可以選取 [資料收集控制] 視窗中的 [繼續收集]，以啟動程式碼剖析。 如需詳細資訊，請參閱[如何︰暫停和繼續效能資料收集](../profiling/how-to-pause-and-resume-performance-data-collection.md)。

### <a name="to-end-profiling"></a>結束程式碼剖析

- 結束程式碼剖析工作階段的建議方式，是結束應用程式。 若要立即停止程式碼剖析，請在 [效能總管] 工具列上按一下 [停止]。

## <a name="see-also"></a>另請參閱
- [控制資料收集](../profiling/controlling-data-collection.md)
- [如何：暫停和繼續效能資料收集](../profiling/how-to-pause-and-resume-performance-data-collection.md)
