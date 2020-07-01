---
title: 自動功能暫停
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 236a95cd8d4af8da91199bf79e7c9fe3aa0d49af
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769487"
---
# <a name="automatic-feature-suspension"></a>自動功能暫停

如果可用的系統記憶體低於 200 MB 或更少，Visual Studio 會在程式碼編輯器中顯示下列訊息：

![暫停完整解決方案分析的警示文字](../code-quality/media/fsa_alert.png)

當 Visual Studio 偵測到記憶體不足的狀況時，它會自動暫停特定的「先進的功能」，協助它保持穩定。 Visual Studio 會繼續如之前一樣運作，但其效能已降低。

在記憶體不足的情況下，會發生下列動作：

- Visual c # 和 Visual Basic 的即時程式碼分析會縮減為最小範圍。

- Visual c # 和 Visual Basic 的[垃圾收集](/dotnet/standard/garbage-collection/index)（GC）低延遲模式已停用。

- Visual Studio 快取會排清。

## <a name="improve-visual-studio-performance"></a>改善 Visual Studio 效能

如需如何在處理大型解決方案或記憶體不足的情況下改善 Visual Studio 效能的秘訣和訣竅，請參閱[大型解決方案的效能考慮](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)。

## <a name="live-code-analysis-is-reduced-to-minimal-scope"></a>即時程式碼分析縮減為最小範圍

根據預設，即時程式碼分析會針對開啟的檔和專案執行。 您可以自訂此分析範圍，使其縮減為目前的檔或增加至整個解決方案。 如需詳細資訊，請參閱[如何：設定受控碼的即時程式碼分析範圍](./configure-live-code-analysis-scope-managed-code.md)。 在記憶體不足的情況下，Visual Studio 強制將即時分析範圍縮減為目前的檔。 不過，您可以在顯示的資訊列中選擇 [**重新啟用**] 按鈕，或重新開機 Visual Studio，以重新啟用慣用的分析範圍。 [選項] 對話方塊一律會顯示目前的即時程式碼分析範圍設定。

## <a name="gc-low-latency-disabled"></a>停用 GC 低延遲

若要重新啟用 GC 低延遲模式，請重新開機 Visual Studio。 根據預設，每當您輸入時，Visual Studio 都會啟用 GC 低延遲模式，以確保您的輸入不會封鎖任何 GC 作業。 不過，如果記憶體不足的狀況導致 Visual Studio 顯示自動暫停警告，則會停用該會話的 GC 低延遲模式。 重新開機 Visual Studio 重新啟用預設的 GC 行為。 如需詳細資訊，請參閱 <xref:System.Runtime.GCLatencyMode> 。

## <a name="visual-studio-caches-flushed"></a>已排清 Visual Studio 快取

如果您繼續目前的開發會話或重新開機 Visual Studio，所有 Visual Studio 快取都會立即清空，但會開始重新擴展。 已排清的快取包含下列功能的快取：

- 尋找所有參考

- 巡覽至

- 新增使用

此外，也會清除用於內部 Visual Studio 作業的快取。

> [!NOTE]
> 自動功能暫止警告只會針對每個解決方案執行一次，而不會以每個會話為基礎。 這表示如果您從 Visual Basic 切換至 Visual c # （或相反），並遇到另一個記憶體不足的狀況，您可能會收到另一個自動功能擱置警告。

## <a name="see-also"></a>另請參閱

- [如何：設定受控碼的即時程式碼分析範圍](./configure-live-code-analysis-scope-managed-code.md)
- [Fundamentals of Garbage Collection (記憶體回收的基本概念)](/dotnet/standard/garbage-collection/fundamentals)
- [大型解決方案的效能考慮](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
