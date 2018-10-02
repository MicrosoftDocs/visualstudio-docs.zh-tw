---
title: 如何：建立項目範本 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project item templates, XML reference
- project item templates, custom template locations
- project item templates, creating
- project item templates, metadata files
ms.assetid: 77bc53d4-d607-4820-a032-7e3b365891b5
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d16591f7650aec3eaebf08e1330b74dd425cc572
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488268"
---
# <a name="how-to-create-item-templates"></a>如何：建立項目範本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的[第一個程序](../ide/how-to-create-item-templates.md#export_template)步驟，說明如何使用 [匯出範本精靈] 建立項目範本。 如果您的範本中包含多個檔案，請參閱[如何：建立多檔案項目範本](../ide/how-to-create-multi-file-item-templates.md)。  
  
 此精靈會執行許多工作，為您建立基本範本，但在許多情況下，您將需要在匯出了範本之後手動修改.vstemplate 檔案。 例如，如果您想要在 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 應用程式專案的 [新增項目] 對話方塊中顯示項目，您必須執行一些額外的步驟。 本主題的[第二個程序](../ide/how-to-create-item-templates.md#modify_template)可協助您完成上述工作。  
 
 在某些情況下，您可能想要或需要從頭開始手動建立項目範本。 [第三個程序](../ide/how-to-create-item-templates.md#create_template)說明如何執行上述作業。  
  
 如需可用於 .vstemplate 檔案中的項目資訊，請參閱 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)。  
  
### <a name="to-add-a-custom-project-item-template-to-the-add-new-item-dialog-box"></a>若要將自訂專案項目範本加入至加入新項目對話方塊  
  
1.  在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中建立或開啟專案。  
  
2.  將項目加入至專案，並於需要時修改。  
  
3.  修改程式碼檔，指出要執行參數取代的地方。 如需詳細資訊，請參閱[如何：替代範本中的參數](../ide/how-to-substitute-parameters-in-a-template.md)。  
  
4.  按一下 [檔案] 功能表上的 [匯出範本]。  
  
5.  按一下 [項目範本]，然後選取包含項目的專案，並按一下 [下一步]。  
  
6.  選取要建立範本的項目，並按一下 [下一步]。  
  
7.  選取組件參考，以便在範本中包含此參考，然後按一下 [下一步]。  
  
8.  輸入圖示檔檔名、預覽影像、範本名稱和範本描述，然後按一下 [完成]。  
  
     範本檔案會加入至.zip 檔案，並複製至您在對話方塊中指定的任何目錄。 預設位置為 **..\Users\\<使用者名稱\>\Documents\Visual Studio \<>\My Exported Templates\\** 資料夾。  
  
    > [!WARNING]
    >  在舊版 Visual Studio 中，預設位置為 **..\Users\\<使用者名稱\>\Documents\Visual Studio \<版本>\Templates\ItemTemplates**。  
  
### <a name="to-enable-the-item-template-to-be-used-in-a-store-project"></a>若要讓項目範本可在市集專案中使用  
  
1.  遵循上述程序的步驟匯出項目範本。  
  
2.  從複製到 ..\Users\\<使用者名稱>\Documents\Visual Studio <版本>\Templates\ItemTemplates\ (或 **My Exported Templates**) 資料夾的 .zip 檔案，解壓縮 .vstemplate 檔案。  
  
3.  在 Visual Studio 中開啟 .vstemplate 檔案。  
  
4.  若為 Windows 8.1 市集 C#  專案，請在 .vstemplate 檔中的開頭和結尾 `<TemplateData>` 標記內，加入下列 XML：`<TemplateGroupID>WinRT-Managed</TemplateGroupID>`。  
  
     C + + Windows 8.1 市集專案使用 `WinRT-Native-6.3` 的值。 若為 Windows 10 及其他專案類型，請參閱 [TemplateGroupID 項目 (Visual Studio 範本)](../extensibility/templategroupid-element-visual-studio-templates.md)。  
  
     下列範例顯示已加入 XML `<TemplateGroupID>WinRT-Managed</TemplateGroupID>` 程式行之後 .vstemplate 檔案的完整內容。 這個範例是 C# 專案專用的。 您可以修改 <ProjectTpe> 和 \< [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)> 項目，來指定其他語言和專案類型。  
  
    ```xml  
    <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
      <TemplateData>  
        <DefaultName>MyItemStoreTemplate.xaml</DefaultName>  
        <Name>MyItemStoreTemplate</Name>  
        <Description>This is an example itemtemplate</Description>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>10</SortOrder>  
        <Icon>__TemplateIcon.ico</Icon>  
        <TemplateGroupID>WinRT-Managed</TemplateGroupID>  
      </TemplateData>  
      <TemplateContent>  
        <References />  
        <ProjectItem SubType="Designer" TargetFileName="$fileinputname$.xaml" ReplaceParameters="true">MyItemTemplate.xaml</ProjectItem>  
        <ProjectItem SubType="Code" TargetFileName="$fileinputname$.xaml.cs" ReplaceParameters="true">MyItemTemplate.xaml.cs</ProjectItem>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
     如需其他可能的 TemplateGroupID 值，請參閱 [TemplateGroupID 項目 (Visual Studio 範本)](../extensibility/templategroupid-element-visual-studio-templates.md))。 如需完整的 .vstemplate 參考，請參閱 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)。  
  
5.  在 Visual Studio 中，儲存並關閉 .vstemplate 檔案。  
  
6.  複製 .vstemplate 檔案，並將其貼至 ..\Users\\<使用者名稱>\Documents\Visual Studio <版本>\Templates\ItemTemplates\ 資料夾中的 .zip 檔案。  
  
     如果出現 [複製檔案] 對話方塊，請選擇 [複製並取代] 選項。  
  
 您現在可以使用 [新增項目] 對話方塊，將以這個範本為依據的項目新增至 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 專案。  
  
 如需參數名稱的詳細資訊，請參閱[範本參數](../ide/template-parameters.md)。  
  
### <a name="to-enable-templates-for-specific-project-sub-types"></a>若要啟用特定專案子類型的範本  
  
1.  開發環境可讓您使專案項目可從特定專案的 [加入項目] 對話方塊中取得。 使用此程序，可讓自訂項目可供 Windows、Web、Office 或資料庫專案使用。  
  
     在項目範本的.vstemplate 檔案中，找出 ProjectType 項目。  
  
     緊接著 ProjectType 項目之後加入 [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) 項目。  
  
2.  將項目的文字值設為下列其中一個值：  
  
    1.  Windows  
  
    2.  Office  
  
    3.  資料庫  
  
    4.  Web  
  
     例如：`<ProjectSubType>Database</ProjectSubType>`。  
  
     下列範例顯示可供 Office 專案使用的項目範本。  
  
    ```  
    <VSTemplate Version="2.0.0" Type="Item" Version="2.0.0">  
        <TemplateData>  
            <Name>Class</Name>  
            <Description>An empty class file</Description>  
            <Icon>Class.ico</Icon>  
            <ProjectType>CSharp</ProjectType>  
            <ProjectSubType>Office</ProjectSubType>  
            <DefaultName>Class.cs</DefaultName>  
        </TemplateData>  
        <TemplateContent>  
            <ProjectItem>Class1.cs</ProjectItem>  
        </TemplateContent>  
    </VSTemplate>  
  
    ```  
  
### <a name="to-manually-create-an-item-template-without-using-the-export-template-wizard"></a>若要手動建立項目範本而不使用 [匯出範本] 精靈  
  
1.  建立專案和專案項目。  
  
2.  修改專案項目，直到它準備好儲存成範本。  
  
3.  適時修改程式碼檔案，指出要執行參數取代的位置。 如需參數取代的詳細資訊，請參閱＜作法：替代範本中的參數＞。  
  
4.  在與新項目範本相同的目錄中，使用 .vstemplate 檔案副檔名來建立 XML 檔案並儲存它。  
  
5.  編寫 .vstemplate XML 檔案，以提供項目範本中繼資料。 如需詳細資訊，請參閱 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)和上一節中的範例。  
  
6.  儲存並關閉 .vstemplate 檔案。  
  
7.  在 Windows 的 [檔案總管] 中，選取您要併入範本中的檔案，以滑鼠右鍵按一下選取項目，按一下 [傳送到]，然後按一下 [壓縮的 (zipped) 資料夾]。 您選取的檔案即會壓縮成 .zip 檔。  
  
8.  複製 .zip 檔案，並在使用者項目範本位置中貼上它。 在 Visual Studio 2015 中，預設目錄是...\Users\\< 使用者名稱\>\Documents\Visual Studio 2015\Templates\ItemTemplates\\。 如需詳細資訊，請參閱＜作法：尋找並組織專案範本和項目範本＞。  
  
## <a name="see-also"></a>另請參閱  
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)   
 [如何：建立多檔案項目範本](../ide/how-to-create-multi-file-item-templates.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)