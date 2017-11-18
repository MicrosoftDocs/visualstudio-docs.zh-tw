---
title: "變更方法簽章-重構 (C#) |Microsoft 文件"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: b4f45f9d-9c8f-46ae-99f7-7705c6d90b6e
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs: csharp
ms.openlocfilehash: 9ed72704c37fcfc5d0c48ba17937f5b06097ce0b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="change-a-method-signature-in-c"></a>變更在 C# 方法簽章 #
**項目：**可讓您移除或變更的方法參數的順序。

**當：**您想要移動或移除目前正在使用不同的位置中的方法參數。  

**原因：**但您無法手動移除和重新排列參數，然後尋找該方法的所有呼叫並變更它們的其中一個，可能導致錯誤。  這項重構工具會自動執行的工作。

**如何：**

1. 反白顯示，或將文字指標放置名稱的方法，若要修改，或其使用方式的其中一個：

   ![反白顯示的程式碼](media/changesignature_highlight.png)

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl + R**，然後**Ctrl + V 鍵**。  (請注意，根據您所選取的設定檔，鍵盤快速鍵可能會不同)。
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**變更簽章**從預覽視窗快顯視窗。
   * **滑鼠**
     * 選取**編輯 > 重構 > 移除參數**。
     * 選取**編輯 > 重構 > 重新排列參數**。
     * 以滑鼠右鍵按一下程式碼中，選取**快速控制項目及重構**功能表，然後選取**變更簽章**從預覽視窗快顯視窗。

1. 在**變更簽章**對話方塊出現，您也可以在右側使用按鈕，變更方法簽章：

   ![變更簽章對話方塊](media/changesignature_dialog.png)

   | 按鈕 | 說明
   | ------ | ---
   | **向上/向下鍵** | 將選取的參數在清單中上下移動
   | **移除**  | 從清單中移除選取的參數
   | **還原** | 還原已選取，跨越 out 參數清單

   > [!TIP]
   > 使用[**預覽參考變更**](../../ide/preview-changes.md)核取方塊，以查看結果將會對它執行之前。

1. 當您完成時，請按**確定**進行的變更 按鈕。

   ![變更簽章結果](media/changesignature_result.png)

## <a name="see-also"></a>另請參閱  
[重構 (C#)](../refactoring-csharp.md)  
[預覽變更](../../ide/preview-changes.md)