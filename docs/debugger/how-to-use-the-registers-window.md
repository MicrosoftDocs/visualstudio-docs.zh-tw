---
title: 在 Visual Studio 偵錯工具中檢視暫存器值 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.registers
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5f236bf43d3667cd4263d205c4588593a973824d
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257159"
---
# <a name="view-register-values-and-use-the-registers-window-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>檢視暫存器值，並使用 Visual Studio 偵錯工具中的 [暫存器] 視窗 (C#，c + +、 Visual Basic 中， F#)
暫存器視窗是在已啟用位址層級偵錯時，才可以使用**選項** 對話方塊中，**偵錯**節點，**一般**類別目錄。  
  
 **註冊**視窗會顯示暫存器內容。 如果您保留**註冊**視窗開啟，當您逐步執行程式，您可以看到您的程式碼執行時暫存器值的變更。 最近變更過的值以紅色顯示。 您可以編輯暫存器值。 如需詳細資訊，請參閱 <<c0> [ 如何： 編輯暫存器值](../debugger/how-to-edit-a-register-value.md)。  
  
 若要減少雜亂，**註冊**視窗會將暫存器組織成群組，根據平台和處理器類型不同型別。 您可以視需要顯示或隱藏群組。 如需詳細資訊，請參閱 <<c0> [ 如何： 顯示和隱藏暫存器群組](../debugger/how-to-display-and-hide-register-groups.md)。  
  
 暫存器和暫存器視窗的基本概念的高階介紹，請參閱 <<c0> [ 偵錯基本概念： 暫存器視窗](../debugger/debugging-basics-registers-window.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
### <a name="to-display-the-registers-window"></a>若要顯示暫存器視窗  
  
-   上**偵錯**功能表上，選擇**Windows**，然後選擇**註冊**(或選擇**Ctrl** + **Alt**  +  **G**)。  
  
     偵錯工具必須正在執行或處於中斷模式。  
  
    > [!NOTE]
    >  暫存器資訊無法用於指令碼或 SQL 應用程式內。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯基本概念：暫存器視窗](../debugger/debugging-basics-registers-window.md)   
 [在 偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)   
 [偵錯基本概念：暫存器視窗](../debugger/debugging-basics-registers-window.md)