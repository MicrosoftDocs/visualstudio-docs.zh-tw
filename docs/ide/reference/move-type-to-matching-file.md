---
title: 將類型移到對應的檔案重構
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
ms.openlocfilehash: 997cf31d14acd65abd003bcb00cce4a9797b394a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059635"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>將類型移到對應的檔案重構

此重構適用於：

- C#

- Visual Basic

**功能：** 讓您將所選取類型移到具有相同名稱的個別檔案。

**時機：** 您在相同檔案中有多個類別、結構、介面等，而您想要加以分隔。

**原因：** 將多個類型放在相同檔案中會很難尋找這些類型。 藉由將類型移到具有相同名稱的檔案，程式碼會變得較容易閱讀及瀏覽。

## <a name="how-to"></a>操作說明

1. 將游標放在其中定義它的類型名稱內。 例如：

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. 接著，執行下列其中一項操作：

   - 在字行任何地方按 **Ctrl**+**.**，
   - 以滑鼠右鍵按一下類型名稱，並選取 [快速動作與重構]。

1. 從功能表選取 [將類型移到 *TypeName*.cs]，其中 *TypeName* 是您所選取之類型的名稱。

   該類型將移動到專案中與該類型名稱相同的新檔案。

   - C#: 

      ![內嵌結果 - C#](media/movetype-result-cs.png)

   - Visual Basic：

      ![內嵌結果 - Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
