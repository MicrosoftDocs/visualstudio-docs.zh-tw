---
title: "如何：尋找並組織專案範本和項目範本 | Microsoft Docs"
ms.custom: 
ms.date: 06/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project templates [Visual Studio], locations
- custom template locations [Visual Studio]
- item templates, locations
- Visual Studio templates, locations
- project templates [Visual Studio], displaying
- templates [Visual Studio], locations
ms.assetid: 71f9ed52-c9c9-4818-9bce-c279ffaa0438
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e4f3388d7484021bd4c12e4a7273b312190bd6dd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>如何：尋找並組織專案範本和項目範本
範本檔案必須放在 Visual Studio 可以辨識的位置，以便範本將出現在 [新增專案] 和 [新增項目] 對話方塊中。 您可以建立範本的自訂子類別，因此子類別也會出現在使用者介面中。  

## <a name="locating-templates"></a>尋找範本  
 依預設，Visual Studio 會在兩個位置搜尋專案和項目範本。 如果包含 .vstemplate 檔案的壓縮檔存在於這些位置中，範本將出現在 [新增專案] 或 [新增項目] 對話方塊中。  

### <a name="installed-templates"></a>已安裝的範本  
 依預設，與產品一起安裝的範本位於：  

-   \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\\<語言>\\<地區設定>\  

-   \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\\<語言>\\<地區設定>*\\*  

 例如，下列目錄包含英文的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案範本：  

 C:\\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\VisualBasic\1033\  

### <a name="custom-templates"></a>自訂範本  
 依預設，自訂範本位於：  

-   \My Documents\Visual Studio *Version*\Templates\ProjectTemplates\\<語言>\  

-   \My Documents\Visual Studio <版本>\Templates\ItemTemplates\\<語言>\  

 例如，下列目錄包含自訂的 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 專案範本：  

 C:\Documents and Settings\UserName\My Documents\Visual Studio <版本>\Templates\ProjectTemplates\Visual C#\  

 自訂範本不包含當地語系化之範本的子目錄。 您可以在 [選項] 對話方塊的 [環境\專案和方案] 下變更自訂範本的預設目錄。  

## <a name="organizing-templates"></a>組織範本  
 [新增專案] 和 [新增項目] 對話方塊中的類別反映存在於已安裝和自訂範本位置的目錄結構。 您可以修改這些目錄結構，以對您有意義的方式組織範本。  

> [!NOTE]
>  您無法在程式設計語言層級建立新的類別。 只能在每一種語言內建立新的類別。  

 如果特定語言的已安裝和自訂範本的目錄結構沒有相同的結構 (也就是某個資料夾下有不存在於其他資料夾下的目錄)，則出現在 [新增專案] 對話方塊的類別集將合併所有類別。  

### <a name="organizing-installed-templates"></a>組織已安裝的範本  
 您可以在程式設計語言資料夾中建立子目錄，組織已安裝的範本。 這些子目錄會出現在 [新增專案] 和 [新增項目] 對話方塊中，作為每種語言內的虛擬資料夾。  

##### <a name="to-create-new-installed-project-template-categories"></a>建立新的已安裝專案範本類別  

1.  在已安裝的範本目錄的語言資料夾中建立資料夾。 例如，若要為 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案範本建立 Office 類別，您將建立下列目錄：  

     \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\VisualBasic\1033\Office\  

2.  將此類別的所有範本都放在新資料夾中。  

3.  關閉 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的所有執行個體。  

4.  在 [開始] 功能表上，按一下 [執行]、鍵入 **cmd**，然後按一下 [確定]。  

5.  在命令提示字元中，找出包含 devenv.exe 的目錄，然後鍵入 **devenv /installvstemplates**。  

6.  執行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  

7.  按一下 [ **檔案** ] 功能表上的 [ **新增**]，然後按一下 [ **專案**]。  

8.  確認 Office 類別出現在 [新增專案] 對話方塊中，位於 [專案類型] 窗格的 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 底下。  

 您也可以將專案項目範本子集分組成自訂資料夾。  

##### <a name="to-create-new-installed-item-template-categories"></a>建立新的已安裝項目範本類別  

