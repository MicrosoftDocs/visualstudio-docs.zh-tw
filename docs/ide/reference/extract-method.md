---
title: 使用 Visual Studio 來擷取方法
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 6978457fdc976f87a8334b181ab69dfd78ef240c
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294536"
---
# <a name="extract-a-method-refactoring"></a>擷取方法重構

此重構適用於：

- C#

- Visual Basic

**功能：** 讓您將程式碼片段轉換成它自己的方法。

**時機：** 您在某個必須從另一個方法來呼叫的方法中有現有的程式碼片段。

**原因：** 您可以複製/貼上該程式碼，但那樣會造成重複。 較好的解決方案是將該片段重構成它自己的且可由任何其他方法自由呼叫的方法。

## <a name="how-to"></a>操作說明

1. 醒目標示的擷取的程式碼：

   - C#: 

       ![醒目提示的程式碼 - C#](media/extractmethod-highlight-cs.png)

   - Visual Basic：

       ![醒目提示的程式碼 - Visual Basic](media/extractmethod-highlight-vb.png)

2. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 按 **CTRL+R**，再按 **CTRL+M**。 (請注意，根據您所選取的設定檔，鍵盤快速鍵可能會不同)。
      - 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [擷取方法]。
   - **滑鼠**
      - 選取 [編輯] > [重構] > [擷取方法]。
      - 在程式碼上按一下滑鼠右鍵，然後選取 [重構] > [擷取] > [擷取方法]。
      - 在程式碼上按一下滑鼠右鍵，選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [擷取方法]。

   系統將會立即建立方法。 從這裡，您現在即可輸入新名稱來為方法重新命名。

   > [!TIP]
   > 您也可以使用出現在 IDE 右上角 [重新命名] 方塊中的核取方塊，以更新註解和其他字串來使用這個新名稱，以及在儲存前先[預覽變更](../../ide/preview-changes.md)。

   - C#: 

      ![重新命名方法 - C#](media/extractmethod-rename-cs.png)

   - Visual Basic：

      ![重新命名方法 - Visual Basic](media/extractmethod-rename-vb.png)

3. 當您對變更感到滿意時，請選擇 [套用] 按鈕或按 **ENTER**，便會認可變更。

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)