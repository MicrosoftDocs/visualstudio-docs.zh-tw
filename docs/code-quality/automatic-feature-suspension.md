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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8480eb57a08905c2a593adbab519ae793638888
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431237"
---
# <a name="automatic-feature-suspension"></a>自動功能暫停

如果可用的系統記憶體降至 200 MB 或更少，Visual Studio 會在代碼編輯器中顯示以下消息：

![警報文本暫停完整的解決方案分析](../code-quality/media/fsa_alert.png)

當 Visual Studio 檢測到記憶體不足時，它會自動掛起某些高級功能，以説明其保持穩定。 Visual Studio 繼續像以前那樣工作，但其性能下降。

在記憶體不足的情況下，將執行以下操作：

- Visual C++ 和視覺化基本的即時代碼分析被縮小到最小範圍。

- 禁用了 Visual C++ 和視覺化基本版的[垃圾回收](/dotnet/standard/garbage-collection/index)（GC） 低延遲模式。

- 視覺化工作室緩存被刷新。

## <a name="improve-visual-studio-performance"></a>提高視覺工作室性能

有關在處理大型解決方案或記憶體不足條件時如何提高 Visual Studio 性能的提示和技巧，請參閱[大型解決方案的性能注意事項](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)。

## <a name="live-code-analysis-is-reduced-to-minimal-scope"></a>即時代碼分析減少到最小範圍

預設情況下，對打開的文檔和專案執行即時代碼分析。 您可以自訂此分析範圍以簡化為當前文檔或增加到整個解決方案。 有關詳細資訊，請參閱[如何：為託管代碼配置即時代碼分析範圍](./configure-live-code-analysis-scope-managed-code.md)。 在記憶體不足的情況下，Visual Studio 強制將即時分析範圍縮減為當前文檔。 但是，您可以通過在資訊列中選擇"在資訊列中**重新啟用**"按鈕時重新啟用該按鈕或重新開機 Visual Studio 來重新啟用首選分析範圍。 "選項"對話方塊始終顯示當前即時代碼分析範圍設置。

## <a name="gc-low-latency-disabled"></a>禁用 GC 低延遲

要重新啟用 GC 低延遲模式，請重新開機 Visual Studio。 預設情況下，視覺化工作室在鍵入時啟用 GC 低延遲模式，以確保鍵入不會阻止任何 GC 操作。 但是，如果記憶體不足導致 Visual Studio 顯示自動掛起警告，則該會話將禁用 GC 低延遲模式。 重新開機視覺化工作室可重新啟用預設 GC 行為。 如需詳細資訊，請參閱 <xref:System.Runtime.GCLatencyMode>。

## <a name="visual-studio-caches-flushed"></a>視覺化工作室緩存已刷新

如果繼續當前開發會話或重新開機 Visual Studio，則所有 Visual Studio 緩存將立即清空，但開始重新填充。 刷新的緩存包括以下功能的緩存：

- 尋找所有參考

- 巡覽至

- 使用添加

此外，還清除了用於內部視覺化工作室操作的緩存。

> [!NOTE]
> 自動功能掛起警告僅按每個解決方案發生一次，而不是基於每個會話。 這意味著，如果您從 Visual Basic 切換到 Visual C++（反之亦然），並遇到另一個記憶體不足的情況，則可能會收到另一個自動功能掛起警告。

## <a name="see-also"></a>另請參閱

- [如何：為託管代碼配置即時代碼分析範圍](./configure-live-code-analysis-scope-managed-code.md)
- [Fundamentals of Garbage Collection (記憶體回收的基本概念)](/dotnet/standard/garbage-collection/fundamentals)
- [大型解決方案的性能注意事項](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
