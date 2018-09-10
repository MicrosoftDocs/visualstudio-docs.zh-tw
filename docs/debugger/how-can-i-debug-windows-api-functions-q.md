---
title: 如何偵錯 Windows API 函式？ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.api
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7cc765c6da62973469280e97759fbab566ca6f37
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281672"
---
# <a name="how-can-i-debug-windows-api-functions"></a>如何偵錯 Windows API 函式？
如果要偵錯已載入 NT 符號的 Windows API 函式，必須進行下列步驟。  
  
### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>若要在含載入之 NT 符號的 Windows API 函式上設定中斷點  
  
-   輸入加上函式所在 DLL 名稱的函式名稱。 在 32 位元程式碼中，請使用函式名稱的裝飾形式。 若要設定中斷點**MessageBeep**，比方說，您必須輸入下列。  
  
    ```cpp
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     若要取得裝飾的名稱，請參閱[檢視裝飾名稱](https://msdn.microsoft.com/library/f79e2717-a4db-4d12-a689-69830cce2be0)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯機器碼常見問題集](../debugger/debugging-native-code-faqs.md)   
 [偵錯機器碼](../debugger/debugging-native-code.md)
