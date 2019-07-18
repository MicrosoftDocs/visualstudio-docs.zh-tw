---
title: 哪裡可以查看 Win32 錯誤碼？ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vc.errors
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d403315a2320589f69174109d55c8726ffd5f673
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149402"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>哪裡可以查看 Win32 錯誤碼？
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您的預設系統安裝 INCLUDE 目錄裡的 WINERROR.H 包含 Win32 API 函式的錯誤碼定義。  
  
 您可以在 [監看式]  視窗或 [快速監看式]  對話方塊中鍵入程式碼來查看錯誤碼。 例如：  
  
```  
0x80000004,hr  
```  
  
## <a name="see-also"></a>另請參閱  
 [對機器碼進行偵錯的常見問題集](../debugger/debugging-native-code-faqs.md)   
 [偵錯機器碼](../debugger/debugging-native-code.md)
