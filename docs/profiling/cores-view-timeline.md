---
title: 核心檢視時間軸 | Microsoft Docs
description: 瞭解時程表的基本概念：如何判斷哪個執行緒在任何時間點上的哪個核心執行，以及如何放大和縮小。
custom.ms: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cores.timeline.threads
helpviewer_keywords:
- Concurrency Visualizer, Cores View Timeline
ms.assetid: 10f0c666-ac2f-4ac5-9fb5-a88f660ab840
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: de09394bfc071cbe3dd1fedad52d1e5a511b62c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882891"
---
# <a name="cores-view-timeline"></a>核心檢視時間表
時間軸中的每個資料列都代表已分析系統上的邏輯處理器核心。 針對每個資料列，水平軸會顯示哪一個執行緒在指定時間點的邏輯核心上執行。 您可以將滑鼠指標停留在時間軸中感興趣的色彩上方，以傳回可識別執行緒的工具提示。 為了協助執行緒識別，視窗底部的圖例會顯示每個色彩所代表的內容。 使用 [縮放] 工具來放大和縮小，方法是按一下並拖曳，或按 CTRL 鍵並移動滑鼠滾輪。 切換 [核心檢視] 與 [執行緒檢視] 時，會維護縮放一致性。

## <a name="see-also"></a>另請參閱
- [核心檢視](../profiling/cores-view.md)
- [縮放控制項 (執行緒視圖) ](../profiling/zoom-control-threads-view.md)