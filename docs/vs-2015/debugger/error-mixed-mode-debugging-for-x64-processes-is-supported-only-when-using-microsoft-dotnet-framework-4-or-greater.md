---
title: 錯誤： 混合模式偵錯的處理程序只有在使用 Microsoft.NET Framework 4 時，才支援的 x64 或更新版本 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e4b0216c-7006-4832-883f-08e982ba8d3f
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 479a771300e37e09412accb16771d31454469f95
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488227"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>錯誤：只有使用 Microsoft .NET Framework 4 或更新版本時才支援 x64 處理序的混合模式偵錯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[錯誤： 混和模式偵錯的處理程序只有在使用 Microsoft.NET Framework 4 時，才支援的 x64 或更高](https://docs.microsoft.com/visualstudio/debugger/error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-dotnet-framework-4-or-greater)。  
  
若要對 64 位元處理序中混合的原生和 Managed 程式碼進行偵錯，必須具備 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4 版。 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4 (含) 以前版本不支援 64 位元處理序的混合模式偵錯。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請執行下列其中一個步驟：  
  
    -   將 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 升級為 4 版。  
  
    -   建置 32 位元版本的應用程式以進行偵錯。  
  
## <a name="see-also"></a>另請參閱  
 [在裝置上設定遠端工具](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)