1.  在已安裝的範本目錄的語言資料夾中建立資料夾。 例如，若要為 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 項目範本建立 Web 類別，您將建立下列目錄：  

     \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\CSharp\1033\Web\  

2.  將此類別的所有範本放在新資料夾中。  

3.  關閉 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的所有執行個體。  

4.  在 [開始] 功能表上，按一下 [執行]、鍵入 **cmd**，然後按一下 [確定]。  

5.  在命令提示字元中，找出包含 devenv.exe 的目錄，然後鍵入 **devenv /setup**。  

6.  執行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  

7.  建立專案或開啟現有專案。  

8.  在 [專案]  功能表中，按一下 [加入新項目] 。  

9. 確認 Web 類別出現在 [新增項目] 對話方塊的 [專案類型] 窗格中。  

### <a name="organizing-custom-templates"></a>組織自訂範本  
 自訂範本可在自訂範本位置加入新的資料夾來組織成專屬類別 [新增專案] 對話方塊會反映您對範本類別所做的任何變更。  

##### <a name="to-create-new-custom-project-template-categories"></a>建立新的自訂專案範本類別  

1.  在自訂專案範本目錄的語言資料夾中建立資料夾。 例如，若要為 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 範本建立 HelloWorld 類別，您將建立下列目錄：  

     \My Documents\Visual Studio <版本>\Templates\ProjectTemplates\CSharp\HelloWorld\  

2.  將此類別的所有範本都放在新資料夾中。  

3.  按一下 [ **檔案** ] 功能表上的 [ **新增**]，然後按一下 [ **專案**]。  

4.  確認 HelloWorld 類別出現在 [新增專案] 對話方塊中，位於 [專案類型] 窗格的 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 底下。  

 您也可以將自訂項目範本子集分組成自訂資料夾。  

##### <a name="to-create-new-custom-item-template-categories"></a>建立新的自訂項目範本類別  

1.  在自訂項目範本目錄的語言資料夾中建立資料夾。 例如，若要為 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 範本建立 HelloWorld 類別，您將建立下列目錄：  

     \My Documents\Visual Studio <版本>\Templates\ItemTemplates\CSharp\HelloWorld\  

2.  將此類別的所有範本都放在新資料夾中。  

3.  建立專案或開啟現有專案。  

4.  在 [專案]  功能表中，按一下 [加入新項目] 。  

5.  確認 HelloWorld 類別出現在 [新增項目] 對話方塊的 [專案類型] 窗格中。  

### <a name="displaying-templates-in-parent-categories"></a>在父類別中顯示範本  
 您可以使用 .vstemplate 檔案中的 `NumberOfParentCategoriesToRollUp` 項目，讓子類別中的範本可以顯示在其父類別中。 對於專案範本和項目範本而言，這些步驟都相同。  

##### <a name="to-display-templates-in-parent-categories"></a>在父類別中顯示範本  

1.  找出包含樣板的.zip 檔。  

2.  將 zip 檔解壓縮。  

3.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中開啟 .vstemplate 檔案。  

4.  在 `TemplateData` 項目中，加入 `NumberOfParentCategoriesToRollUp` 項目。 例如，下列程式碼可讓您在父類別中看到範本，但不得高於此類別。  

    ```  
    <TemplateData>  
        ...  
        <NumberOfParentCategoriesToRollUp>  
            1  
        </NumberOfParentCategoriesToRollUp>  
        ...  
    </TemplateData>  
    ```  

5.  儲存並關閉.vstemplate 檔案。  

6.  在範本中選取檔案，在選取項目上按一下滑鼠右鍵，按一下 [傳送到]，然後按一下 [壓縮的 (zipped) 資料夾]。 檔案即會壓縮成 .zip 檔案。  

7.  刪除已解壓縮的樣板檔案和舊樣板 .zip 檔案。  

8.  將新的.zip 檔案放在有已刪除 .zip 檔案的目錄。  

## <a name="see-also"></a>請參閱  
 [自訂範本](../ide/customizing-project-and-item-templates.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [NumberOfParentCategoriesToRollUp (Visual Studio 範本)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)   
 [如何：建立專案範本](../ide/how-to-create-project-templates.md)   
 [如何：建立項目範本](../ide/how-to-create-item-templates.md)
