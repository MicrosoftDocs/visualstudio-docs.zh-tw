---
title: "整理 Visual Studio 中的範本 | Microsoft Docs"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project templates [Visual Studio], locations
- item templates [Visual Studio], locations
- template locations [Visual Studio]
- Visual Studio templates, organizing
- templates [Visual Studio], organizing
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 167ffa269ea8051a4791000d96a86cb5788af60d
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>如何：尋找並整理專案範本和項目範本

範本檔案必須放在 Visual Studio 可以辨識的位置，所以範本要出現在 [新增專案] 和 [新增項目] 對話方塊中。 您可以建立範本的自訂子類別，它們也會出現在對話方塊中。

## <a name="locating-templates"></a>尋找範本

已安裝的範本和使用者範本會儲存在兩個不同的位置。 如果包含 .vstemplate 檔案的壓縮檔存在於這些位置中，範本將出現在 [新增專案] 或 [新增項目] 對話方塊中。

> [!TIP]
> 您可以在 [工具] > [選項] > [專案和方案] >  [位置] 中設定使用者範本的位置。

### <a name="installed-templates"></a>已安裝的範本

根據預設，與 Visual Studio 一起安裝的範本位於：

- \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\\式設計語言*程*\\地區設定識別碼

- \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\\程式設計語言\\地區設定識別碼

例如，下列目錄包含適用於英文的 Visual Basic 項目範本 (LCID 1033)：

   C:\\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\VisualBasic\1033\

### <a name="user-templates"></a>使用者範本

根據預設，自訂範本位於：

- %USERPROFILE%\Documents\Visual Studio \<版本\>\Templates\ProjectTemplates

- %USERPROFILE%\Documents\Visual Studio \<版本\>\Templates\ItemTemplates

例如，下列目錄包含 C# 的使用者專案範本：

   C:\Users\UserName\Documents\Visual Studio 2017\Templates\ProjectTemplates\Visual C#\

> [!NOTE]
> 使用者範本位置不包含當地語系化範本的地區設定子目錄。

您可以在 [選項] 對話方塊的 [專案和方案] > [位置] 中變更使用者範本的預設目錄。

## <a name="organizing-templates"></a>整理範本

[新增專案] 和 [新增項目] 對話方塊中的類別，反映已安裝範本和使用者範本位置中的目錄結構。 您可以修改這些目錄結構，以對您有意義的方式組織範本。

> [!NOTE]
> 您無法在程式設計語言層級建立新的類別。 只能在每一種語言內建立新的類別。

> [!NOTE]
> 如果特定語言的已安裝和使用者範本目錄結構不一樣 (亦即一個資料夾下有目錄而另一個沒有)，則所有類別都會顯示在 [新增專案] 對話方塊中。

### <a name="organizing-user-templates"></a>整理使用者範本

在使用者範本位置新增資料夾，可將使用者範本整理成專屬類別。 [新增專案] 對話方塊會反映您對範本類別所做的任何變更。

#### <a name="to-create-new-user-project-template-categories"></a>建立新的使用者專案範本類別

1. 在使用者專案範本目錄的程式設計語言資料夾中建立資料夾。 例如，若要為 C# 專案範本建立 **HelloWorld** 類別，請建立下列目錄：

    \%USERPROFILE%\Documents\Visual Studio \<版本\>\Templates\ProjectTemplates\Visual C#\HelloWorld\

1. 將此類別的所有範本都放在新資料夾中。

1. 在 [檔案] 功能表上，選擇 [新增] > [專案]。

   **HelloWorld** 類別隨即出現在 [新增專案] 對話方塊下的 [已安裝] > [Visual C#] 中。

#### <a name="to-create-new-user-item-template-categories"></a>建立新的使用者項目範本類別

1. 在使用者項目範本目錄的程式設計語言資料夾中建立資料夾。 例如，若要為 C# 項目範本建立 **HelloWorld** 類別，請建立下列目錄：

    \%USERPROFILE%\Documents\Visual Studio \<版本\>\Templates\ItemTemplates\Visual C#\HelloWorld\

1. 將此類別的所有範本都放在新資料夾中。

1. 建立專案或開啟現有專案。 在 [專案] 功能表中，選擇 [新增項目]。

   **HelloWorld** 類別隨即出現在 [新增項目] 對話方塊下的 [已安裝] > [Visual C# 項目] 中。

### <a name="displaying-templates-in-parent-categories"></a>在父類別中顯示範本

您可以使用 .vstemplate 檔案中的 `NumberOfParentCategoriesToRollUp` 項目，讓子類別中的範本可以顯示在其父類別中。 對於專案範本和項目範本而言，這些步驟都相同。

#### <a name="to-display-templates-in-parent-categories"></a>在父類別中顯示範本

1. 找出包含樣板的.zip 檔。

1. 將 zip 檔解壓縮。

1. 在 Visual Studio 中開啟 .vstemplate 檔案。

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

1. 儲存並關閉.vstemplate 檔案。

1. 在範本中選取檔案，以滑鼠右鍵按一下選項，選擇 [Send to] (傳送至) > [壓縮的 (zipped) 資料夾]。

   檔案即會壓縮成 .zip 檔案。

1. 刪除已解壓縮的樣板檔案和舊樣板 .zip 檔案。

1. 將新的.zip 檔案放在有已刪除 .zip 檔案的目錄。

## <a name="see-also"></a>另請參閱

[自訂範本](../ide/customizing-project-and-item-templates.md)  
[Visual Studio 範本結構描述參考 (擴充性)](../extensibility/visual-studio-template-schema-reference.md)  
[NumberOfParentCategoriesToRollUp (Visual Studio 範本)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)  
[如何：建立專案範本](../ide/how-to-create-project-templates.md)  
[如何：建立項目範本](../ide/how-to-create-item-templates.md)
