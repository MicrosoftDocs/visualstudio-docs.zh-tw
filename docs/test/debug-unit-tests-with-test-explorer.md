---
title: 使用測試總管進行偵錯單元測試
description: 瞭解如何使用 Visual Studio 中的 Test Explorer 來偵測單元測試。
ms.date: 07/14/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 09889839c9e2873810c78a5f0c3425820170b68d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964377"
---
# <a name="debug-and-analyze-unit-tests-with-test-explorer"></a>使用 Test Explorer 來對單元測試進行調試和分析

您可以使用 [測試總管] 來啟動測試的偵錯工作階段。 使用 Visual Studio 偵錯工具逐步執行程式碼可讓您順暢地在單元測試和受測專案之間來回進行。 啟動偵錯：

1. 在 Visual Studio 編輯器中，於您要偵錯的一個或多個測試方法中設定中斷點。

    > [!NOTE]
    > 由於測試方法可以依照任何順序執行，請在您要偵錯的所有測試方法中設定中斷點。

::: moniker range="vs-2017"
2. 在 [測試瀏覽器] 中，選取 (s 的測試方法) 然後選擇右鍵功能表上的 [偵測 **選取的測試** ]。
::: moniker-end
::: moniker range=">=vs-2019"
2. 在 [測試瀏覽器] 中，選取 (s 的測試方法) 然後在右鍵功能表上選擇 [ **Debug** ]。

   ![測試執行詳細資料](../test/media/vs-2019/test-explorer-debug.png)
::: moniker-end

   如需偵錯工具的詳細資訊，請參閱[在 Visual Studio 中偵錯](../debugger/debugger-feature-tour.md)。

## <a name="diagnose-test-method-performance-issues"></a>診斷測試方法效能問題

::: moniker range="vs-2017"
若要診斷測試方法為何花費太多時間，請在 [測試總管] 中選取該方法，然後在右鍵功能表上選擇 [設定檔已選取測試]。 請參閱 [檢測分析報表](../profiling/understanding-instrumentation-data-values.md?view=vs-2017&preserve-view=true)。
::: moniker-end

::: moniker range=">=vs-2019"
若要診斷測試方法為何花費太多時間，請在 [測試總管] 中選取該方法，然後選擇右鍵功能表上的 [設定檔]。 請參閱 [檢測分析報表](../profiling/understanding-instrumentation-data-values.md?view=vs-2017&preserve-view=true)。
::: moniker-end

> [!NOTE]
> .NET Core 目前不支援這項功能。

## <a name="see-also"></a>另請參閱

- [對程式碼進行單元測試](../test/unit-test-your-code.md)
- [使用測試總管執行單元測試](../test/run-unit-tests-with-test-explorer.md)
- [測試清單編輯器常見問題集](test-explorer-faq.md)
