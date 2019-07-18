---
title: 作法：建立多檔案項目範本 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c6c6dde1880881bfb236909fde6ce6deb6bf596f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201839"
---
# <a name="how-to-create-multi-file-item-templates"></a>作法：建立多檔案項目範本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

項目範本只能指定一個項目，但有時項目是由多個檔案所構成。 例如，Visual Basic 的 Windows Forms 項目範本需要下列三個檔案：  
  
- 包含表單程式碼的.vb 檔案。  
  
- 包含表單設計工具資訊的 .designer.vb 檔案。  
  
- 包含表單內嵌資源的 .resx 檔案。  
  
  多檔案項目範本需要參數，確保在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中建立項目時使用正確的檔案名稱副檔名。 如果您使用 [匯出範本精靈]  建立項目範本，則會自動產生這些參數，而且不需要進行任何進一步編輯。 下列步驟說明如何使用參數，確保建立正確的檔案名稱副檔名。  
  
### <a name="to-manually-create-a-multi-file-item-template"></a>手動建立多檔案項目範本  
  
1. 當您建立單一檔案項目範本，請建立項目範本。 如需詳細資訊，請參閱[如何：建立項目範本](../ide/how-to-create-item-templates.md)。  
  
2. 將 `TargetFileName` 屬性新增至每個 `ProjectItem` 項目。 將 `TargetFileName` 屬性的值設為 $fileinputname$.*FileExtension*，其中 *FileExtension* 是範本中所含檔案的檔案名稱副檔名。 例如：  
  
    ```  
    <ProjectItem TargetFileName="$fileinputname$.vb">  
        Form1.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
        Form1.Designer.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.resx">  
        Form1.resx  
    </ProjectItem>  
    ```  
  
     將衍生自此範本的項目新增至專案時，檔案名稱是根據使用者在 [新增項目]  對話方塊中鍵入的名稱。  
  
3. 選取要包含在範本中的檔案，並以滑鼠右鍵按一下選取項目，再按一下 [傳送到]  ，然後按一下 [壓縮的 (zipped) 資料夾]  。 您選取的檔案即會壓縮成 .zip 檔。  
  
4. 將 .zip 檔案放在使用者項目範本位置中。 此目錄預設為 \My Documents\Visual Studio <版本>  \Templates\ItemTemplates\\。 如需詳細資訊，請參閱[如何：尋找並整理範本](../ide/how-to-locate-and-organize-project-and-item-templates.md)。  
  
## <a name="example"></a>範例  
 下列範例示範 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Windows Forms 範本。 根據此範本來建立項目時，所建立三個檔案的名稱會符合 [新增項目]  對話方塊中所輸入的名稱。  
  
```  
<VSTemplate Version="2.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-file Item Template</Name>  
        <Icon>Icon.ico</Icon>  
        <Description>An example of a multi-file item template</Description>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem TargetFileName="$fileinputname$.vb" SubType="Form">  
            Form1.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
            Form1.Designer.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.resx">  
            Form1.resx  
        </ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>另請參閱  
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)   
 [如何：建立項目範本](../ide/how-to-create-item-templates.md)   
 [範本參數](../ide/template-parameters.md)   
 [如何：替代範本中的參數](../ide/how-to-substitute-parameters-in-a-template.md)
