---
title: 產生的 using
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
helpviewer_keywords:
- add missing usings
ms.openlocfilehash: 903b160bac0e8096062e09fd78ff4c92c46cf8ee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094309"
---
# <a name="add-missing-usings-in-visual-studio"></a>在 Visual Studio 中新增遺漏的 using

此程式碼產生適用於：

- C#

- Visual Basic

**內容：** 允許您立即添加必要的導入或使用[指令](/dotnet/csharp/language-reference/keywords/using-directive)進行複製和粘貼代碼。

**何時：** 通常的做法是從專案或其他源的不同位置複製代碼並將其粘貼到新代碼中。 此快速操作查找缺少複製和粘貼代碼的導入指令，然後提示您添加它們。 此代碼修復還可以從專案到專案增加參考。

**原因：** 由於"快速操作"會自動添加必要的導入，因此無需手動複製代碼所需的`using`指令。

## <a name="add-missing-usings-refactoring"></a>新增遺漏的 using 重構

1. 從檔案複製代碼並將其粘貼到新檔中，而不包含必要的`using`指令。 生成的錯誤附帶添加缺少`using`的指令的代碼修復程式。

    > [!NOTE]
    > 您需要在 [工具] > [選項] > [文字編輯器] > [C#] > [進階] > [Using 指示詞]**** 中啟用此建議。

2. 選取 Ctrl+. 以開啟 [快速動作與重構]**** 功能表。

    ![產生的 using](media/generate-using-codefix.png)

3. 選取 [使用\<您的參考\>]**** 以新增遺失的參考。

    ![產生 using 結果](media/generate-using-result.png)

## <a name="see-also"></a>另請參閱

- [產生程式碼](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
- [.NET 開發人員的提示](../csharp-developer-productivity.md)
