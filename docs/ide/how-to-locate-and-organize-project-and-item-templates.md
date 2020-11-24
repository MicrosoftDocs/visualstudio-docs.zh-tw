---
title: 尋找範本
description: 瞭解如何尋找和組織專案範本和專案範本。
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- project templates [Visual Studio], locations
- item templates [Visual Studio], locations
- template locations [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 517918bf7e56381a4d4d2a36fc43f976a07c29ea
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597154"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>如何：尋找並整理專案範本和項目範本

範本檔案必須放在已知的位置，使其顯示在 [新增專案] 和 [新項目] 對話方塊中。

::: moniker range="vs-2017"

您也可以在使用者範本位置中建立自訂的子目錄，且目錄會顯示在 [新增專案] 和 [新增項目] 對話方塊中。

::: moniker-end

## <a name="locate-templates"></a>尋找範本

已安裝的範本和使用者範本會儲存在兩個不同的位置。

### <a name="installed-templates"></a>已安裝的範本

根據預設，與 Visual Studio 一起安裝的範本位於：

::: moniker range="vs-2017"

- *% ProgramFiles (x86) % \\ Microsoft Visual Studio \\ 2017 \\ \<edition> \\ Common7\IDE\ProjectTemplates \\<Language \> \\<地區設定識別碼\>*

- *% ProgramFiles (x86) % \\ Microsoft Visual Studio \\ 2017 \\ \<edition> \Common7\IDE\ItemTemplates \\<Language \> \\<地區設定識別碼\>*

例如，下列目錄有適用於英文的 Visual Basic 項目範本 (LCID 1033)：

*C:\\Program Files (x86)\\Microsoft Visual Studio\\2017\\Community\\Common7\\IDE\\ItemTemplates\\VisualBasic\\1033*

::: moniker-end

::: moniker range=">=vs-2019"

- *% ProgramFiles (x86) % \\ Microsoft Visual Studio \\ 2019 \\ \<edition> \\ Common7\IDE\ProjectTemplates \\<Language \> \\<地區設定識別碼\>*

- *% ProgramFiles (x86) % \\ Microsoft Visual Studio \\ 2019 \\ \<edition> \Common7\IDE\ItemTemplates \\<Language \> \\<地區設定識別碼\>*

例如，下列目錄有適用於英文的 Visual Basic 項目範本 (LCID 1033)：

*C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\Community\\Common7\\IDE\\ItemTemplates\\VisualBasic\\1033*

::: moniker-end

### <a name="user-templates"></a>使用者範本

如果您將包含 *.vstemplate* 檔案的壓縮檔 (*.zip*) 新增到使用者範本目錄，範本將出現在 [新增專案] 和 [新增項目] 對話方塊中。 根據預設，自訂範本位於：

::: moniker range="vs-2017"

- *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ItemTemplates*

例如，下列目錄有 C# 的使用者專案範本：

- *C:\Users\UserName\Documents\Visual Studio 2017\Templates\ProjectTemplates\Visual C#*

::: moniker-end

::: moniker range=">=vs-2019"

- *%USERPROFILE%\Documents\Visual Studio 2019\Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual Studio 2019\Templates\ItemTemplates*

例如，下列目錄有 C# 的使用者專案範本：

- *C:\Users\UserName\Documents\Visual Studio 2019\Templates\ProjectTemplates\Visual C#*

::: moniker-end

> [!TIP]
> 您可以在 [**工具**  >  **選項**]  >  **專案和方案**  >  **位置** 中變更使用者範本的已知位置。

::: moniker range="vs-2017"

## <a name="organize-templates"></a>組織範本

[新增專案] 和 [新增項目] 對話方塊中的類別，反映已安裝範本和使用者範本位置中的目錄結構。 在使用者範本目錄新增資料夾，可將使用者範本組織成專屬類別。 [新增專案] 和 [新增項目] 對話方塊會顯示您對使用者範本類別所做的任何變更。

> [!NOTE]
> 您無法在程式設計語言層級建立新的類別。 只能在每一種語言內建立新的類別。

### <a name="create-new-user-project-template-categories"></a>建立新的使用者專案範本類別

1. 在使用者專案範本目錄的程式設計語言資料夾中建立資料夾。 例如，若要為 C# 專案範本建立 **HelloWorld** 類別，請建立下列目錄：

    - *\%USERPROFILE%\Documents\Visual Studio \<Version\> \Templates\ProjectTemplates\Visual c # \HelloWorld*

1. 將此類別的所有範本都放在新資料夾中。

1. 在 [檔案] 功能表上，依序選擇 [新增]**和 [專案]** > 。

   **HelloWorld** 類別隨即出現在 [新增專案] 對話方塊下的 [已安裝]**[Visual C#]** >  中。

### <a name="create-new-user-item-template-categories"></a>建立新的使用者項目範本類別

1. 在使用者項目範本目錄的程式設計語言資料夾中建立資料夾。 例如，若要為 C# 項目範本建立 **HelloWorld** 類別，請建立下列目錄：

    - *\%USERPROFILE%\Documents\Visual Studio \<Version\> \Templates\ItemTemplates\Visual c # \HelloWorld*

1. 將此類別的所有範本都放在新資料夾中。

1. 建立專案或開啟現有專案。 在 [專案] 功能表中，選擇 [新增項目]。

   **HelloWorld** 類別隨即出現在 [新增項目] 對話方塊下的 [已安裝]**[Visual C# 項目]** >  中。

### <a name="display-templates-in-parent-categories"></a>在父類別中顯示範本

您可以使用 *.vstemplate* 檔案中的 `NumberOfParentCategoriesToRollUp` 項目，讓子分類中的範本可以顯示在其父分類中。 對於專案範本和項目範本而言，這些步驟都相同。

1. 尋找包含範本的 *.zip* 檔。

1. 將 *.zip* 檔案解壓縮。

1. 在 Visual Studio 中開啟 *.vstemplate* 檔案。

1. 在 `TemplateData` 項目中，加入 `NumberOfParentCategoriesToRollUp` 項目。 例如，下列程式碼可讓您在父類別中看到範本，但不得高於此類別。

    ```xml
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

1. 儲存並關閉 *.vstemplate* 檔案。

1. 在範本中選取檔案，以滑鼠右鍵按一下選項，選擇 [傳送至] **[壓縮的 (zipped) 資料夾]** > 。

   檔案會壓縮成 *.zip* 檔案。

1. 刪除已解壓縮的範本檔案和舊的範本 *.zip* 檔。

1. 將新的 *.zip* 檔案放在有已刪除 *.zip* 檔案的目錄。

::: moniker-end

## <a name="see-also"></a>另請參閱

- [自訂範本](../ide/customizing-project-and-item-templates.md)
- [Visual Studio 範本結構描述參考 (擴充性)](../extensibility/visual-studio-template-schema-reference.md)
- [NumberOfParentCategoriesToRollUp (Visual Studio 範本)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)
- [如何：建立專案範本](../ide/how-to-create-project-templates.md)
- [如何：建立專案範本](../ide/how-to-create-item-templates.md)
