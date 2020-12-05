---
title: 產生的 using
description: 瞭解如何使用 [快速動作與重構] 功能表立即新增必要的匯入，或針對複製和貼上的程式碼使用指示詞。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 38996d1cda52dfe98b6ce9cf24e5adcca6a8b069
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617158"
---
# <a name="add-missing-usings-in-visual-studio"></a>在 Visual Studio 中新增遺漏的 using

此程式碼產生適用於：

- C#

- Visual Basic

事項 **：** 讓您立即新增必要的匯入，或針對複製和貼上的程式碼 [使用](/dotnet/csharp/language-reference/keywords/using-directive)指示詞。

時機 **：** 常見的作法是從專案或其他來源中的不同位置複製程式碼，並將其貼到新的程式碼中。 此快速動作會找出複製和貼上程式碼遺漏的 imports 指示詞，然後提示您加入它們。 這段程式碼修正也可以將專案的參考加入至專案。

**原因：** 由於快速動作會自動新增必要的匯入，因此您不需要手動複製 `using` 程式碼所需的指示詞。

## <a name="add-missing-usings-refactoring"></a>新增遺漏的 using 重構

1. 從檔案複製程式碼，並將它貼到新的程式碼中，而不包含必要的指示詞 `using` 。 產生的錯誤會伴隨程式碼修正，以新增遺漏的指示詞 `using` 。

    > [!NOTE]
    > 您需要在 [工具] > [選項] > [文字編輯器] > [C#] > [進階] > [Using 指示詞] 中啟用此建議。

2. 選取 Ctrl+. 以開啟 [快速動作與重構] 功能表。

    ![產生的 using](media/generate-using-codefix.png)

3. 選取 **[ \<your reference\> 使用** ]，以加入遺漏的參考。

    ![產生 using 結果](media/generate-using-result.png)

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
- [.NET 開發人員的秘訣](../csharp-developer-productivity.md)
