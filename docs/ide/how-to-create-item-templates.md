---
title: 建立項目範本
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- item templates [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: d921257e202e3b8175fcfd01910c00ece4306136
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952257"
---
# <a name="how-to-create-item-templates"></a>HOW TO：建立項目範本

本文會向您示範如何使用 [匯出範本精靈] 建立項目範本。 如果您的範本中包含多個檔案，請參閱[如何：建立多檔案項目範本](../ide/how-to-create-multi-file-item-templates.md)。

## <a name="to-add-a-user-item-template-to-the-add-new-item-dialog-box"></a>將使用者項目範本新增至 [新增項目] 對話方塊

1. 在 Visual Studio 中建立或開啟專案。

1. 如有需要，可將項目新增至專案並加以修改。

1. 修改程式碼檔，指出要執行參數取代的地方。 如需詳細資訊，請參閱[＜How to：替代範本中的參數](../ide/how-to-substitute-parameters-in-a-template.md)。

1. 選擇 [專案] 功能表上的 [匯出範本]。

1. 在 [選擇範本類型] 頁面上，選擇 [項目範本]，選取包含項目的專案，然後選擇 [下一步]。

1. 在 [選取要匯出的項目] 頁面上，選擇您想要建立範本的項目，然後選擇 [下一步]。

1. 在 [選取項目參考] 頁面上，選取要包含在範本中的組件參考，然後選擇 [下一步]。

1. 在 [選取範本選項] 頁面上，輸入範本名稱和選擇性描述、圖示影像和預覽影像，然後選擇 [完成]。

    範本檔案會新增至 *.zip* 檔案，並複製到您在精靈中指定的目錄。 預設位置是 *%USERPROFILE%\Documents\Visual Studio \<版本\>\My Exported Templates*。

1. 如果您未在 [匯出範本精靈] 中選取 [自動將範本匯入 Visual Studio] 選項，請尋找匯出的範本。 然後，將它複製到使用者項目範本目錄。 預設位置是 *%USERPROFILE%\Documents\Visual Studio \<版本\>\Templates\ItemTemplates*。

1. 結束再重新開啟 Visual Studio。

1. 建立新的專案或開啟現有的專案，然後選擇 [專案] > [新增項目] 或按 **Ctrl**+**Shift**+**A**。

   項目範本會出現在 [新增項目] 對話方塊中。 如已在 [匯出範本精靈] 中新增描述，該描述會出現在對話方塊的右邊。

## <a name="to-enable-the-item-template-to-be-used-in-a-universal-windows-app-project"></a>讓項目範本能在通用 Windows 應用程式專案中使用

此精靈為建立基本範本執行許多工作，但在許多情況下，您需要在匯出範本之後手動修改 *.vstemplate* 檔案。 例如，如果您希望項目出現在通用 Windows 應用程式專案的 [新增項目] 對話方塊中，您必須執行一些額外的步驟。

1. 遵循上一節中的步驟匯出項目範本。

1. 解壓縮已建立的 *.zip* 檔案，在 Visual Studio 中開啟 *.vstemplate* 檔案。

1. 若為 C# 通用 Windows 專案，請在 `<TemplateData>` 項目內新增下列 XML：

   ```xml
   <TemplateID>Microsoft.CSharp.Class</TemplateID>
   ```

1. 在 Visual Studio 中，儲存並關閉 *.vstemplate* 檔案。

1. 複製 *.vstemplate* 檔案，並貼回至 *.zip* 檔案。

     如果出現 [複製檔案] 對話方塊，請選擇 [複製並取代] 選項。

您現在可以根據此範本，從 [新增項目] 對話方塊將項目新增至通用 Windows 專案。

## <a name="to-enable-templates-for-specific-project-subtypes"></a>啟用特定專案子類型的範本

您可以指定範本只針對特定的專案子類型顯示，例如 Windows、Office、資料庫或 Web。

1. 在項目範本的 *.vstemplate* 檔案中，尋找 `ProjectType` 項目。

1. 緊接在 `ProjectType` 項目之後新增 [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) 項目。

1. 將項目的文字值設為下列其中一個值：

    - Windows
    - Office
    - 資料庫
    - Web

例如：`<ProjectSubType>Database</ProjectSubType>`。

下列範例顯示 **Office** 專案的項目範本。

```xml
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

## <a name="to-manually-create-an-item-template-without-using-the-export-template-wizard"></a>若要手動建立項目範本而不使用 [匯出範本] 精靈

在某些情況下，您可能想要從頭開始手動建立項目範本。

1. 建立專案和專案項目。

1. 修改專案項目，直到它準備好儲存成範本。

1. 修改程式碼檔案，指出要執行參數取代的位置 (如有)。 如需參數取代的詳細資訊，請參閱[如何：替代範本中的參數。](../ide/how-to-substitute-parameters-in-a-template.md)

1. 在與專案項目檔案相同的目錄中，使用 *.vstemplate* 檔案副檔名來建立並儲存 XML 檔案。

1. 編輯 *.vstemplate* XML 檔案，以提供項目範本中繼資料。 如需詳細資訊，請參閱[範本結構描述參考 (擴充性)](../extensibility/visual-studio-template-schema-reference.md) 和上一節中的範例。

1. 儲存並關閉 *.vstemplate* 檔案。

1. 在 **Windows 檔案總管**中選取您想要併入範本的檔案。 以滑鼠右鍵按一下選項，選擇 [傳送到] > [壓縮的 (zipped) 資料夾]。 您選取的檔案即會壓縮成 *.zip* 檔。

1. 複製 *.zip* 檔案，並在使用者項目範本位置中貼上它。 在 Visual Studio 2017 中，預設目錄是 *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ItemTemplates*。 如需詳細資訊，請參閱[＜How to：尋找及整理專案與項目範本](../ide/how-to-locate-and-organize-project-and-item-templates.md)。

## <a name="see-also"></a>另請參閱

- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [如何：建立多檔案項目範本](../ide/how-to-create-multi-file-item-templates.md)
- [Visual Studio 範本結構描述參考 (擴充性)](../extensibility/visual-studio-template-schema-reference.md)
