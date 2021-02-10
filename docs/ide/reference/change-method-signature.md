---
title: 變更方法簽章
description: 加入、移除或變更方法參數的順序。 以滑鼠右鍵按一下方法、選取 [快速動作與重構]，然後選取 [變更簽章]。
ms.date: 07/20/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 01acbab7725effff5b2edbf8a80ab4f115fd2eff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935842"
---
# <a name="change-a-method-signature-refactoring"></a>變更方法特徵標記重構

此重構適用於：

- C#

- Visual Basic

**功能：** 讓您移除或變更方法參數的順序。

**時機：** 您想要移動或移除目前在各種位置中使用的方法參數。

**原因：** 您可以手動移除參數或重新排列其順序，然後尋找對該方法的所有呼叫並逐一變更這些呼叫，但這樣可能會造成錯誤。  這個重構工具將可自動執行此工作。

## <a name="how-to"></a>使用方法

1. 醒目標示要修改的方法名稱或它的其中一個使用方式，或將文字游標放在要修改的方法名稱或它的其中一個使用方式內：

   - C#：

       ![醒目提示的程式碼 C#](media/changesignature-highlight-cs.png)

   - VB：

       ![醒目提示的程式碼 - Visual Basic](media/changesignature-highlight-vb.png)

2. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 按 **CTRL+R**，再按 **CTRL+V**。  (請注意，根據您所選取的設定檔，鍵盤快速鍵可能會不同)。
      - 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [變更簽章]。
   - **滑鼠**
      - 選取 [編輯] > [重構] > [移除參數]。
      - 選取 [編輯] > [重構] > [重新排列參數]。
      - 在程式碼上按一下滑鼠右鍵，選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [變更簽章]。

3. 在 [變更簽章] 快顯對話方塊中，您可以使用右邊的按鈕來變更方法簽章：

   ![[變更簽章] 對話方塊](media/change-signature.png)

   | 按鈕 | 描述
   | ------ | ---
   | **向上/向下** | 將選取的參數在清單中向上和向下移動
   | **加入** | 新增參數至清單
   | **移除** | 將選取的參數從清單中移除
   | **還原** | 將所選的已刪除參數還原到清單中

   > [!TIP]
   > 使用 [ **預覽參考變更** ] 核取方塊，以在認可之前 [查看結果](../../ide/preview-changes.md) 。

4. 選取 [**變更** 簽章] 對話方塊中的 [**加入**]，將會開啟 [**加入參數**] 對話方塊。 [加入參數] 對話方塊可讓您新增類型名稱和參數名稱。 您可以選擇使參數為必要或選擇性且具預設值。 您可以接著在呼叫位置新增值並為該值選擇具名引數，或是引進 TODO 變數。 TODO 變數會將 TODO 放在您的程式碼中，讓您可以瀏覽每個錯誤並個別瀏覽每個呼叫位置，然後決定要傳遞的內容。 針對選擇性參數，您可以選擇完全省略呼叫位置。

    ![新增參數對話方塊-C#](media/add-parameter-dialog.png)

5. 當您完成新增參數時，請按 **[確定]** 以預覽變更。

    ![[變更簽章] 對話方塊](media/change-signature.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)