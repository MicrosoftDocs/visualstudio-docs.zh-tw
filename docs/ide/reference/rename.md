---
title: 重構重新命名
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 02b08f3218ab6f1380884d2385899d6dd486bb81
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063149"
---
# <a name="rename-a-code-symbol-refactoring"></a>為程式碼符號重新命名的重構

此重構適用於：

- C#

- Visual Basic

**功能：** 讓您重新命名程式碼符號 (例如欄位、區域變數、方法、命名空間、屬性及類型) 的識別碼。

**時機：** 您想要安全地重新命名某個項目，而無須尋找所有執行個體及複製/貼上新名稱。

**原因：** 在整個專案複製並貼上新名稱可能造成錯誤。 這個重構工具將可正確地執行重新命名動作。

## <a name="how-to"></a>操作說明

1. 醒目標示要重新命名的項目，或將文字游標放在要重新命名的項目內：

   - C#: 

       ![醒目提示的程式碼 - C#](media/rename-highlight-cs.png)

   - Visual Basic：

       ![醒目提示的程式碼 - Visual Basic](media/rename-highlight-vb.png)

2. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 按 **CTRL+R**，再按 **CTRL+R**。 (請注意，根據您所選取的設定檔，鍵盤快速鍵可能會不同)。
   - **滑鼠**
      - 選取 [編輯] > [重構] > [重新命名]。
      - 在程式碼上按一下滑鼠右鍵，然後選取 [重新命名]。

3. 直接輸入新名稱來重新命名項目。

   - C#: 

      ![重新命名動畫 - C#](media/rename-animated-cs.gif)

   - Visual Basic：

      ![重新命名 - VB](media/rename-rename-vb.png)

   > [!TIP]
   > 您也可以使用出現在編輯器右上角 [重新命名] 方塊中的核取方塊，將註解及其他字串更新為使用這個新名稱，以及在儲存前先[預覽變更](../../ide/preview-changes.md)。

4. 當您對變更感到滿意時，請選擇 [套用] 按鈕或按 **ENTER**，便會認可變更。

> [!NOTE]
> 如果您使用已經存在的名稱，因而造成衝突，[重新命名] 方塊將會警告您。
>
> ![重新命名衝突](media/rename-conflict-cs.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
