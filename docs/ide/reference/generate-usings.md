---
title: 產生 using
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
helpviewer_keywords:
- add missing usings
ms.openlocfilehash: f3b3435e10d6bb9a71fd16b9286759b136c167f4
ms.sourcegitcommit: ea5e02720d71185f8e27fbea205024371b0c7ceb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77544551"
---
# <a name="add-missing-usings-in-visual-studio"></a>在 Visual Studio 中新增遺漏的 using

此程式碼產生適用於：

- C#

**功能：** 讓您立即為複製和貼上的程式碼新增必要的匯入或[使用](/dotnet/csharp/language-reference/keywords/using-directive)指示詞。

時機 **：** 從您的專案或其他來源中的不同位置複製程式碼，並將它貼入新的程式碼，是常見的作法。 這個快速動作會尋找複製和貼上程式碼缺少匯入指示詞，然後提示您加入它們。 這個程式碼修正也可以將專案的參考加入至專案。

**原因：** 因為快速動作會自動新增必要的匯入，所以您不需要手動複製程式碼所需的 `using` 指示詞。

## <a name="add-missing-usings-refactoring"></a>新增遺漏的 using 重構

1. 複製檔案中的程式碼，並將它貼入新的檔案，而不包含必要的 `using` 指示詞。 產生的錯誤會伴隨程式碼修正，以加入遺漏的 `using` 指示詞。

    > [!NOTE]
    > 您需要在 [工具] > [選項] > [文字編輯器] > [C#] > [進階] > [Using 指示詞] 中啟用此建議。

2. 選取 Ctrl+. 以開啟 [快速動作與重構] 功能表。

    ![產生 using](media/generate-using-codefix.png)

3. 選取 [使用**您的參考\<]\>** 以新增遺失的參考。

    ![產生 using 結果](media/generate-using-result.png)

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
- [.NET 開發人員的秘訣](../csharp-developer-productivity.md)
