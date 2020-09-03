---
title: 錯誤-只有在使用 Microsoft .NET Framework 2.0 或更高版本時，才支援混合模式的偵錯工具 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: de19f6b735f990b0e419c040291e1bf538f680f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460620"
---
# <a name="error-mixed-mode-debugging-is-supported-only-when-using-microsoft-net-framework-20-or-greater"></a>錯誤：只有使用 Microsoft .NET Framework 2.0 或更新版本時才支援混合模式偵錯
若要對混合原生和 managed 程式碼進行偵錯工具，您必須有 .NET Framework 版本2.0、3.0。 3.5 或 4 版。 不支援使用舊版 .NET Framework 進行混合模式的偵錯工具。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 將 .NET Framework 升級為2.0、3.0、3.5 或4.0 版。

## <a name="see-also"></a>另請參閱
- [遠端偵錯](../debugger/remote-debugging.md)