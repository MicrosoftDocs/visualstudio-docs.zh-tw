---
title: HOW TO：使用暫存器視窗 |Microsoft Docs
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
ms.openlocfilehash: f622440c5bd0f0d09967eff56479459a4a3bfbb0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60042871"
---
# <a name="how-to-use-the-registers-window"></a>HOW TO：使用暫存器視窗
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

暫存器視窗是在已啟用位址層級偵錯時，才可以使用**選項** 對話方塊中，**偵錯**節點，**一般**類別目錄。  
  
 **註冊**視窗會顯示暫存器內容。 如果您保留**註冊**視窗開啟，當您逐步執行程式，您可以看到您的程式碼執行時暫存器值的變更。 最近變更過的值以紅色顯示。 您可以編輯暫存器值。 如需詳細資訊，請參閱[如何：編輯暫存器值](../debugger/how-to-edit-a-register-value.md)。  
  
 為了減少雜亂的情況，[暫存器] 視窗會依據平台和處理器類型，將暫存器分為不同的群組。 您可以視需要顯示或隱藏群組。 如需詳細資訊，請參閱[如何：顯示和隱藏暫存器群組](../debugger/how-to-display-and-hide-register-groups.md)。  
  
 暫存器和暫存器視窗的基本概念的高階介紹，請參閱[偵錯基本概念：暫存器視窗](../debugger/debugging-basics-registers-window.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-display-the-registers-window"></a>若要顯示暫存器視窗  
  
- 在上**偵錯**功能表上，選擇**Windows**，然後選擇**註冊**。  
  
     偵錯工具必須正在執行或處於中斷模式。  
  
    > [!NOTE]
    >  暫存器資訊無法用於指令碼或 SQL 應用程式內。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯基本概念：暫存器視窗](../debugger/debugging-basics-registers-window.md)   
 [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)   
 [偵錯基本概念：暫存器視窗](../debugger/debugging-basics-registers-window.md)
