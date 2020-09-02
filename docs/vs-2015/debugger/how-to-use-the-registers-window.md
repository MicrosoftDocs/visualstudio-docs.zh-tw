---
title: 如何：使用暫存器視窗 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.registers
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 233092af638824c462a6d9a47865a1c6f5fd9397
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697471"
---
# <a name="how-to-use-the-registers-window"></a>如何：使用暫存器視窗
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

只有在透過 [選項]**** 對話方塊 [一般]**** 分類的 [偵錯]**** 節點啟用位址層級偵錯時，才可以使用 [暫存器] 視窗。  
  
 [ **緩存** 器] 視窗會顯示暫存器內容。 當您逐步執行程式 **時，如果您讓 [緩存** 器] 視窗保持開啟，您可以在程式碼執行時看到登錄值變更。 最近變更過的值以紅色顯示。 您可以編輯暫存器值。 如需詳細資訊，請參閱 [如何：編輯](../debugger/how-to-edit-a-register-value.md)暫存器值。  
  
 為了減少雜亂的情況，[暫存器]**** 視窗會依據平台和處理器類型，將暫存器分為不同的群組。 您可以視需要顯示或隱藏群組。 如需詳細資訊，請參閱 [如何：顯示和隱藏](../debugger/how-to-display-and-hide-register-groups.md)暫存器群組。  
  
 如需 [暫存器] 和 [暫存器] 視窗背後概念的高階簡介，請參閱 [偵錯工具基本概念：](../debugger/debugging-basics-registers-window.md)暫存器視窗。  
  
> [!NOTE]
> 您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。 若要變更您的設定，請在 [工具]**** 功能表上選擇 [匯入和匯出設定]****。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### <a name="to-display-the-registers-window"></a>若要顯示暫存器視窗  
  
- 在 [ **調試** ] 功能表上，選擇 [ **視窗**]，然後選擇 [ **註冊**]。  
  
     偵錯工具必須正在執行或處於中斷模式。  
  
    > [!NOTE]
    > 暫存器資訊無法用於指令碼或 SQL 應用程式內。  
  
## <a name="see-also"></a>另請參閱  
 [調試基本概念：暫存器視窗](../debugger/debugging-basics-registers-window.md)   
 [在偵錯工具中查看資料](../debugger/viewing-data-in-the-debugger.md)   
 [偵錯基本概念：暫存器視窗](../debugger/debugging-basics-registers-window.md)
