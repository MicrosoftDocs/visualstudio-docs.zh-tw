---
title: 建立多檔案項目範本
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1871b7270c462ea599450e48f0a86a4887ebc5ac
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55970513"
---
# <a name="how-to-create-multi-file-item-templates"></a>HOW TO：建立多重檔案項目範本

項目範本只能指定一個項目，但有時項目是由多個檔案所構成。 例如，Windows Forms 項目範本需要下列三個檔案：

- 一個包含表單程式碼的檔案

- 一個包含表單設計工具資訊的檔案

- 一個包含表單內嵌資源的檔案

多檔案項目範本需要參數，確保建立項目時使用正確的檔案副檔名。 如果您使用 [匯出範本精靈] 建立多檔案項目範本，就會自動產生這些參數，而且不需要進行任何進一步編輯。

## <a name="to-create-a-multi-file-item-template-by-using-the-export-template-wizard"></a>使用 [匯出範本精靈] 建立多檔案項目範本

建立多檔案項目範本使用的方式和建立單一檔案項目範本一樣。 請參閱[如何：建立項目範本](../ide/how-to-create-item-templates.md)。 在精靈的 [選取要匯出的項目] 頁面中，選取有相依檔案的檔案 (例如，Windows Forms 表單檔案)。 精靈會自動納入範本的所有相依檔案，例如設計工具和資源檔。

## <a name="to-manually-create-a-multi-file-item-template"></a>手動建立多檔案項目範本

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

1. 選取要包含在範本中的檔案，以滑鼠右鍵按一下選項，選擇 [Send to] (傳送至) > [壓縮的 (zipped) 資料夾]。

   您選取的檔案即會壓縮成 *.zip* 檔。

1. 將 *.zip* 檔案複製到使用者項目範本的位置。 此目錄預設為 *%USERPROFILE%\Documents\Visual Studio \<版本\>\Templates\ItemTemplates*。 如需詳細資訊，請參閱[＜How to：尋找並整理範本](../ide/how-to-locate-and-organize-project-and-item-templates.md)。

1. 結束再重新開啟 Visual Studio。

1. 建立新的專案或開啟現有的專案，然後選擇 [專案] > [新增項目] 或按 **Ctrl**+**Shift**+**A**。

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
- [如何：建立項目範本](../ide/how-to-create-item-templates.md)
- [範本參數](../ide/template-parameters.md)
- [如何：替代範本中的參數](../ide/how-to-substitute-parameters-in-a-template.md)