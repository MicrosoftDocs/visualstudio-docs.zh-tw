---
title: 錯誤：混合模式偵錯的處理程序只有在使用 Microsoft.NET Framework 4 時，才支援的 x64 或更新版本 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e4b0216c-7006-4832-883f-08e982ba8d3f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 56ae0260b73d41e953fa25b74eae9b012604258a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60106327"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>錯誤：只有使用 Microsoft .NET Framework 4 或更新版本時才支援 x64 處理序的混合模式偵錯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要對 64 位元處理序中混合的原生和 Managed 程式碼進行偵錯，必須具備 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4 版。 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4 (含) 以前版本不支援 64 位元處理序的混合模式偵錯。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請執行下列其中一個步驟：  
  
    - 將 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 升級為 4 版。  
  
    - 建置 32 位元版本的應用程式以進行偵錯。  
  
## <a name="see-also"></a>另請參閱  
 [在裝置上設定遠端工具](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
