---
title: 在 Visual Studio 中的自動功能暫止
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: d75c02bf6b817d03492a15b1f827f94eaaf3e306
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="automatic-feature-suspension"></a>自動功能暫止

如果可用的系統記憶體會設為 200 MB 或更少，Visual Studio 將程式碼編輯器中顯示下列訊息：

![警示文字中暫停完整解決方案分析](../code-quality/media/fsa_alert.png)

當 Visual Studio 偵測到記憶體不足的狀況時，它會自動暫停某些進階的功能，可協助它保持穩定。 Visual Studio 會繼續如常運作，但其效能的效能降低。

在記憶體不足情況下，會發生下列動作：

- 針對 Visual C# 和 Visual Basic 的完整解決方案分析已停用。

- [記憶體回收](/dotnet/standard/garbage-collection/index)已停用 Visual C# 和 Visual Basic (GC) 低度延遲模式。

- Visual Studio 快取排清。

## <a name="improve-visual-studio-performance"></a>改善 Visual Studio 效能

秘訣和訣竅如何改善 Visual Studio 效能處理大型方案或記憶體不足的狀況時，請參閱[針對大型方案的效能考量](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)。

## <a name="full-solution-analysis-suspended"></a>暫停的完整解決方案分析

根據預設，會完整解決方案分析 Visual basic 中啟用，而且停用 Visual C#。 不過，記憶體不足的狀況，在完整解決方案分析會自動停用 Visual Basic 和 Visual C# 中，不論其在 [選項] 對話方塊中的設定為何。 不過，您可以重新啟用完整解決方案分析選擇**重新啟用**中的資訊列出現時，藉由選取按鈕**啟用完整解決方案分析**核取方塊，或在 [選項] 對話方塊重新啟動 Visual Studio。 選項對話方塊永遠會顯示目前的完整解決方案分析設定。 如需詳細資訊，請參閱[How to： 啟用和停用完整解決方案分析](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)。

## <a name="gc-low-latency-disabled"></a>GC 低度延遲停用

若要重新啟用 GC 低度延遲模式，請重新啟動 Visual Studio。 根據預設，Visual Studio 可讓 GC 低度延遲模式，每當您輸入以確保您輸入的內容不會封鎖任何 GC 作業。 不過，如果記憶體不足的狀況會造成 Visual Studio 顯示自動擱置警告，GC 低度延遲模式已停用該工作階段。 重新啟動 Visual Studio 會重新啟用預設 GC 行為。 如需詳細資訊，請參閱<xref:System.Runtime.GCLatencyMode>。

## <a name="visual-studio-caches-flushed"></a>Visual Studio 快取排清

如果您繼續目前的開發工作階段或重新啟動 Visual Studio 時，會立即清空所有 Visual Studio 快取，但開始重新擴展。 排清的快取包含下列功能的快取：

- 尋找所有參考

- 巡覽至

- 加入 Using

此外，也會清除快取用於 Visual Studio 的內部作業。

> [!NOTE]
> 自動功能暫止警告只發生一次針對每個解決方案，不是在每個工作階段為基礎。 這表示如果您從 Visual Basic 切換至 Visual C# （或反之亦然），並執行到另一個記憶體不足的狀況，則可以可能取得另一個自動功能暫止的警告。

## <a name="see-also"></a>另請參閱

- [如何： 啟用和停用完整解決方案分析](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [記憶體回收的基本概念](/dotnet/standard/garbage-collection/fundamentals)
- [針對大型方案的效能考量](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)