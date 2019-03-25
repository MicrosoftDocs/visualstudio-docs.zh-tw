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
ms.openlocfilehash: f59dceabb076ebce36755c41caa6de00258be883
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160637"
---
# <a name="generate-usings-in-visual-studio"></a>在 Visual Studio 中產生 using

此程式碼產生適用於：

- C#

**功能：****功能：** 可讓您立即新增必要的匯入，或複製並貼上程式碼的 [using 陳述式](/dotnet/csharp/language-reference/keywords/using-statement)。

**時機：** 常見做法是從專案或其他程式碼來源中的不同位置複製並貼上程式碼。 此快速動作會分析複製並貼上程式碼所遺失的匯入，並會提示您將其新增。

**原因：** 藉由自動新增必要的匯入，使用者不需要手動複製所需的 `using` 陳述式。

## <a name="generate-usings-refactoring"></a>產生 using 重構

1. 從不同的檔案複製並貼上程式碼，但不包含必要的 `using` 陳述式。 該錯誤現在會伴隨程式碼修正，該修正會新增遺失的 `using` 陳述式。

    > [!NOTE] 
    > 這項建議需要在 [工具 > 選項 > 文字編輯器 > C# > 進階 > Using 指示詞] 中開啟。

2. 在字行任何地方按 **Ctrl**+**.**， 以開啟 [快速動作與重構] 功能表。 

    ![產生 using](media/generate-using-codefix.png)

3. 選取 [使用\<您的參考\>] 以新增遺失的參考。

    ![產生 using 結果](media/generate-using-result.png)

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
- [.NET 開發人員的秘訣](../../ide/visual-studio-2017-for-dotnet-developers.md)