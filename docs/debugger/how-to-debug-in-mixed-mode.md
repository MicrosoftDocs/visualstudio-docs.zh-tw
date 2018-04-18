---
title: 如何： 在混合模式偵錯 |Microsoft 文件
ms.custom: ''
ms.date: 06/19/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b39191422eeb4c808faf858fc1ef8abb9a0a41e2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-debug-in-mixed-mode"></a>How to: Debug in Mixed Mode
下列程序描述如何同時偵錯 Managed 和原生程式碼，這也稱為混合模式偵錯。 依照 DLL 或應用程式是否以機器碼撰寫而定，會有下列兩種情況：  
  
-   呼叫 DLL 的呼叫應用程式是以機器碼撰寫。 在這個情況中，您的 DLL 是 Managed，而且 Managed 和原生偵錯工具都必須啟用，才能為兩種程式碼偵錯。 您可以簽入**\<專案 > 屬性頁** 對話方塊。 不同的做法是取決於您是由 DLL 專案啟動偵錯，或者由呼叫應用程式專案啟動偵錯。  
  
-   呼叫 DLL 的呼叫應用程式是以 Managed 程式碼撰寫，而您的 DLL 是以機器碼撰寫。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

如果您沒有存取呼叫的應用程式的專案，您可以偵錯 DLL 專案的 DLL。 如需詳細資訊，請參閱 [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md)。 您不需要使用混合偵錯 DLL 專案。
  
### <a name="to-enable-mixed-mode-debugging-c-calling-app"></a>若要啟用混合模式偵錯 （c + + 呼叫應用程式）  
  
1.  在**方案總管] 中**，選取 [原生專案。
  
2.  在**檢視**功能表上，按一下 **屬性頁**。
  
3.  在**\<專案 > 屬性頁**對話方塊方塊中，展開 **組態屬性**節點，然後再選取**偵錯**。  
  
4.  設定**偵錯工具類型**至**混合**或**自動**。

    ![啟用混合的模式偵錯](../debugger/media/dbg-mixed-mode-from-native.png "啟用混合的模式偵錯")

### <a name="to-enable-mixed-mode-debugging-c-or-vb-calling-app"></a>若要啟用混合模式偵錯 （C# 或 VB 呼叫應用程式）  
  
1.  在**方案總管 中**，選取受管理的專案。  
  
2.  在**檢視**功能表上，按一下 **屬性頁**。  
  
3.  在**\<專案 > 屬性頁**對話方塊中，選取**偵錯**索引標籤，然後選取**啟用機器碼偵錯**

    ![啟用機器碼偵錯](../debugger/media/dbg-mixed-mode-from-csharp.png "啟用機器碼偵錯")
  
## <a name="see-also"></a>另請參閱  
 [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md)