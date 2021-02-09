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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 01f8bf0b018ed5dd91cedcc221a037f3502815e7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871490"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>錯誤：只有使用 Microsoft .NET Framework 4 或更新版本時才支援 x64 處理序的混合模式偵錯
若要在64位進程中偵測混合原生和 managed 程式碼，您必須有 .NET Framework 第4版。 不支援以4之前的 .NET Framework 版本進行64位進程的混合模式調試。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 請執行下列其中一個步驟：

  - 將您的 .NET Framework 升級至第4版。

  - 建置 32 位元版本的應用程式以進行偵錯。

## <a name="see-also"></a>另請參閱
- [遠端偵錯](../debugger/remote-debugging.md)