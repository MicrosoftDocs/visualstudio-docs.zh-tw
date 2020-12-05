---
title: 重構重新命名
description: 瞭解如何使用重構重新命名功能來重新命名程式碼符號的識別碼，例如欄位、區域變數、方法、命名空間、屬性和類型。
ms.custom: SEO-VS-2020
ms.date: 05/04/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 43a6e93815732c4f9d2ec7f29d6d6bef4c1f3451
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616716"
---
# <a name="rename-a-code-symbol-refactoring"></a>為程式碼符號重新命名的重構

此重構適用於：

- C#

- Visual Basic

**功能：** 讓您重新命名程式碼符號 (例如欄位、區域變數、方法、命名空間、屬性及類型) 的識別碼。

**時機：** 您想要安全地重新命名某個項目，而無須尋找所有執行個體及複製/貼上新名稱。

**原因：** 在整個專案複製並貼上新名稱可能造成錯誤。 這個重構工具將可正確地執行重新命名動作。

## <a name="how-to"></a>操作方式

1. 醒目標示要重新命名的項目，或將文字游標放在要重新命名的項目內：

   - C#：

       ![醒目提示的程式碼 - C#](media/rename-highlight-cs.png)

   - Visual Basic：

       ![醒目提示的程式碼 - Visual Basic](media/rename-highlight-vb.png)

2. 接下來，使用鍵盤或滑鼠，如下所示：

   - **鍵盤**
      - 按 **CTRL+R**，再按 **CTRL+R**。 (請注意，根據您所選取的設定檔，鍵盤快速鍵可能會不同)。
   - **滑鼠**
      - 選取 [編輯] > [重構] > [重新命名]。
      - 在程式碼上按一下滑鼠右鍵，然後選取 [重新命名]。

3. 直接輸入新名稱來重新命名項目。

   - C#：

      ![重新命名動畫 - C#](media/rename-animated-cs.gif)

   - Visual Basic：

      ![重新命名 - VB](media/rename-rename-vb.png)

   > [!TIP]
   > 您也可以使用出現在編輯器右上角 [重新命名] 方塊中的核取方塊，將註解及其他字串更新為使用這個新名稱，以及在儲存前先[預覽變更](../../ide/preview-changes.md)。

4. 當您對變更感到滿意時，請選擇 [套用] 按鈕或按 **ENTER**，便會認可變更。

## <a name="remarks"></a>備註

- 從 Visual Studio 2019 16.3 版開始，當您重新命名符合其所在檔案名的型別時，會出現一個核取方塊，讓您可以同時重新命名檔案。 當您重新命名類別、介面或列舉時，會出現此選項。 具有多個定義的部分類型不支援此選項。

   ![使用 file-C 重新命名動畫#](media/rename-with-file-animated-cs.gif)

- 如果您使用已經存在的名稱，因而造成衝突，[重新命名] 方塊將會警告您。

   ![重新命名衝突](media/rename-conflict-cs.png)

- 重新命名符號的另一個方法是在編輯器中變更其名稱。 然後，將游標放在符號名稱中，然後按下 **Ctrl** + **。** 或直接展開出現的燈泡圖示功能表，然後選擇 [**重新 \<old name> 命名 \<new name> 為**]。

   ![在編輯器中重新命名](media/rename-with-editor-cs.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
