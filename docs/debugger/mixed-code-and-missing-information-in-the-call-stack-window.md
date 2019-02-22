---
title: 混合程式碼和遺失的資訊，在呼叫堆疊視窗 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc43ba24e821c00adb4efb64e4785e02dae31f28
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992551"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>呼叫堆疊視窗內的混合程式碼和遺失的資訊
因為 Managed 和機器碼呼叫堆疊之間的差異，當程式碼類型混合時，偵錯工具則無法永遠顯示完整的呼叫堆疊。 當機器碼呼叫受控碼時，您會在 [呼叫堆疊] 視窗內看到下列差異：  
  
- 受控碼正上方的原生框架可能會從 [呼叫堆疊] 視窗遺失。 如需詳細資訊，請參閱[＜How to：在原生框架從 [呼叫堆疊] 視窗遺失時跳離受控碼](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md)。  
  
- 針對啟動於偵錯工具外部的混合模式應用程式，[呼叫堆疊] 視窗只會顯示受控碼，並且看不到任一個原生框架。  
  
  這兩個狀況都相當少見。 在大多數呼叫 Managed 程式碼的原生呼叫中，呼叫堆疊看起來都是正確的。  
  
## <a name="see-also"></a>請參閱  
 [如何：使用 [呼叫堆疊] 視窗](../debugger/how-to-use-the-call-stack-window.md)