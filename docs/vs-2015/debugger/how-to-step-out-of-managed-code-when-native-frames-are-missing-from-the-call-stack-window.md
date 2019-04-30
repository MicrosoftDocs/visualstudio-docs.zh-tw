---
title: HOW TO：原生框架遺失於呼叫堆疊視窗時跳離 Managed 程式碼 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1672ba8e6bcf66973a5cd32be3fb03821750e3f2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442740"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>HOW TO：在原生框架從呼叫堆疊視窗遺失時跳離受控程式碼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果程式碼擁有在 [呼叫堆疊] 視窗中不可見的原生框架，跳離受控程式碼函式可以產生未預期的結果。 您可使用中斷點，而不要使用 [跳離函式]，便可解決這個問題。  
  
> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>若要在原生框架遺失於呼叫堆疊顯示時跳離 Managed 程式碼  
  
1. 在機器碼中，請在呼叫 Managed 程式碼之後設定一個位置中斷點。  
  
2. 選擇 [偵錯] 功能表上的 [繼續]。  
  
     完成 Managed 呼叫之後，執行將停止於機器碼的中斷點處。  
  
## <a name="see-also"></a>另請參閱  
 [如何：使用 [呼叫堆疊] 視窗](../debugger/how-to-use-the-call-stack-window.md)
