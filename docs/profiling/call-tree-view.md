---
title: 呼叫樹狀圖檢視 | Microsoft Docs
description: 瞭解 [呼叫樹狀檢視]，其會顯示已在已分析的應用程式中進行的函式執行路徑。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.calltree
helpviewer_keywords:
- Call Tree view
- profiling tools reports, Call Tree view
- performance reports, Call Tree view
- profiling tools, Call Tree view
ms.assetid: b2dbc033-bf95-4d10-8e51-f9462979133e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 386f8e85c02fe73eab9801b3edf79ec0d0b178fc
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150778"
---
# <a name="call-tree-view"></a>呼叫樹狀圖檢視
[呼叫樹狀圖] 檢視顯示在分析的應用程式中周遊的函式執行路徑。 樹狀圖的根是應用程式或元件的進入點。 每個函式節點都會列出其所呼叫的所有函式，以及這些函式呼叫的效能資料。

 [呼叫樹狀圖] 檢視也可展開並反白顯示花最多時間或最常取樣的函式的執行路徑。 若要顯示效能資源使用最多的路徑，請以滑鼠右鍵按一下函式，然後按一下 [展開最忙碌路徑]。

 分析執行中的每個處理序都會顯示為根節點。 您可以設定 [呼叫樹狀圖] 檢視的開始節點，方法是以滑鼠右鍵按一下您想要設定為開始節點的節點，然後選取 [設定根目錄]。

 設定根節點時，除了所選取節點的樹狀子目錄以外，請從檢視中排除所有其他的項目。 您可以將根節點重設回先前檢視的節點。 在 [呼叫樹狀圖檢視] 視窗中，按一下滑鼠右鍵，然後選取 [重設根目錄]。

 [呼叫樹狀圖] 檢視可以自訂以新增或移除資料行。 以滑鼠右鍵按一下 [Column Name Title Bar] (資料行名稱標題列)，然後選取 [新增/移除資料行]。

 [呼叫樹狀圖] 檢視可以設定透過限制呈現的資料量來減少雜訊。 使用減少雜訊，可讓檢視中的效能問題更為顯著。 容易區分效能問題時，分析會較容易。 如需詳細資訊，請參閱 [如何：在報表檢視中設定減少雜訊](../profiling/how-to-configure-noise-reduction-in-report-views.md)。

> [!NOTE]
> 如果設定減少雜訊在啟用時顯示警告，則會在報表中顯示資訊列。

 如需 [呼叫樹狀圖] 檢視中資料行定義的詳細資訊，請參閱下列各項：

- [呼叫樹狀檢視](../profiling/call-tree-view-sampling-data.md)

- [呼叫樹狀檢視](../profiling/call-tree-view-instrumentation-data.md)

- [呼叫樹狀檢視-取樣](../profiling/call-tree-view-dotnet-memory-sampling-data.md)

- [呼叫樹狀檢視](../profiling/call-tree-view-contention-data.md)

## <a name="see-also"></a>另請參閱
- [效能報表檢視](../profiling/performance-report-views.md)
- [認識檢測資料值](../profiling/understanding-instrumentation-data-values.md)
- [認識取樣資料值](../profiling/understanding-sampling-data-values.md)
