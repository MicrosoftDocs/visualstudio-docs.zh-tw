---
title: 錯誤：混合模式偵錯的處理程序只有在使用 Microsoft.NET Framework 4 時，才支援的 x64 或更新版本 |Microsoft Docs
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
ms.openlocfilehash: 61c92460976ec9b95163b83744ee0b01b6ebc572
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986081"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>錯誤：只有使用 Microsoft .NET Framework 4 或更新版本時才支援 x64 處理序的混合模式偵錯
若要對 64 位元處理序中混合的原生和 Managed 程式碼進行偵錯，必須具備 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4 版。 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4 (含) 以前版本不支援 64 位元處理序的混合模式偵錯。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請執行下列其中一個步驟：  
  
  - 將 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 升級為 4 版。  
  
  - 建置 32 位元版本的應用程式以進行偵錯。  
  
## <a name="see-also"></a>請參閱  
 [Remote Debugging](../debugger/remote-debugging.md)