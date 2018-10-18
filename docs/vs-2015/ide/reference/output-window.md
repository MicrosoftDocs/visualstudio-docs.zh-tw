---
title: 輸出視窗 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.build.output
- vs.debug.output
- vs.output
helpviewer_keywords:
- Output window, about Output window
- Output window
- Toolbox, removing controls
ms.assetid: d8931d88-250e-4db4-963f-2c5b3e99b45f
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 55869ff13cf4048b6d256e57892d470062847501
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189900"
---
# <a name="output-window"></a>輸出視窗
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
[輸出] 視窗可以顯示整合式開發環境 (IDE) 中各種功能的狀態訊息。 若要開啟 [輸出] 視窗，請在功能表列上選擇 [檢視/輸出]\(或按一下 CTRL+ALT+O)。  
  
> [!WARNING]
>  在 Visual Studio Express 版本的 [檢視] 功能表上不會出現 [輸出] 視窗。 若要顯示它，請使用快速鍵 CTRL+ALT+O。  
  
## <a name="toolbar"></a>工具列  
 **顯示來自以下位置的輸出**  
 顯示要檢視的一或多個輸出窗格。 根據 IDE 中的哪些工具使用 [輸出] 視窗將訊息傳遞給使用者，可能可以使用數個資訊窗格。  
  
 **在程式碼中尋找訊息**  
 將程式碼編輯器中的插入點移至包含所選取建置錯誤的行。  
  
 **移至上一個訊息**  
 將 [輸出] 視窗中的焦點變更為上一個建置錯誤，並將程式碼編輯器中的插入點移至包含該建置錯誤的行。  
  
 **移至下一個訊息**  
 將 [輸出] 視窗中的焦點變更為下一個建置錯誤，並將程式碼編輯器中的插入點移至包含該建置錯誤的行。  
  
 **全部清除**  
 從 [輸出] 窗格清除所有文字。  
  
 **切換自動換行**  
 開啟和關閉 [輸出] 窗格中的自動換行功能。 開啟自動換行時，較長項目中超出檢視區域的文字會顯示在下一行。  
  
## <a name="output-pane"></a>輸出窗格  
 [顯示來自以下位置的輸出] 清單中所選取的 [輸出] 窗格會顯示來自所指出來源的輸出。  
  
## <a name="routing-messages-to-the-output-window"></a>將訊息傳送至輸出視窗  
 若只要建置專案就顯示 [輸出] 視窗，請在 [選項] 對話方塊、[專案和方案]、[一般] 中選取 [建置開始時顯示輸出視窗]。 然後，在開啟程式碼檔進行編輯時，選擇 [輸出] 視窗工具列上的 [移至下一個訊息] 和 [移至上一個訊息] 按鈕以選取 [輸出] 窗格中的項目。 當您這麼做時，程式碼編輯器中的插入點會跳到發生所選取問題的程式碼行。  
  
 [命令視窗](../../ide/reference/command-window.md)中所叫用的某些 IDE 功能和命令會將其輸出傳遞給 [輸出] 視窗。 當您在[管理外部工具](../../ide/managing-external-tools.md)中選取 [使用輸出視窗] 選項時，會將一般顯示在 [命令提示字元] 視窗中且來自外部工具的輸出 (例如 .bat 和 .com 檔案) 傳送至 [輸出] 窗格。 許多其他種類的訊息也可以顯示在 [輸出] 窗格中。 例如，針對目標資料庫檢查預存程序中的 Transact-SQL 語法時，結果會顯示在 [輸出] 視窗中。  
  
 您也可以透過程式設計方式撰寫自己的應用程式，以在執行階段將診斷訊息寫入 [輸出] 窗格。 若要執行此工作，請使用 .NET Framework 類別庫 <xref:System.Diagnostics> 命名空間的 <xref:System.Diagnostics.Debug> 類別或 <xref:System.Diagnostics.Trace> 類別成員。 建置方案或專案的偵錯組態時，<xref:System.Diagnostics.Debug> 類別的成員會顯示輸出；建置偵錯或發行組態時，<xref:System.Diagnostics.Trace> 類別的成員會顯示輸出。 如需詳細資訊，請參閱[輸出視窗中的診斷訊息](../../debugger/diagnostic-messages-in-the-output-window.md)。  
  
 在 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 中，您可以建立自訂建置步驟和建置事件，而其警告和錯誤會顯示並計入 [輸出] 窗格中。 您可以在輸出行上按 F1，以顯示適當的說明主題。 如需詳細資訊，請參閱[格式化自訂建置步驟或建置事件的輸出](http://msdn.microsoft.com/library/92ad3e38-24d7-4b89-90e6-5a16f5f998da)。  
  
## <a name="scrolling-behavior"></a>捲動行為  
 如果您在 [輸出] 視窗中使用自動捲動，然後使用滑鼠或方向鍵進行巡覽，則會停止自動捲動。 若要繼續自動捲動，請按 CTRL+END。  
  
## <a name="see-also"></a>另請參閱  
 [輸出視窗中的診斷訊息](../../debugger/diagnostic-messages-in-the-output-window.md)   
 [如何：控制輸出視窗](http://msdn.microsoft.com/library/91aebd15-8854-4a7a-9f7d-57376fb4e858)   
 [編譯和建置](../../ide/compiling-and-building-in-visual-studio.md)   
 [了解組建組態](../../ide/understanding-build-configurations.md)   
 [類別庫概觀](http://msdn.microsoft.com/library/7e4c5921-955d-4b06-8709-101873acf157)



