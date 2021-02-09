---
title: 建立多檔案項目範本
description: 瞭解如何在由多個檔案組成的 Visual Studio 中建立專案範本。
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: b375cf54dfe35928a35f991190c94b3d08685827
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875376"
---
# <a name="how-to-create-multi-file-item-templates"></a>如何：建立多檔案項目範本

項目範本只能指定一個項目，但有時項目是由多個檔案所構成。 例如，Windows Forms 項目範本需要下列三個檔案：

- 一個包含表單程式碼的檔案

- 一個包含表單設計工具資訊的檔案

- 一個包含表單內嵌資源的檔案

多檔案項目範本需要參數，確保建立項目時使用正確的檔案副檔名。 如果您使用 [匯出範本精靈] 建立多檔案項目範本，就會自動產生這些參數，而且不需要進行任何進一步編輯。

## <a name="use-the-export-template-wizard"></a>使用 [匯出範本精靈]

建立多檔案項目範本使用的方式和建立單一檔案項目範本一樣。 請參閱[如何：建立項目範本](../ide/how-to-create-item-templates.md)。 在精靈的 [選取要匯出的項目] 頁面中，選取有相依檔案的檔案 (例如，Windows Forms 表單檔案)。 精靈會自動納入範本的所有相依檔案，例如設計工具和資源檔。

## <a name="manually-create-a-multi-file-item-template"></a>手動建立多檔案項目範本

1. 以手動建立單一檔案項目範本的方式建立項目範本，但包含構成多檔案項目的每一個檔案。

1. 在 *.vstemplate* XML 檔案中，為每個個別的檔案新增 `ProjectItem` 項目，並在此項目中新增 `TargetFileName` 屬性。 將 `TargetFileName` 屬性的值設為 *$fileinputname$.FileExtension*，其中 *FileExtension* 是範本中所含檔案的檔案副檔名。 例如：

    ```xml
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

     > [!NOTE]
     > 將衍生自此範本的項目新增至專案時，檔案名稱會衍生自使用者在 [新增項目] 對話方塊中輸入的名稱。

1. 選取要包含在範本中的檔案，在選取專案上按一下滑鼠右鍵，然後選擇 [**傳送到**  >  **壓縮的 (壓縮的) 資料夾**。

   您選取的檔案會壓縮成 *.zip* 檔案。

1. 將 *.zip* 檔案複製到使用者項目範本的位置。 依預設，此目錄為 *%USERPROFILE%\Documents\Visual Studio \<Version\> \Templates\ItemTemplates*。 如需詳細資訊，請參閱[如何：尋找並整理範本](../ide/how-to-locate-and-organize-project-and-item-templates.md)。

1. 結束再重新開啟 Visual Studio。

1. 建立新的專案，或開啟現有的專案，然後選擇 [ **project**  >  **加入新專案**] 或按 **Ctrl** + **Shift** + **a**。

   多檔案項目範本即會出現在 [新增項目] 對話方塊中。

## <a name="example"></a>範例

下例示範 Windows Forms 範本。 根據此範本來建立項目時，所建立三個檔案的名稱會符合 [新增項目] 對話方塊中所輸入的名稱。

```xml
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

- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [如何：建立專案範本](../ide/how-to-create-item-templates.md)
- [範本參數](../ide/template-parameters.md)
- [如何：替代範本中的參數](../ide/how-to-substitute-parameters-in-a-template.md)
