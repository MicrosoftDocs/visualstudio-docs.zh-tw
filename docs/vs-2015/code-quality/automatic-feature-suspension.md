---
title: 自動功能暫停 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ab9b6e0ee62bc2506022a853a04871902fa04aad
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58944161"
---
# <a name="automatic-feature-suspension"></a>自動功能暫停
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
如果您的可用系統記憶體落在設為 200 MB 或更少，Visual Studio 會顯示下列訊息，程式碼編輯器中。

 ![警示文字中暫停完整解決方案分析](../code-quality/media/fsa-alert.png "FSA_Alert")

 當 Visual Studio 偵測到記憶體不足的情況時，它會自動暫停某些進階的功能，可協助它保持穩定。 當這個進階的功能暫止警告會出現，Visual Studio 會繼續運作，但會稍微降低其效能。

 在記憶體不足情況下，會發生下列情況：

-   針對 Visual C# 和 Visual Basic 的完整解決方案分析已停用。

-   [記憶體回收](http://msdn.microsoft.com/library/22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9)(GC) Visual C# 和 Visual Basic 的低延遲模式已停用。

-   Visual Studio 將快取清除。

## <a name="improve-visual-studio-performance"></a>改善 Visual Studio 效能
 祕訣和訣竅，如何處理大型解決方案或低記憶體情況時，改善 Visual Studio 效能，請參閱[大型解決方案的效能考量](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)。

## <a name="full-solution-analysis-suspended"></a>暫止的完整解決方案分析
 根據預設，是針對 Visual Basic 啟用完整解決方案分析，並將其停用 Visual C# 中。 不過，在記憶體不足情況下，完整解決方案分析會自動停用 Visual Basic 和 Visual C# 中，不論其在 [選項] 對話方塊中的設定為何。 不過，您可以重新啟用完整解決方案分析選擇**重新啟用**中的資訊列出現時，藉由選取按鈕**啟用完整解決方案分析**核取方塊，在 [選項] 對話方塊中，或重新啟動 Visual Studio。 [選項] 對話方塊中一律會顯示目前的完整解決方案分析設定。 如需詳細資訊，請參閱[如何：啟用和停用完整解決方案分析](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)。

## <a name="gc-low-latency-disabled"></a>GC 低度延遲停用
 若要重新啟用 GC 低延遲模式，請重新啟動 Visual Studio。  根據預設，Visual Studio 可讓 GC 低延遲模式，只要您輸入以確保您輸入的內容不會封鎖任何 GC 作業。 不過，如果記憶體不足的情況會導致 Visual Studio 顯示自動暫止警告，GC 低延遲模式已停用該工作階段中。 重新啟動 Visual Studio 會重新啟用預設的 GC 行為。 如需詳細資訊，請參閱<xref:System.Runtime.GCLatencyMode>。

## <a name="visual-studio-caches-flushed"></a>Visual Studio 快取排清

Visual Studio 的所有快取會立即清空，但重新擴展，如果您繼續您目前的開發工作階段，或重新啟動 Visual Studio 就會開始。 排清的快取包含下列功能的快取。

-   尋找所有參考

-   巡覽至

-   加入 Using

此外，也會清除快取用於 Visual Studio 的內部作業。

> [!NOTE]
> 自動功能暫停警告只出現一次上為每個解決方案，不以個別工作階段為基礎。 這表示如果您從 Visual Basic 切換至 Visual C# （或反之亦然），並執行到另一個記憶體不足的情況，您可以可能取得另一個自動功能暫停警告。

## <a name="see-also"></a>另請參閱

- [如何：啟用和停用完整解決方案分析](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [記憶體回收的基本概念](http://msdn.microsoft.com/library/67c5a20d-1be1-4ea7-8a9a-92b0b08658d2)
- [大型解決方案的效能考量](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)