---
title: 如何偵錯 Windows API 函式？ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.api
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d7729782fe23c1404aa6862116e884baa97b17f5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60103591"
---
# <a name="how-can-i-debug-windows-api-functions"></a>如何偵錯 Windows API 函式？
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果要偵錯已載入 NT 符號的 Windows API 函式，必須進行下列步驟。  
  
### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>若要在含載入之 NT 符號的 Windows API 函式上設定中斷點  
  
- 輸入加上函式所在 DLL 名稱的函式名稱。 在 32 位元程式碼中，請使用函式名稱的裝飾形式。 例如，若要在 **MessageBeep** 上設定中斷點，您必須輸入下列程式碼。  
  
    ```  
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     若要取得裝飾的名稱，請參閱[檢視裝飾名稱](http://msdn.microsoft.com/f79e2717-a4db-4d12-a689-69830cce2be0)。  
  
## <a name="see-also"></a>另請參閱  
 [對機器碼進行偵錯的常見問題集](../debugger/debugging-native-code-faqs.md)   
 [偵錯機器碼](../debugger/debugging-native-code.md)
