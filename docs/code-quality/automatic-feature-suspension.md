---
title: 自動功能暫停
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b79588ea3ad67d717066535392b6789e2c0d1ae
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448660"
---
# <a name="automatic-feature-suspension"></a>自動功能暫停

如果可用的系統記憶體低於 200 MB 或更少，Visual Studio 會在程式碼編輯器中顯示下列訊息：

![暫停完整解決方案分析的警示文字](../code-quality/media/fsa_alert.png)

當 Visual Studio 偵測到記憶體不足的狀況時，它會自動暫停特定的「先進的功能」，協助它保持穩定。 Visual Studio 會繼續如之前一樣運作，但其效能已降低。

在記憶體不足的情況下，會發生下列動作：

- 已停用 Visual C#和 Visual Basic 的完整解決方案分析。

- 視覺效果C#和 Visual Basic 的[垃圾收集](/dotnet/standard/garbage-collection/index)（GC）低延遲模式已停用。

- Visual Studio 快取會排清。

## <a name="improve-visual-studio-performance"></a>改善 Visual Studio 效能

如需如何在處理大型解決方案或記憶體不足的情況下改善 Visual Studio 效能的秘訣和訣竅，請參閱[大型解決方案的效能考慮](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)。

## <a name="full-solution-analysis-suspended"></a>已暫停完整解決方案分析

根據預設，會啟用 Visual Basic 的完整解決方案分析，並針對視覺C#效果停用。 不過，在記憶體不足的情況下，不論其在 [選項] 對話方塊中的設定C#為何，皆會自動停用 Visual Basic 和視覺效果的完整解決方案分析。 不過，您可以在顯示的資訊列中選擇 [**重新啟用**] 按鈕、選取 [選項] 對話方塊中的 [**啟用完整解決方案分析**] 核取方塊，或重新開機 Visual Studio，以重新啟用完整的解決方案分析。 [選項] 對話方塊一律會顯示目前的完整解決方案分析設定。 如需詳細資訊，請參閱[如何：啟用和停用完整解決方案分析](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)。

## <a name="gc-low-latency-disabled"></a>停用 GC 低延遲

若要重新啟用 GC 低延遲模式，請重新開機 Visual Studio。 根據預設，每當您輸入時，Visual Studio 都會啟用 GC 低延遲模式，以確保您的輸入不會封鎖任何 GC 作業。 不過，如果記憶體不足的狀況導致 Visual Studio 顯示自動暫停警告，則會停用該會話的 GC 低延遲模式。 重新開機 Visual Studio 重新啟用預設的 GC 行為。 如需詳細資訊，請參閱<xref:System.Runtime.GCLatencyMode>。

## <a name="visual-studio-caches-flushed"></a>已排清 Visual Studio 快取

如果您繼續目前的開發會話或重新開機 Visual Studio，所有 Visual Studio 快取都會立即清空，但會開始重新擴展。 已排清的快取包含下列功能的快取：

- 尋找所有參考

- 巡覽至

- 新增使用

此外，也會清除用於內部 Visual Studio 作業的快取。

> [!NOTE]
> 自動功能暫止警告只會針對每個解決方案執行一次，而不會以每個會話為基礎。 這表示如果您從 Visual Basic 切換到視覺效果C# （反之亦然）並遇到另一個記憶體不足的狀況，您可能會收到另一個自動功能暫停警告。

## <a name="see-also"></a>請參閱

- [如何：啟用和停用完整解決方案分析](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [記憶體回收的基本概念](/dotnet/standard/garbage-collection/fundamentals)
- [大型解決方案的效能考慮](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
