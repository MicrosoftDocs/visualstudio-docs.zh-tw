---
title: "在 Visual Studio 中將檔案名稱重新命名以符合類型 | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 45cd94161f492ea0326ff08fe40727149a733556
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-refactoring"></a>將類型同步至檔案名稱，或將檔案名稱同步至類型的重構

此重構適用於：

- C#

- Visual Basic

**功能：**讓您將類型重新命名以符合檔案名稱，或將檔案名稱重新命名以符合其包含的類型。

**時機：**您已將檔案或類型重新命名，但尚未更新對應的檔案或類型來使其相符。

**原因：**將類型放在不同名稱的檔案中 (或反之亦然) 會很難找出所要尋找的項目。 藉由將類型或檔案名稱重新命名，程式碼會變得較容易閱讀及瀏覽。

## <a name="how-to"></a>操作說明

1. 醒目標示要同步的類型名稱，或將文字游標放在要同步的類型名稱內：

   - C#: 

    ![醒目提示的程式碼 - C#](media/synctype-highlight-cs.png)

   - Visual Basic：

    ![醒目提示的程式碼 - Visual Basic](media/synctype-highlight-vb.png)

1. 接著，執行下列其中一項操作：

   - **鍵盤**
     - 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [將檔案重新命名為 *TypeName*.cs]，其中 *TypeName* 是您所選類型的名稱。
     - 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [將類型重新命名為 _Filename_]，其中 *Filename* 是目前檔案的名稱。
   - **滑鼠**
     - 在程式碼上按一下滑鼠右鍵，選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [將檔案重新命名為 *TypeName*.cs]，其中 *TypeName* 是您所選類型的名稱。
     - 在程式碼上按一下滑鼠右鍵，選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [將類型重新命名為 _Filename_]，其中 *Filename* 是目前檔案的名稱。

   類型或檔案會重新命名。

   - C#：在下面的範例中，檔案 **MyClass.cs** 已重新命名為 **MyNewClass.cs** 以符合類型名稱。

      ![內嵌結果 C#](media/synctype-result-cs.png)

   - Visual Basic：在下面的範例中，檔案 **Employee.vb** 已重新命名為 **Person.vb** 以符合類型名稱。

      ![內嵌結果 Visual Basic](media/synctype-result-vb.png)

> ！[注意] 這項重構尚不適用於.NET Standard 和.NET Core 專案。

## <a name="see-also"></a>另請參閱

[重構](../refactoring-in-visual-studio.md)
