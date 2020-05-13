---
title: 插入 XML 文件註解
ms.date: 01/22/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0e21d0617f954c0cc34975b7f8626b83966f6b5d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77706386"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>如何：在文件產生中插入 XML 註解

Visual Studio 可藉由自動產生標準 XML 文件註解結構，來幫助您記錄諸如類別和方法的程式碼項目。 編譯時間中，您可以產生包含文件註解的 XML 檔案。

> [!TIP]
> 如需設定所產生 XML 檔案的名稱和位置，請參閱[使用 XML 註解記錄您的程式碼 (C# 指南)](/dotnet/csharp/codedoc)。

編譯器所產生的 XML 檔案可以隨著 .NET 組件一起散發，因此 Visual Studio 和其他 IDE 可以使用 IntelliSense 來顯示類型和成員的快速資訊。 此外，可以透過 [DocFX](https://dotnet.github.io/docfx/) 和 [Sandcastle](https://www.microsoft.com/download/details.aspx?id=10526) 這類工具執行 XML 檔案來產生 API 參考網站。

> [!NOTE]
> 會自動插入 XML 文件註解的**插入註解**命令適用於 [C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) 和 [Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)。 然而，您可以手動插入 [C + + 中的 XML 文件註解](/cpp/build/reference/xml-documentation-visual-cpp)檔案，且仍可在編譯時間產生 XML 文件檔。

## <a name="to-insert-xml-comments-for-a-code-element"></a>為程式碼項目插入 XML 註解

1. 將文字游標放在您想要記載的元素 (例如方法) 上方。

2. 執行下列其中一個動作：

   - 在 C# 中鍵入 `///`，或在 Visual Basic 中鍵入 `'''`

   - 從 [編輯]**** 功能表上，選擇 [IntelliSense]**** > [插入註解]****

   - 從代碼元素上方或代碼元素上方的按右鍵或內容功能表中，選擇 **"程式碼片段** > **插入注釋"**

   XML 範本會立即在程式碼項目上方產生。 例如，在注釋方法時，它生成**\<摘要\>** 元素、每個參數的**\<\>參數**元素和**\<用於\>** 記錄傳回值的返回元素。

   ![XML 註解範本 - C#](media/doc-preview-cs.png)

   ![XML 註解範本 - Visual Basic](media/doc-preview-vb.png)

3. 為每個 XML 項目輸入描述，以完整記錄程式碼項目。

   ![已完成的註解](media/doc-result-cs.png)

您可以在 XML 注釋中使用樣式，這些樣式在懸停在元素上時將在"快速資訊"中呈現。 這些樣式包括：斜體、粗體、專案符號和可按一下連結。

   ![已完成的註解](media/doc-style-cs.png) 

> [!NOTE]
> 在 C# 鍵入 `///` 或在 Visual Basic 鍵入 `'''` 之後，會有切換 XML 文件註解的[選項](../../ide/reference/options-text-editor-csharp-advanced.md)。 從功能表列中，選擇 **"工具** > **選項**"以打開"**選項**"對話方塊。 然後，導航到**文字編輯器** > **C#** 或**基本** > **高級**。 在 [編輯器說明]**** 區段中，尋找 [產生 XML 文件註解]**** 選項。

## <a name="see-also"></a>另請參閱

- [XML 文件註解 (C# 程式設計指南)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [使用 XML 註解記錄您的程式碼 (C# 指南)](/dotnet/csharp/codedoc)
- [如何：建立 XML 文件 (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [C++ 註解](/cpp/cpp/comments-cpp)
- [XML 文件 (C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [產生程式碼](../code-generation-in-visual-studio.md)
