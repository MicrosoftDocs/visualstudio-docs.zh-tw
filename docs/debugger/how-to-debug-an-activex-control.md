---
title: "如何： 偵錯 ActiveX 控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.controls.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 932ccf7bdbea8fa68d0c2883d0ae8fd77eedf5bd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-an-activex-control"></a>如何：偵錯 ActiveX 控制項
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [工具] 功能表中選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
 若要偵錯您的 ActiveX 控制項，您必須指定容器 (可執行檔)，讓控制項在其中執行。  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>若要指定此偵錯工作階段的容器  
  
1.  在 [方案總管] 中選取專案。  
  
2.  從**檢視**功能表上，選擇**屬性頁**。  
  
3.  在**專案屬性頁**對話方塊中，開啟**組態屬性**資料夾，然後選取**偵錯**。  
  
4.  在下**偵錯**分類中，找出**命令**屬性。  
  
5.  指定該容器的路徑名稱。 例如，C:\Program Files\Internet Explorer\IEXPLORE.EXE。  
  
6.  如果您指定 Internet Explorer 做為容器，而且您正使用 Active Desktop，輸入`/new`中**命令引數**方塊。  
  
7.  按一下 [確定]。  
  
     如果您未指定容器中的**專案屬性頁**對話方塊中，當您開始偵錯時，可以指定容器。 當您選取 [執行命令以啟動偵錯，[偵錯工作階段] 對話方塊的可執行檔](../debugger/executable-for-debugging-session-dialog-box.md)隨即出現。 在對話方塊中指定容器的路徑名稱。  
  
## <a name="see-also"></a>另請參閱  
 [ActiveX 控制項](/cpp/mfc/activex-controls)   
 [使用測試容器測試屬性和事件](/cpp/mfc/testing-properties-and-events-with-test-container)   
 [COM 和 ActiveX 的偵錯](../debugger/com-and-activex-debugging.md)   
 [Visual Studio 偵錯](../debugger/index.md)  
 [偵錯工具功能導覽](../debugger/debugger-feature-tour.md)