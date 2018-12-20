---
title: 組織範本
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], locations
- item templates [Visual Studio], locations
- template locations [Visual Studio]
- Visual Studio templates, organizing
- templates [Visual Studio], organizing
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: c6bca61dd88b164fcae2b2ccb7e2a98086bf102b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066284"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>HOW TO：尋找及整理專案與項目範本

範本檔案必須放在 Visual Studio 可以辨識的位置，這樣範本才會出現在 [新增專案] 和 [新增項目] 對話方塊中。 您也可以在使用者範本位置中建立自訂的子目錄，且目錄會顯示在 [新增專案] 和 [新增項目] 對話方塊中。

## <a name="locate-templates"></a>尋找範本

已安裝的範本和使用者範本會儲存在兩個不同的位置。

### <a name="user-templates"></a>使用者範本

如果您將包含 *.vstemplate* 檔案的壓縮檔 (*.zip*) 新增到使用者範本目錄，範本將出現在 [新增專案] 或 [新增項目] 對話方塊中。 根據預設，自訂範本位於：

- *%USERPROFILE%\Documents\Visual Studio \<版本\>\Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual Studio \<版本\>\Templates\ItemTemplates*

例如，下列目錄有 C# 的使用者專案範本：

- *C:\Users\UserName\Documents\Visual Studio 2017\Templates\ProjectTemplates\Visual C#*

> [!TIP]
> 您可以在 [工具] > [選項] > [專案和方案] >  [位置] 中設定使用者範本的位置。

### <a name="installed-templates"></a>已安裝的範本

根據預設，與 Visual Studio 一起安裝的範本位於：

- *\\<VisualStudioInstallationDirectory\>\Common7\IDE\ItemTemplates\\<程式設計語言\>\\<Locale ID>*

- *\\<VisualStudioInstallationDirectory\>\Common7\IDE\ProjectTemplates\\<程式設計語言\>\\<Locale ID>*

例如，下列目錄有適用於英文的 Visual Basic 項目範本 (LCID 1033)：

- *C:\\<Visual Studio 安裝目錄\>\Common7\IDE\ItemTemplates\VisualBasic\1033*

## <a name="organize-templates"></a>組織範本

[新增專案] 和 [新增項目] 對話方塊中的類別，反映已安裝範本和使用者範本位置中的目錄結構。 在使用者範本目錄新增資料夾，可將使用者範本組織成專屬類別。 [新增專案] 和 [新增項目] 對話方塊會顯示您對使用者範本類別所做的任何變更。

> [!NOTE]
> 您無法在程式設計語言層級建立新的類別。 只能在每一種語言內建立新的類別。

### <a name="to-create-new-user-project-template-categories"></a>建立新的使用者專案範本類別

1. 在使用者專案範本目錄的程式設計語言資料夾中建立資料夾。 例如，若要為 C# 專案範本建立 **HelloWorld** 類別，請建立下列目錄：

    - *\%USERPROFILE%\Documents\Visual Studio \<版本\>\Templates\ProjectTemplates\Visual C#\HelloWorld*

1. 將此類別的所有範本都放在新資料夾中。

1. 在 [檔案] 功能表上，選擇 [新增] > [專案]。

   **HelloWorld** 類別隨即出現在 [新增專案] 對話方塊下的 [已安裝] > [Visual C#] 中。

### <a name="to-create-new-user-item-template-categories"></a>建立新的使用者項目範本類別

1. 在使用者項目範本目錄的程式設計語言資料夾中建立資料夾。 例如，若要為 C# 項目範本建立 **HelloWorld** 類別，請建立下列目錄：

    - *\%USERPROFILE%\Documents\Visual Studio \<版本\>\Templates\ItemTemplates\Visual C#\HelloWorld*

1. 將此類別的所有範本都放在新資料夾中。

1. 建立專案或開啟現有專案。 在 [專案] 功能表中，選擇 [新增項目]。

   **HelloWorld** 類別隨即出現在 [新增項目] 對話方塊下的 [已安裝] > [Visual C# 項目] 中。

### <a name="display-templates-in-parent-categories"></a>在父類別中顯示範本

您可以使用 *.vstemplate* 檔案中的 `NumberOfParentCategoriesToRollUp` 項目，讓子分類中的範本可以顯示在其父分類中。 對於專案範本和項目範本而言，這些步驟都相同。

#### <a name="to-display-templates-in-parent-categories"></a>在父類別中顯示範本

1. 尋找包含範本的 *.zip* 檔。

1. 解壓縮 *.zip* 檔。

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

1. 在範本中選取檔案，以滑鼠右鍵按一下選項，選擇 [Send to] (傳送至) > [壓縮的 (zipped) 資料夾]。

   檔案即會壓縮成 *.zip* 檔案。

1. 刪除已解壓縮的範本檔案和舊範本 *.zip* 檔案。

1. 將新的 *.zip* 檔案放在有已刪除 *.zip* 檔案的目錄。

## <a name="see-also"></a>另請參閱

- [自訂範本](../ide/customizing-project-and-item-templates.md)
- [Visual Studio 範本結構描述參考 (擴充性)](../extensibility/visual-studio-template-schema-reference.md)
- [NumberOfParentCategoriesToRollUp (Visual Studio 範本)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)
- [如何：建立專案範本](../ide/how-to-create-project-templates.md)
- [如何：建立項目範本](../ide/how-to-create-item-templates.md)