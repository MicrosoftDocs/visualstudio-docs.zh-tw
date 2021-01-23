---
title: 使用效能規則分析資料 | Microsoft Docs
description: 瞭解 Visual Studio 分析工具的效能警告指出程式碼剖析的應用程式中，可能會使程式執行變慢的問題。
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1deed23e-b31b-4714-982f-08ceebfc3096
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9a896e128f949897b64fd6a273784f39543a9663
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721134"
---
# <a name="use-performance-rules-to-analyze-data"></a>使用效能規則分析資料
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具的效能警告指出，正在進行程式碼剖析的應用程式中發生問題，可能會降低程式執行速度。 警告也可能表示您可能需要變更收集方法，以收集更有用的資料。 效能警告會在程式碼剖析工作階段中自動產生。 在 Visual Studio 中開啟程式碼剖析資料檔案時，警告會出現在 [錯誤清單] 視窗中。 您可以在 [錯誤清單] 視窗中找到問題的原始程式碼，並可以顯示有關錯誤的詳細資訊，例如有關如何解決問題的資訊。 您也可以將您不想要的警告停用。

> [!NOTE]
> 分析工具效能警告是由程式執行的動態分析所產生，並且和程式碼分析警告無關。 程式碼分析也可以根據原始程式碼的靜態分析，來產生 Managed 程式碼的效能警告。 如需詳細資訊，請參閱[分析受控程式碼品質](../code-quality/code-analysis-for-managed-code-overview.md)和[效能警告](/dotnet/fundamentals/code-analysis/quality-rules/performance-warnings)。

## <a name="in-this-section"></a>本節內容
- [如何：查看效能警告](../profiling/how-to-view-performance-warnings.md)

 提供如何開啟 [錯誤清單] 視窗以檢視分析工具效能警告的相關資訊。

- [如何：設定效能規則](../profiling/how-to-configure-performance-rules.md)

 提供如何將個別效能警告開啟或關閉的相關資訊。

- [效能規則參考](../profiling/performance-rules-reference.md)

 提供有關分析工具效能警告的詳細資訊
