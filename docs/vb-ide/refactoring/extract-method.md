---
title: "擷取方法重構 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: 8ad16c15-432b-4b8c-86fd-5f31ad652d24
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.extractmethod
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: 6ec25b8c0e2a583364ff3c6418515507cdc04d40
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="extract-a-method-in-visual-basic"></a>擷取在 Visual Basic 中的方法
**項目：**可讓您的程式碼片段變成它自己的方法。

**當：**某些需要從另一個方法呼叫的方法中有現有的程式碼片段。  

**原因：**您無法複製/貼上該程式碼，但這就可能會導致重複。  更好的解決方案是該片段重構自己的任何其他方法可以自由呼叫的方法。

**如何：**

1. 反白顯示要擷取的程式碼：

   ![反白顯示的程式碼](media/extractmethod_highlight.png)

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl + R**，然後**Ctrl + M**。  (請注意，根據您所選取的設定檔，鍵盤快速鍵可能會不同)。
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**擷取方法**從預覽視窗快顯視窗。
   * **滑鼠**
     * 選取**編輯 > 重構 > 擷取方法**。
     * 以滑鼠右鍵按一下程式碼，然後選取**重構 > 擷取 > 擷取方法**。
     * 以滑鼠右鍵按一下程式碼中，選取**快速控制項目及重構**功能表，然後選取**擷取方法**從預覽視窗快顯視窗。

   此方法將會立即建立。  從這裡，您可以立即重新命名方法只要輸入新名稱。

   > [!TIP]
   > 您也可以更新註解和其他字串，才能使用這個新的名稱，以及[預覽變更](../../ide/preview-changes.md)之前儲存使用中的核取方塊**重新命名**會出現在頂端的方塊右邊您的 IDE。

   ![重新命名方法](media/extractmethod_rename.png)

1. 變更感到滿意時，按一下**套用**按鈕或按**Enter**和會認可變更。

## <a name="see-also"></a>請參閱  
[重構 (Visual Basic)](../refactoring-vb.md)  
[預覽變更](../../ide/preview-changes.md)