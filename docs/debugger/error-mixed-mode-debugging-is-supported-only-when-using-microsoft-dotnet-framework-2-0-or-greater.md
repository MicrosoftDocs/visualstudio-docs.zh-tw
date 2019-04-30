---
title: 錯誤：只有在使用 Microsoft.NET Framework 2.0 或更新混合的模式偵錯支援 |Microsoft Docs
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
ms.openlocfilehash: 2fb4d0dfaeb944700757c9ceec222dbd62dab9dd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850677"
---
# <a name="error-mixed-mode-debugging-is-supported-only-when-using-microsoft-net-framework-20-or-greater"></a>錯誤：只有使用 Microsoft .NET Framework 2.0 或更新版本時才支援混合模式偵錯
若要混合偵錯機器碼和 Managed 程式碼，您必須要有 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0、3.0、 3.5 或 4 版。 不支援以更舊版本的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 進行混合模式偵錯。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 將 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 升級為 2.0、3.0、3.5 或 4 版。

## <a name="see-also"></a>另請參閱
- [Remote Debugging](../debugger/remote-debugging.md)