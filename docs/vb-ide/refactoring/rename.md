---
title: "重新命名為重構 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: abf1565b-c7b7-4d45-b3d3-a438a836c70e
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.rename
dev_langs: VB
ms.openlocfilehash: 35313f036e1f324d3f8908a4527cd3a2ad64ae52
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="rename-a-code-symbol-in-visual-basic"></a>重新命名在 Visual Basic 中的程式碼符號
**項目：**可讓您重新命名程式碼的符號，例如欄位、 區域變數、 方法、 命名空間、 屬性和類型的識別項。

**當：**您想要安全地重新命名的項目，而不必尋找所有執行個體，並複製/貼上的新名稱。  

**原因：**複製並貼上整個專案的新名稱可能會導致錯誤。  這項重構工具正確地將執行重新命名動作。

**如何：**

1. 反白顯示，或將文字指標放置在重新命名項目：

   ![反白顯示的程式碼](media/rename_highlight.png)

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl + R**，然後**Ctrl + R**。  (請注意，根據您所選取的設定檔，鍵盤快速鍵可能會不同)。
   * **滑鼠**
     * 選取**編輯 > 重構 > 重新命名**。
     * 以滑鼠右鍵按一下程式碼，然後選取**重新命名**。

1. 只要輸入新名稱，重新命名項目。

   ![重新命名動畫](media/rename_rename.png)

   > [!TIP]
   > 您也可以更新註解和其他字串，才能使用這個新的名稱，以及[預覽變更](../../ide/preview-changes.md)之前儲存使用中的核取方塊**重新命名**會出現在頂端的方塊右邊您的 IDE。

1. 變更感到滿意時，按一下**套用**按鈕或按**Enter**和會認可變更。

> [!NOTE]
> 如果您使用的名稱已經存在，會導致衝突，**重新命名**在您的 IDE 中的方塊會警告您。
>
> ![重新命名衝突](media/rename_conflict.png)

## <a name="see-also"></a>另請參閱  
[重構 (Visual Basic)](../refactoring-vb.md)  
[預覽變更](../../ide/preview-changes.md)