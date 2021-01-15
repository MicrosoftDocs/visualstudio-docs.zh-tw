---
title: 使用原生 Run-Time 檢查 |Microsoft Docs
description: 使用 Visual Studio 中的原生執行時間檢查來攔截常見的執行階段錯誤，例如堆疊指標損毀、本機陣列的溢出和堆疊損毀。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- c.runtime.errorchecks
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- /RTC compiler option [C++], /O compiler option
- run-time checks, native
- stack, pointer corruption
- stack pointers, corruption
- /O compiler option, /RTC option
- run-time errors, error checks
- O compiler option, /RTC option
- debugger, runtime errors
- variables [debugger], loss of data
- runtime_checks pragma
- variables [debugger], catching dependencies on uninitialized local variables
- run-time errors, debugging
- debugger, native run-time checks
- optimized build option
- RTC compiler option, /O compiler option
- native run-time checks
- run-time checks
- debugging arrays
- stack pointers
- arrays [Visual Studio], debugging
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 70f047fa84513821812a13f7dee3136d2d431d9a
ms.sourcegitcommit: 993fca11dc373a10150751bc2a045a9701a9db2f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2021
ms.locfileid: "98240240"
---
# <a name="how-to-use-native-run-time-checks"></a>如何：使用原生執行階段檢查
在 Visual Studio c + + 專案中，您可以使用原生 [runtime_checks](/cpp/preprocessor/runtime-checks) 來攔截常見的執行階段錯誤，例如：

- 堆疊指標損壞

- 區域陣列滿溢

- 堆疊損壞

- 未初始化之區域變數的相依性

- 指派至較短變數時流失資料

  如果使用具有最佳化 ( **/O** ) 組建的 **/RTC**，便會造成編譯器錯誤。 如果您在最佳化組建中使用 `runtime_checks` Pragma，此 Pragma 會失效。

  如果要偵錯的程式已啟用執行階段錯誤檢查，則當這個程式發生執行階段錯誤時，預設動作是停止和中斷偵錯工具。 您可以變更任何執行階段檢查的這個預設行為。 如需詳細資訊，請參閱 [使用偵錯工具管理例外](../debugger/managing-exceptions-with-the-debugger.md)狀況。

  下列程序描述如何在偵錯組建中啟用原生執行階段檢查，以及如何修改原生執行階段檢查行為。

  本節的其他主題提供下列資訊：

- [自訂使用 C 語言執行階段程式庫的執行階段檢查](../debugger/native-run-time-checks-customization.md)

### <a name="to-enable-native-run-time-checks-in-a-debug-build"></a>在偵錯組建中啟用原生的執行階段檢查

- 使用 **/RTC** 選項，並與 C 語言執行階段程式庫的偵錯版本建立連結 (例如 /MDd)。

### <a name="to-modify-native-run-time-check-behavior"></a>修改原生的執行階段檢查行為

- 使用 `runtime_checks` Pragma。

## <a name="see-also"></a>另請參閱
- [Visual Studio 偵錯](../debugger/index.yml)
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)
- [runtime_checks](/cpp/preprocessor/runtime-checks)
- [執行階段錯誤檢查](/cpp/c-runtime-library/run-time-error-checking)