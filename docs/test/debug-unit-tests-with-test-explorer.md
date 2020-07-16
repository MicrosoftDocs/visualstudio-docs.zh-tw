---
title: 使用測試瀏覽器進行單元測試的調試
description: 瞭解如何在 Visual Studio 中使用測試瀏覽器來進行單元測試的調試。
ms.date: 07/14/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2def56c6a3860ce0476f448f87bdde25c7970807
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86393475"
---
# <a name="debug-and-analyze-unit-tests-with-test-explorer"></a>使用測試瀏覽器來對單元測試進行調試和分析

您可以使用 [測試總管] 來啟動測試的偵錯工作階段。 使用 Visual Studio 偵錯工具逐步執行程式碼可讓您順暢地在單元測試和受測專案之間來回進行。 啟動偵錯：

1. 在 Visual Studio 編輯器中，於您要偵錯的一個或多個測試方法中設定中斷點。

    > [!NOTE]
    > 由於測試方法可以依照任何順序執行，請在您要偵錯的所有測試方法中設定中斷點。

::: moniker range="vs-2017"
2. 在 [測試瀏覽器] 中選取測試方法，然後選擇右鍵功能表上的 [偵測**選取的測試**]。
::: moniker-end
::: moniker range=">=vs-2019"
2. 在 [測試瀏覽器] 中選取測試方法，然後選擇右鍵功能表上的 [ **Debug** ]。

   ![測試執行詳細資料](../test/media/vs-2019/test-explorer-debug.png)
::: moniker-end

   如需偵錯工具的詳細資訊，請參閱[在 Visual Studio 中偵錯](../debugger/debugger-feature-tour.md)。

## <a name="diagnose-test-method-performance-issues"></a>診斷測試方法效能問題

::: moniker range="vs-2017"
若要診斷測試方法為何花費太多時間，請在 [測試總管] 中選取該方法，然後在右鍵功能表上選擇 [設定檔已選取測試]****。 請參閱[檢測分析報告](../profiling/understanding-instrumentation-data-values.md?view=vs-2017)。
::: moniker-end

::: moniker range=">=vs-2019"
若要診斷測試方法為何花費太多時間，請在 [測試總管] 中選取該方法，然後選擇右鍵功能表上的 [設定檔]****。 請參閱[檢測分析報告](../profiling/understanding-instrumentation-data-values.md?view=vs-2017)。
::: moniker-end

> [!NOTE]
> .NET Core 目前不支援這項功能。

## <a name="see-also"></a>另請參閱

- [對程式碼進行單元測試](../test/unit-test-your-code.md)
- [使用測試總管執行單元測試](../test/run-unit-tests-with-test-explorer.md)
- [測試清單編輯器常見問題集](test-explorer-faq.md)
