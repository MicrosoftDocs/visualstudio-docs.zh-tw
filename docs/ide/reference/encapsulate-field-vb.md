---
title: "使用 Visual Basic 將欄位重構為屬性 | Microsoft Docs"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.encapsulatefield
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: 010a297745ed6028f7ee127fffc210097d6d26f5
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2018
---
# <a name="encapsulate-a-field-in-visual-basic"></a>使用 Visual Basic 來封裝欄位

**功能：**讓您將欄位轉換為屬性，並更新該欄位的所有使用方式以使用新建立的屬性。

**時機：**您想要將欄位移到屬性中，並更新對該欄位的所有參考。  

**原因：**您想要讓其他類別能夠存取欄位，但不想要讓這些類別擁有直接存取權。  例如，透過將欄位包裝在屬性中，您可以撰寫程式碼來確認所指派的值。

**做法：**

1. 醒目標示要封裝的欄位名稱，或將文字游標放在要封裝的欄位名稱內：

   ![醒目標示的程式碼](media/encapsulate-highlight-vb.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **CTRL+R**，再按 **CTRL+E**。  (請注意，根據您所選取的設定檔，鍵盤快速鍵可能會不同)。
     * 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取任一個 [封裝欄位] 項目。
   * **滑鼠**
     * 選取 [編輯] > [重構] > [封裝欄位]。
     * 在程式碼上按一下滑鼠右鍵，選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取任一個 [封裝欄位] 項目。

   選取 | 描述
   --------- | -----------
   **封裝欄位 (並使用屬性)** | 使用屬性來封裝欄位，並更新該欄位的所有使用方式以使用產生的屬性
   **封裝欄位 (但仍使用欄位)** | 使用屬性來封裝欄位，但將該欄位的所有使用方式保持不變

   系統將會立即建立屬性，並且會更新對該欄位的參考 (如果已選取的話)。

   > [!TIP]
   > 請使用快顯視窗中的 [[預覽變更](../../ide/preview-changes.md)] 連結，以在認可變更之前先查看將會有的結果。

   ![「封裝屬性」結果](media/encapsulate-result-vb.png)

## <a name="see-also"></a>另請參閱

[重構](../refactoring-in-visual-studio.md)  
[預覽變更](../../ide/preview-changes.md)