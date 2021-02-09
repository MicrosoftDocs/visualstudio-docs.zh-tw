---
title: 從檢測排除或包含精簡函式
description: 根據預設，不會呼叫其他函式的簡短函數會從檢測中排除，以降低額外負荷。 瞭解如何包含或排除它們。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9e4cdaf4262f136eb52b9eda7aef5aac831162c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873641"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>如何：從檢測排除或包含精簡函式
根據預設，程式碼剖析工具會從檢測排除 *小型函式*。 小型函式是不會進行任何函式呼叫的精簡函式。 排除這些小型函式可減少檢測負荷，並能因此改善檢測速度。 排除小型函式也會減少效能分析資料檔 (。*.vsp*) 大小和分析所需的時間。 如果已排除小型函式，小型函式所花費的時間會算在其父函式的專有和內含時間。 小型函式可以排除或包含在檢測中，如下列程序所述。

### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>從檢測排除或包含精簡函式

1. 在 [效能總管] 中，選取 [效能工作階段]，然後以滑鼠右鍵按一下並選取 [屬性]。

     [屬性頁面] 對話方塊隨即出現。

2. 在 [屬性頁] 中，按一下 [檢測] 屬性。

3. 若要從檢測排除精簡函式，請選取 [從檢測排除精簡函式]。 這是預設值。

     -或-

     若要在檢測中包含精簡函式，請清除 [從檢測排除精簡函式]。

4. 按一下 [確定]  。

## <a name="see-also"></a>另請參閱
- [控制資料收集](../profiling/controlling-data-collection.md)
- [效能工作階段屬性](../profiling/performance-session-properties.md)
