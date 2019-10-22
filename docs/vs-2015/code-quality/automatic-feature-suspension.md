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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b9c80ba76ba2da978c9cb475299ba0fc9e614120
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655142"
---
# <a name="automatic-feature-suspension"></a>自動功能暫停
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
如果可用的系統記憶體低於 200 MB 或更少，Visual Studio 會在程式碼編輯器中顯示下列訊息。

 ![暫停完整解決方案分析的警示文字](../code-quality/media/fsa-alert.png "FSA_Alert")

 當 Visual Studio 偵測到記憶體不足的狀況時，它會自動暫停特定的「先進的功能」，協助它保持穩定。 當此 [高級功能擱置] 警告出現時，Visual Studio 會繼續如之前一樣使用，但其效能會稍微降低。

 在記憶體不足的情況下，會發生下列情況：

- 已停用 Visual C#和 Visual Basic 的完整解決方案分析。

- 視覺效果C#和 Visual Basic 的[垃圾收集](https://msdn.microsoft.com/library/22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9)（GC）低延遲模式已停用。

- Visual Studio 快取會排清。

## <a name="improve-visual-studio-performance"></a>改善 Visual Studio 效能
 如需如何在處理大型解決方案或記憶體不足的情況下改善 Visual Studio 效能的秘訣和訣竅，請參閱[大型解決方案的效能考慮](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)。

## <a name="full-solution-analysis-suspended"></a>已暫停完整解決方案分析
 根據預設，會啟用 Visual Basic 的完整解決方案分析，並針對視覺C#效果停用。 不過，在記憶體不足的情況下，不論其在 [選項] 對話方塊中的設定C#為何，皆會自動停用 Visual Basic 和視覺效果的完整解決方案分析。 不過，您可以在顯示的資訊列中選擇 [**重新啟用**] 按鈕、選取 [選項] 對話方塊中的 [**啟用完整解決方案分析**] 核取方塊，或重新開機 Visual Studio，以重新啟用完整的解決方案分析。 [選項] 對話方塊一律會顯示目前的完整解決方案分析設定。 如需詳細資訊，請參閱[如何：啟用和停用完整解決方案分析](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)。

## <a name="gc-low-latency-disabled"></a>停用 GC 低延遲
 若要重新啟用 GC 低延遲模式，請重新開機 Visual Studio。  根據預設，每當您輸入時，Visual Studio 都會啟用 GC 低延遲模式，以確保您的輸入不會封鎖任何 GC 作業。 不過，如果記憶體不足的狀況導致 Visual Studio 顯示自動暫停警告，則會停用該會話的 GC 低延遲模式。 重新開機 Visual Studio 將會重新啟用預設的 GC 行為。 如需詳細資訊，請參閱<xref:System.Runtime.GCLatencyMode>。

## <a name="visual-studio-caches-flushed"></a>已排清 Visual Studio 快取

所有 Visual Studio 快取都會立即清空，但如果您繼續目前的開發會話或重新開機 Visual Studio，則會開始重新擴展。 已排清的快取包含下列功能的快取。

- 尋找所有參考

- 巡覽至

- 新增使用

此外，也會清除用於內部 Visual Studio 作業的快取。

> [!NOTE]
> 自動功能暫止警告只會針對每個解決方案執行一次，而不會以每個會話為基礎。 這表示如果您從 Visual Basic 切換到視覺效果C# （反之亦然）並遇到另一個記憶體不足的狀況，您可能會收到另一個自動功能暫停警告。

## <a name="see-also"></a>請參閱

- [如何：啟用和停用完整解決方案分析](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [記憶體回收的基本概念](https://msdn.microsoft.com/library/67c5a20d-1be1-4ea7-8a9a-92b0b08658d2)
- [大型解決方案的效能考慮](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)