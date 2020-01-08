---
title: 將欄位重構為屬性
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: db0bd17cd0bead3807f857b2198b8d4ea4c72ffb
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75569708"
---
# <a name="encapsulate-a-field-refactoring"></a>封裝欄位重構

此重構適用於：

- C#

- Visual Basic

**功能：** 讓您將欄位轉換為屬性，並更新該欄位的所有使用方式以使用新建立的屬性。

**時機：** 您想要將欄位移到屬性中，並更新對該欄位的所有參考。

**原因：** 您想要讓其他類別能夠存取欄位，但不想要讓這些類別擁有直接存取權。  例如，透過將欄位包裝在屬性中，您可以撰寫程式碼來確認所指派的值。

## <a name="how-to"></a>操作說明

1. 醒目標示要封裝的欄位名稱，或將文字游標放在要封裝的欄位名稱內：

   - C#:

       ![醒目提示的程式碼 - C#](media/encapsulate-highlight-cs.png)

   - Visual Basic：

       ![醒目提示的程式碼 - Visual Basic](media/encapsulate-highlight-vb.png)

2. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 按 **CTRL+R**，再按 **CTRL+E**。  (請注意，根據您所選取的設定檔，鍵盤快速鍵可能會不同)。
      - 在字行任何地方按 **Ctrl**+ **.** ， 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取任一個 [封裝欄位] 項目。
   - **滑鼠**
      - 選取 [編輯] > [重構] > [封裝欄位]。
      - 在程式碼上按一下滑鼠右鍵，選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取任一個 [封裝欄位] 項目。

   選取 | 描述
   --------- | -----------
   **封裝欄位 (並使用屬性)** | 使用屬性來封裝欄位，並更新該欄位的所有使用方式以使用產生的屬性
   **封裝欄位 (但仍使用欄位)** | 使用屬性來封裝欄位，但將該欄位的所有使用方式保持不變

   系統會建立屬性，並更新對該欄位的參考 (若已選取)。

   > [!TIP]
   > 請使用快顯視窗中的 [預覽變更] 連結，以在認可變更之前先[查看會有什麼結果](../../ide/preview-changes.md)。

   - C#:

      ![封裝屬性結果 - C#](media/encapsulate-result-cs.png)

   - Visual Basic：

      ![封裝屬性結果 - Visual Basic](media/encapsulate-result-vb.png)

## <a name="see-also"></a>請參閱

- [重構](../refactoring-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
