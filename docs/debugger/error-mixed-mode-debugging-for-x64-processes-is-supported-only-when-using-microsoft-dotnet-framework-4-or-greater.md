---
title: 只有使用 Microsoft .NET Framework 4 或更新版本時，才支援 x64 進程的混合模式偵錯工具 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: e8cfc3ac5cb606637fe5c2818750168a239a46fa
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852611"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>錯誤：只有使用 Microsoft .NET Framework 4 或更新版本時才支援 x64 處理序的混合模式偵錯
若要在64位進程中偵測混合原生和 managed 程式碼，您必須有 .NET Framework 第4版。 不支援以4之前的 .NET Framework 版本進行64位進程的混合模式調試。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 請執行下列其中一個步驟：

  - 將您的 .NET Framework 升級至第4版。

  - 建置 32 位元版本的應用程式以進行偵錯。

## <a name="see-also"></a>另請參閱
- [遠端偵錯](../debugger/remote-debugging.md)