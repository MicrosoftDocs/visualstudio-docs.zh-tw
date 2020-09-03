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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655142"
---
# <a name="automatic-feature-suspension"></a>自動功能暫停
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
如果可用的系統記憶體降至200MB 或更少，Visual Studio 會在程式碼編輯器中顯示下列訊息。

 ![警示文字暫停完整解決方案分析](../code-quality/media/fsa-alert.png "FSA_Alert")

 當 Visual Studio 偵測到記憶體不足的狀況時，它會自動暫停特定的 advanced 功能，以協助它維持穩定狀態。 當此 [advanced feature 擱置] 警告出現時，Visual Studio 將繼續正常運作，但其效能會稍微降級。

 在記憶體不足的情況下，會發生下列情況：

- Visual c # 和 Visual Basic 的完整解決方案分析已停用。

- [垃圾收集](https://msdn.microsoft.com/library/22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9) (GC) 適用于 Visual c # 和 Visual Basic 的低延遲模式已停用。

- Visual Studio 快取排清。

## <a name="improve-visual-studio-performance"></a>改善 Visual Studio 效能
 如需如何在處理大型解決方案或記憶體不足的狀況時改善 Visual Studio 效能的秘訣和訣竅，請參閱 [大型方案的效能考慮](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)。

## <a name="full-solution-analysis-suspended"></a>完整解決方案分析已暫停
 根據預設，會為 Visual Basic 啟用完整的解決方案分析，並且針對 Visual c # 停用。 不過，在記憶體不足的情況下，無論在 [選項] 對話方塊中的設定為何，都會自動停用 Visual Basic 和 Visual c # 的完整解決方案分析。 不過，您可以在 [選項] 對話方塊中 **選取 [** **啟用完整解決方案分析** ] 核取方塊，或重新開機 Visual Studio，藉以重新啟用完整的解決方案分析。 [選項] 對話方塊一律會顯示目前的完整方案分析設定。 如需詳細資訊，請參閱 [如何：啟用和停用完整解決方案分析](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)。

## <a name="gc-low-latency-disabled"></a>GC 低延遲已停用
 若要重新啟用 GC 低延遲模式，請重新開機 Visual Studio。  根據預設，每當您輸入時，Visual Studio 都會啟用 GC 低延遲模式，以確保您的輸入不會封鎖任何 GC 作業。 但是，如果記憶體不足的狀況導致 Visual Studio 顯示自動暫止警告，則會停用該會話的 GC 低延遲模式。 重新開機 Visual Studio 將會重新啟用預設 GC 行為。 如需詳細資訊，請參閱<xref:System.Runtime.GCLatencyMode>。

## <a name="visual-studio-caches-flushed"></a>Visual Studio 快取排清

所有 Visual Studio 快取都會立即清空，但如果您繼續目前的開發會話或重新開機 Visual Studio，就會開始重新擴展。 快取的快取包含下列功能的快取。

- 尋找所有參考

- 巡覽至

- 新增使用

此外，也會清除用於內部 Visual Studio 操作的快取。

> [!NOTE]
> 自動功能暫止警告只會在每個解決方案上進行一次，而不會以每個會話為基礎。 這表示，如果您從 Visual Basic 切換至 Visual c # (或反向) ，並在另一個記憶體不足的情況下執行，您可能會收到另一個自動功能暫停警告。

## <a name="see-also"></a>另請參閱

- [如何：啟用和停用完整解決方案分析](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Fundamentals of Garbage Collection (記憶體回收的基本概念)](https://msdn.microsoft.com/library/67c5a20d-1be1-4ea7-8a9a-92b0b08658d2)
- [大型解決方案的效能考慮](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)