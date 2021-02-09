---
title: '[呼叫堆疊] 視窗中的混合程式碼 & 遺漏資訊'
description: 在混合模式程式 (原生和 managed) 偵錯工具不一定會顯示完整的呼叫堆疊。 瞭解機器碼呼叫 managed 程式碼時的可能差異。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 793d60c9bc550b0f29ac48e50a95dab601750ad4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885101"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>呼叫堆疊視窗內的混合程式碼和遺失的資訊
因為 Managed 和機器碼呼叫堆疊之間的差異，當程式碼類型混合時，偵錯工具則無法永遠顯示完整的呼叫堆疊。 當機器碼呼叫受控碼時，您會在 [呼叫堆疊] 視窗內看到下列差異：

- 受控碼正上方的原生框架可能會從 [呼叫堆疊] 視窗遺失。 如需詳細資訊，請參閱 [如何：從 [呼叫堆疊] 視窗中遺漏原生框架時跳出 Managed 程式碼](how-to-use-the-call-stack-window.md)。

- 針對啟動於偵錯工具外部的混合模式應用程式，[呼叫堆疊] 視窗只會顯示受控碼，並且看不到任一個原生框架。

  這兩個狀況都相當少見。 在大多數呼叫 Managed 程式碼的原生呼叫中，呼叫堆疊看起來都是正確的。

## <a name="see-also"></a>另請參閱
- [如何：使用呼叫堆疊視窗](../debugger/how-to-use-the-call-stack-window.md)