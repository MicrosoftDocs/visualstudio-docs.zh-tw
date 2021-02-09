---
title: 自動功能暫停
ms.date: 11/04/2016
description: 瞭解 Visual Studio 如何減少分析範圍、關閉垃圾收集低延遲模式，以及在系統記憶體有限時清除快取。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: efd053a846a7bf70f475db44788b14152498dc0b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99843718"
---
# <a name="automatic-feature-suspension"></a>自動功能暫停

如果可用的系統記憶體低於 200 MB 或更少，Visual Studio 在程式碼編輯器中顯示下列訊息：

![警示文字暫停完整解決方案分析](../code-quality/media/fsa_alert.png)

當 Visual Studio 偵測到記憶體不足的狀況時，它會自動暫停特定的 advanced 功能，以協助它維持穩定狀態。 Visual Studio 會繼續正常運作，但其效能會降低。

在記憶體不足的情況下，會發生下列動作：

- Visual c # 和 Visual Basic 的即時程式碼分析會縮減為基本範圍。

- 已停用 Visual c # 和 Visual Basic 的[垃圾收集](/dotnet/standard/garbage-collection/index) (GC) 低延遲模式。

- Visual Studio 快取排清。

## <a name="improve-visual-studio-performance"></a>改善 Visual Studio 效能

如需如何在處理大型解決方案或記憶體不足的狀況時改善 Visual Studio 效能的秘訣和訣竅，請參閱 [大型方案的效能考慮](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md)。

## <a name="live-code-analysis-is-reduced-to-minimal-scope"></a>即時程式碼分析縮減至基本範圍

依預設，即時程式碼分析會針對開啟的檔和專案執行。 您可以自訂此分析範圍，以縮減為目前的檔或增加至整個方案。 如需詳細資訊，請參閱 [如何：設定 managed 程式碼的即時程式碼分析範圍](./configure-live-code-analysis-scope-managed-code.md)。 在記憶體不足的情況下，Visual Studio 會強制將即時分析範圍縮減為目前的檔。 不過，您可以在出現或重新開機 Visual Studio 時，選擇資訊列中的 [ **重新啟用** ] 按鈕，以重新啟用您慣用的分析範圍。 [選項] 對話方塊一律會顯示目前的即時程式碼分析範圍設定。

## <a name="gc-low-latency-disabled"></a>GC 低延遲已停用

若要重新啟用 GC 低延遲模式，請重新開機 Visual Studio。 根據預設，每當您輸入時，Visual Studio 都會啟用 GC 低延遲模式，以確保您的輸入不會封鎖任何 GC 作業。 但是，如果記憶體不足的狀況導致 Visual Studio 顯示自動暫止警告，則會停用該會話的 GC 低延遲模式。 重新開機 Visual Studio 重新啟用預設 GC 行為。 如需詳細資訊，請參閱<xref:System.Runtime.GCLatencyMode>。

## <a name="visual-studio-caches-flushed"></a>Visual Studio 快取排清

如果您繼續目前的開發會話或重新開機 Visual Studio，則會立即清空所有 Visual Studio 快取，但開始重新擴展。 快取的快取包含下列功能的快取：

- 尋找所有參考

- 巡覽至

- 新增使用

此外，也會清除用於內部 Visual Studio 操作的快取。

> [!NOTE]
> 自動功能暫止警告只會在每個解決方案上進行一次，而不會以每個會話為基礎。 這表示，如果您從 Visual Basic 切換至 Visual c # (或反向) ，並在另一個記憶體不足的情況下執行，您可能會收到另一個自動功能暫停警告。

## <a name="see-also"></a>另請參閱

- [如何：設定 managed 程式碼的即時程式碼分析範圍](./configure-live-code-analysis-scope-managed-code.md)
- [Fundamentals of Garbage Collection (記憶體回收的基本概念)](/dotnet/standard/garbage-collection/fundamentals)
- [大型解決方案的效能考慮](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md)
