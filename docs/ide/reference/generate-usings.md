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
ms.openlocfilehash: 9124054dec08fde94ec98ca9e3ebdfb6e48d7384
ms.sourcegitcommit: 614d5b99576ea27a41957cd94062dc95cbd29c1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2019
ms.locfileid: "65531621"
---
# <a name="generate-usings-in-visual-studio"></a>在 Visual Studio 中產生 using

此程式碼產生適用於：

- C#

**功能：** 可讓您立即新增必要的匯入，或複製並貼上程式碼的 [using 陳述式](/dotnet/csharp/language-reference/keywords/using-statement)。

**時機：** 從專案或其他程式碼來源中的不同位置複製程式碼，然後貼上到新程式碼中是很常見的。 此快速控制項目會針對複製並貼上程式碼尋找遺失的匯入，並提示您新增它們。

**原因：** 因為快速控制項目會自動新增必要的匯入，所以您不需要手動複製您程式碼需要的 `using` 陳述式。

## <a name="generate-usings-refactoring"></a>產生 using 重構

1. 從檔案複製程式碼並貼上到新檔案中，但不包含必要的 `using` 陳述式。 產生的錯誤現在會伴隨程式碼修正，該修正會新增遺失的 `using` 陳述式。

    > [!NOTE]
    > 您需要在 [工具] > [選項] > [文字編輯器] > [C#] > [進階] > [Using 指示詞] 中啟用此建議。

2. 選取 Ctrl+. 以開啟 [快速動作與重構] 功能表。

    ![產生 using](media/generate-using-codefix.png)

3. 選取 [使用\<您的參考\>] 以新增遺失的參考。

    ![產生 using 結果](media/generate-using-result.png)

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
- [.NET 開發人員的秘訣](../csharp-developer-productivity.md)
