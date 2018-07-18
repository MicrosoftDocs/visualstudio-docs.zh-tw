---
title: 如何： 在混合模式偵錯 |Microsoft Docs
ms.custom: ''
ms.date: 06/19/2017
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 834288c063a4bc0d830f121dcb8589b509c61bcf
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256158"
---
# <a name="how-to-debug-in-mixed-mode"></a>How to: Debug in Mixed Mode
下列程序描述如何同時偵錯 Managed 和原生程式碼，這也稱為混合模式偵錯。 依照 DLL 或應用程式是否以機器碼撰寫而定，會有下列兩種情況：  
  
-   呼叫 DLL 的呼叫應用程式是以機器碼撰寫。 在這個情況中，您的 DLL 是 Managed，而且 Managed 和原生偵錯工具都必須啟用，才能為兩種程式碼偵錯。 您可以檢查這**\<專案 > 屬性頁** 對話方塊。 不同的做法是取決於您是由 DLL 專案啟動偵錯，或者由呼叫應用程式專案啟動偵錯。  
  
-   呼叫 DLL 的呼叫應用程式是以 Managed 程式碼撰寫，而您的 DLL 是以機器碼撰寫。 如需引導您完成這些步驟的教學課程，請參閱[偵錯 managed 和原生程式碼](../debugger/how-to-debug-managed-and-native-code.md)。
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

如果您沒有存取呼叫端的應用程式的專案，您可以偵錯從 DLL 專案的 DLL。 如需詳細資訊，請參閱 [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md)。 您不需要使用混合偵錯 DLL 專案。
  
### <a name="to-enable-mixed-mode-debugging-c-calling-app"></a>若要啟用混合模式偵錯 （c + + 呼叫端的應用程式）  
  
1.  在 **方案總管 中**，選取 原生專案。
  
2.  在 **檢視**功能表上，按一下**屬性頁**。
  
3.  在  **\<專案 > 屬性頁**對話方塊方塊中，展開**組態屬性**節點，然後再選取**偵錯**。  
  
4.  設定**偵錯工具類型**要**混合**或是**自動**。

    ![啟用混合的模式偵錯](../debugger/media/dbg-mixed-mode-from-native.png "啟用混合的模式偵錯")

### <a name="to-enable-mixed-mode-debugging-c-or-vb-calling-app"></a>若要啟用混合模式偵錯 （C# 或 VB 呼叫端應用程式）  
  
1.  在 **方案總管 中**，選取 受管理的專案。  
  
2.  在 **檢視**功能表上，按一下**屬性頁**。  
  
3.  在  **\<專案 > 屬性頁**對話方塊中，選取**偵錯**索引標籤，然後再選取 **啟用機器碼偵錯**

    ![啟用機器碼偵錯](../debugger/media/dbg-mixed-mode-from-csharp.png "啟用機器碼偵錯")
  
## <a name="see-also"></a>另請參閱  
 [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md)