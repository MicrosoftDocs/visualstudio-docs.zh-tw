---
title: 執行偵錯工具之外的應用程式時，偵錯存取違規 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 42284de1195afb3b0926b15335c8e37bdcd5ec30
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "53048472"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>在偵錯工具外執行我的程式時，如何偵錯存取違規？

## <a name="problem-description"></a>問題說明  
 我的程式在 Visual Studio 環境裡執行正常，但是當我以 Windows 作業系統獨立執行它時，它會產生存取違規。 我該如何偵錯這個問題？  
  
## <a name="solution"></a>方案  
 設定 [ 偵錯](../debugger/just-in-time-debugging-in-visual-studio.md)選項並獨立執行您的程式，直到發生存取違規為止。 然後，在 [存取違規] 對話方塊中，您可以按一下 [取消] 來啟動偵錯工具。  
  
## <a name="see-also"></a>請參閱  
 [對機器碼進行偵錯的常見問題集](../debugger/debugging-native-code-faqs.md)   
 [偵錯機器碼](../debugger/debugging-native-code.md)