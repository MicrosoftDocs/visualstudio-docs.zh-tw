---
title: 錯誤：只有使用 Microsoft .NET Framework 4 或更高版本時，才支援 x64 進程的混合模式偵錯工具 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 67b9d1c737e4490195b209abca824b2d6d51176c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737608"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>錯誤：只有使用 Microsoft .NET Framework 4 或更新版本時才支援 x64 處理序的混合模式偵錯
若要在64位進程中，對混合原生和 managed 程式碼進行偵錯工具，您必須擁有 .NET Framework 第4版。 不支援具有早于4之 .NET Framework 版本之64位進程的混合模式偵錯工具。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 請執行下列其中一個步驟：

  - 將您的 .NET Framework 升級至第4版。

  - 建置 32 位元版本的應用程式以進行偵錯。

## <a name="see-also"></a>請參閱
- [Remote Debugging](../debugger/remote-debugging.md)