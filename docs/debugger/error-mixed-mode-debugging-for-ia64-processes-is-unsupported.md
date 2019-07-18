---
title: 錯誤：不支援混合的模式偵錯，如 IA64 處理 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c4414651249aa7622e7f7be59e6150a4925f1b8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850872"
---
# <a name="error-mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>錯誤：不支援 IA64 處理序的混合模式偵錯
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 偵錯工具不支援對 Itanium 處理序中混合的原生和 Managed 程式碼進行偵錯。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 建置 32 位元版本的應用程式以進行偵錯。

## <a name="see-also"></a>另請參閱
- [Remote Debugging](../debugger/remote-debugging.md)