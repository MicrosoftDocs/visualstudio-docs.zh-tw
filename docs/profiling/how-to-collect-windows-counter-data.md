---
title: 如何：收集 Windows 計數器資料 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c85187fd54d61fdf40956c8aee3c0a222d95a313
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776315"
---
# <a name="how-to-collect-windows-counter-data"></a>如何：收集 Windows 計數器資料

Windows 計數器是程式碼剖析期間可以設定的間隔收集的系統效能計數器。 在程式碼剖析工具報告的 [標記] 檢視中，每個收集間隔會有一個標示為 [自動標記]**** 的資料列。 該資料列包含以該間隔描述效能計數器值的資料行。 要將分析限制在兩個特定標記之間的時間段，請選擇標記，按右鍵，然後從快顯功能表中選擇 **"按** > **標記**篩選"。

> [!NOTE]
> Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 UWP App 也需要新的收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。

## <a name="to-collect-windows-counter-data"></a>收集 Windows 計數器資料

1. 在 [效能總管] 中，以滑鼠右鍵按一下您要為其設定 Windows 計數器的工作階段，然後選取 [屬性]****。

2. 在 [屬性頁]**** 中，按一下 [Windows 計數器]****。

3. 選取 [收集 Windows 計數器]**** 核取方塊。

4. 在 [收集間隔 (毫秒)]**** 文字方塊中，輸入一段時間。

5. 從 [計數器分類]**** 下拉式清單選取一個類別。

6. 從 [執行個體]**** 下拉式清單選取一個執行個體。

7. 選取對應用程式進行程式碼剖析時要使用的計數器。

8. 按一下 [套用]****。

## <a name="see-also"></a>另請參閱

[配置性能會話](../profiling/configuring-performance-sessions.md)
[性能會話屬性](../profiling/performance-session-properties.md)
[CPU 和 Windows 計數器](../profiling/cpu-and-windows-counters.md)
