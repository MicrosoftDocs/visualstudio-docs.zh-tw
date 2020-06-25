---
title: Debug Windows API 函式 |Microsoft Docs
ms.custom: seodec18
ms.date: 06/03/2020
ms.topic: how-to
f1_keywords:
- vs.debug.api
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6fab5627f3d467c0df289969e4fee010dd3ea78b
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350390"
---
# <a name="how-can-i-debug-windows-api-functions"></a>如何偵錯 Windows API 函式？
如果要偵錯已載入 NT 符號的 Windows API 函式，必須進行下列步驟。

### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>若要在含載入之 NT 符號的 Windows API 函式上設定中斷點

- 在函式[中斷點](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)中，輸入函式名稱並加上函式所在的 DLL 名稱（請參閱[內容運算子](../debugger/context-operator-cpp.md)）。 在 32 位元程式碼中，請使用函式名稱的裝飾形式。 例如，若要在 **MessageBeep** 上設定中斷點，您必須輸入下列程式碼。

    ```cpp
    {,,USER32.DLL}_MessageBeep@4
    ```

     若要取得裝飾名稱，請參閱[查看裝飾名稱](https://msdn.microsoft.com/library/f79e2717-a4db-4d12-a689-69830cce2be0)。

     您可以測試裝飾名稱，並在反組解碼程式碼中加以查看。 在 Visual Studio 偵錯工具的函式中暫停時，以滑鼠右鍵按一下 [程式碼編輯器] 或 [呼叫堆疊] 視窗中的函式，然後選擇 [**移至**反組解碼]。

- 在64位程式碼中，您可以使用未修飾的名稱。

    ```cpp
    {,,USER32.DLL}MessageBeep
    ```

## <a name="see-also"></a>另請參閱
- [機器碼偵錯 FAQ](../debugger/debugging-native-code-faqs.md)
- [偵錯機器碼](../debugger/debugging-native-code.md)
