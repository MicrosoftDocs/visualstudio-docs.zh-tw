---
title: "哪裡可以查看 Win32 錯誤碼？ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.errors
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 508b741dcac0662d41e58b37ecaf177a2245010f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="where-can-i-look-up-win32-error-codes"></a>哪裡可以查看 Win32 錯誤碼？
您的預設系統安裝 INCLUDE 目錄裡的 WINERROR.H 包含 Win32 API 函式的錯誤碼定義。  
  
 您可以輸入程式碼中的查閱錯誤碼**監看式**視窗或**快速監看式** 對話方塊。 例如:   
  
```  
0x80000004,hr  
```  
  
## <a name="see-also"></a>另請參閱  
 [機器碼偵錯 Faq](../debugger/debugging-native-code-faqs.md)   
 [偵錯機器碼](../debugger/debugging-native-code.md)