---
title: 在 Visual Studio 中將類型移到對應的檔案重構
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 00fab87a8fed4d1dcd9b4899551d68eaab28d46a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945333"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>將類型移到對應的檔案重構

此重構適用於：

- C#

- Visual Basic

**功能：** 讓您將選取的類型移到具有相同名稱的個別檔案。

**時機：** 您在相同檔案中有多個類別、結構、介面等，而想要加以分隔。

**原因：** 將多個類型放在相同檔案中會很難尋找這些類型。 藉由將類型移到具有相同名稱的檔案，程式碼會變得較容易閱讀及瀏覽。

## <a name="how-to"></a>操作說明

1. 醒目標示要移動的類型名稱，或將文字游標放在要移動的類型名稱內：

   - C#: 

    ![醒目提示的程式碼 - C#](media/movetype-highlight-cs.png)

   - Visual Basic：

    ![醒目提示的程式碼 - Visual Basic](media/movetype-highlight-vb.png)

1. 接著，執行下列其中一項操作：

   - **鍵盤**
     - 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [將類型移到 *TypeName*.cs]，其中 *TypeName* 是您所選類型的名稱。
   - **滑鼠**
     - 在程式碼上按一下滑鼠右鍵，選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [將類型移到 *TypeName*.cs]，其中 *TypeName* 是您所選類型的名稱。

   系統會將類型移到具有該名稱的新檔案中，作為解決方案的一部分。

   - C#: 

    ![內嵌結果 - C#](media/movetype-result-cs.png)

   - Visual Basic：

    ![內嵌結果 - Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)