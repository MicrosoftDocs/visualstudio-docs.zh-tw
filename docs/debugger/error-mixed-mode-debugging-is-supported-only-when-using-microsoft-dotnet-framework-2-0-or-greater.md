---
title: 錯誤：只有使用 Microsoft .NET Framework 2.0 或更高版本時，才支援混合模式的調試 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_to_old
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
ms.openlocfilehash: c85dac85146c59d8aeba9f9cf85351b5bc17a81c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737617"
---
# <a name="error-mixed-mode-debugging-is-supported-only-when-using-microsoft-net-framework-20-or-greater"></a>錯誤：只有使用 Microsoft .NET Framework 2.0 或更新版本時才支援混合模式偵錯
若要對混合的原生和 managed 程式碼進行偵錯工具，您必須擁有 .NET Framework 版本2.0，3.0。 3.5 或 4 版。 不支援使用舊版 .NET Framework 進行混合模式的調試。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 將 .NET Framework 升級至2.0、3.0、3.5 或4.0 版。

## <a name="see-also"></a>請參閱
- [Remote Debugging](../debugger/remote-debugging.md)