---
title: "使用 C# 來重構方法簽章 | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: 44aaf3f4a570600b715d6d54f5fd80da84611b94
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2018
---
# <a name="change-a-method-signature-in-c"></a>使用 C# 來變更方法簽章 #

**功能：**讓您移除或變更方法參數的順序。

**時機：**您想要移動或移除目前在各種位置中使用的方法參數。  

**原因：**您可以手動移除參數或重新排列其順序，然後尋找對該方法的所有呼叫並逐一變更這些呼叫，但這樣可能會造成錯誤。  這個重構工具將可自動執行此工作。

**做法：**

1. 醒目標示要修改的方法名稱或它的其中一個使用方式，或將文字游標放在要修改的方法名稱或它的其中一個使用方式內：

   ![醒目標示的程式碼](media/changesignature-highlight-cs.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **CTRL+R**，再按 **CTRL+V**。  (請注意，根據您所選取的設定檔，鍵盤快速鍵可能會不同)。
     * 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [變更簽章]。
   * **滑鼠**
     * 選取 [編輯] > [重構] > [移除參數]。
     * 選取 [編輯] > [重構] > [重新排列參數]。
     * 在程式碼上按一下滑鼠右鍵，選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [變更簽章]。

1. 在 [變更簽章] 快顯對話方塊中，您可以使用右邊的按鈕來變更方法簽章：

   ![[變更簽章] 對話方塊](media/changesignature-dialog-cs.png)

   | 按鈕 | 描述
   | ------ | ---
   | **向上/向下** | 將選取的參數在清單中向上和向下移動
   | **移除**  | 將選取的參數從清單中移除
   | **還原** | 將所選的已刪除參數還原到清單中

   > [!TIP]
   > 請使用 [[預覽參考變更](../../ide/preview-changes.md)] 核取方塊，以在認可變更之前先查看將會有的結果。

1. 完成時，按 [確定] 按鈕以進行變更。

   ![「變更簽章」結果](media/changesignature-result-cs.png)

## <a name="see-also"></a>另請參閱

[重構](../refactoring-in-visual-studio.md)  
[預覽變更](../../ide/preview-changes.md)