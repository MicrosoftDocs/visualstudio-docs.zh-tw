---
title: "移至定義和查看定義 | Microsoft Docs"
ms.custom: 
ms.date: 10/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code editor, go to definition
- code editor, peek definition
- go to definition
- peek definition
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: db67f01ff2a58ee856e4588df8770fc4edef8ca2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="go-to-definition-and-peek-definition"></a>移至定義和查看定義  
[移至定義] 和 [查看定義] 功能可讓您輕鬆地檢視類型或成員的定義。

## <a name="go-to-definition"></a>移至定義  
[移至定義] 功能可巡覽至類型或成員的來源，並在新的索引標籤中開啟結果。如果您是鍵盤使用者，請將文字游標放在符號名稱內的某個位置，然後按 **F12**。 如果您是滑鼠使用者，請選取操作功能表中的 [移至定義]，或使用下面所述的 **Ctrl+按一下滑鼠左鍵** 功能。  

### <a name="ctrl-click-go-to-definition"></a>Ctrl+按一下滑鼠左鍵移至定義  
在 Visual Studio 2017 15.4 版中，有更簡單的方法，可讓滑鼠使用者快速存取 [移至定義]。 當您按 **Ctrl** 並將滑鼠指標移至類型和成員上方時，符號會變成可點選。 若要快速巡覽至符號的定義，請按 **Ctrl** 鍵，然後按一下它。 就是這麼簡單！

![滑鼠點按移至定義動畫](../ide/media/click_gotodef.gif)

您可以變更滑鼠點按 [移至定義] 的輔助按鍵，方法是移至 [工具]、[選項]、[文字編輯器] 和 [一般]，然後選取 [Alt] 或 [Ctrl+Alt] 從 [Use modifier key] (使用輔助按鍵) 下拉式清單。 您也可以停用滑鼠點按 [移至定義]，方法是取消核取 [Enable mouse click to perform Go To Definition] (啟用滑鼠點按以執行移至定義) 核取方塊。  

![啟用滑鼠點按移至定義](../ide/media/editor_options_mouse_click_gotodef.png)  

## <a name="peek-definition"></a>查看定義
[查看定義] 功能可讓您預覽類型的定義，而不需要離開編輯器中的目前位置。 如果您是鍵盤使用者，請將文字游標放在類型或成員名稱內的某個位置，然後按 **Alt + F12**。 如果您是使用滑鼠的使用者，則可以選取操作功能表中的 [查看定義]。 在 Visual Studio 2017 15.4 版和更新版本中，有新的方式可以使用滑鼠查看檢視定義。 首先，依序移至 [工具]、[選項]、[文字編輯器] 和 [一般]。 選取 [Open definition in peek view] (在查看檢視中開啟定義) 選項，然後按一下 [確定] 關閉 [選項] 對話方塊。  

![設定滑鼠點按查看定義選項](../ide/media/editor_options_peek_view.png)  

然後按 **Ctrl** (或 [選項] 中選取的輔助按鍵)，然後按一下類型或成員。  

![查看定義動畫](../ide/media/peek_definition.gif)

如果您從快顯視窗查看另一個定義，則將開始階層連結路徑，而階層連結路徑可使用出現在快顯視窗上方的圓形和箭號進行巡覽。  

如需詳細資訊，請參閱[如何：使用查看定義檢視和編輯程式碼 (Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)。  

## <a name="see-also"></a>請參閱  
[巡覽程式碼](../ide/navigating-code.md)  
[如何：使用查看定義檢視和編輯程式碼 (Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)  
