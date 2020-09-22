---
title: 如何：使用 Finder 工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Window Finder Tool
ms.assetid: 5841926b-08c3-4e43-88bd-4223d04f9aef
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 00535fd336f504afcebdd24a4d009a10f7f6ff33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839057"
---
# <a name="how-to-use-the-finder-tool"></a>如何：使用搜尋工具
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 [ **尋找視窗** ] 對話方塊中的 [Finder] 工具來顯示視窗屬性或訊息。 Finder 工具也可以找出已停用的子視窗，並辨別停用的子視窗是否重迭時要醒目提示哪個視窗。  
  
 ![Spy&#43;&#43; 尋找視窗] 對話方塊](../debugger/media/icon-spy-find.png "Icon_Spy + + _Find")  
尋找視窗對話方塊中的 Finder 工具  
  
 上圖顯示下列步驟3之後的 [尋找視窗] 對話方塊。  
  
### <a name="to-display-window-properties-or-messages"></a>顯示視窗屬性或訊息  
  
1. 排列視窗，讓 Spy + + 和目標視窗都可以看見。  
  
2. 從 **Spy** 功能表選擇 [ **尋找視窗]**。  
  
     [ [尋找視窗] 對話方塊](../debugger/find-window-dialog-box.md) 隨即開啟。  
  
3. 將 [ **Finder] 工具** 拖曳至目標視窗。  
  
     當您拖曳工具時，[ **尋找視窗** ] 對話方塊會顯示所選視窗的詳細資料。  
  
     -或-  
  
     如果您有想要檢查的視窗控制碼 (例如，從偵錯工具) 複製的，請將它輸入 [ **控制碼** ] 文字方塊中。  
  
    > [!TIP]
    > 若要減少螢幕混亂，請選取 [ **隱藏 Spy** ] 選項。 此選項會隱藏主要的 Spy + + 視窗，讓 [ **尋找視窗** ] 對話方塊只會顯示在其他應用程式的頂端。 當您按一下 **[確定] 或 [** **取消**]，或清除 [ **隱藏 spy + +** ] 選項時，就會還原 Spy + + 主視窗。  
  
4. 在 [ **顯示**] 底下，選取 [ **屬性** ] 或 [ **訊息**]。  
  
5. 按下 **[確定]**。  
  
     如果您選取 [ **屬性**]，則 [ [視窗屬性] 對話方塊](../debugger/window-properties-dialog-box.md) 隨即開啟。 如果您選取 [ **訊息**]，則會開啟 [ [訊息] 視圖](../debugger/messages-view.md) 視窗。  
  
## <a name="see-also"></a>另請參閱  
 [Spy + + Views](../debugger/spy-increment-views.md)   
 [使用 Spy + +](../debugger/using-spy-increment.md)   
 [Spy++ 參考](../debugger/spy-increment-reference.md)
