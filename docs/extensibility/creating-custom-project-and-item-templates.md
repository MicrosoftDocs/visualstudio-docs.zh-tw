---
title: 建立自訂專案和專案範本 |Microsoft Docs
description: 瞭解 Visual Studio SDK 中的範本建立範本如何讓您在較大的延伸模組中包含範本。
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: overview
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2dc5f347e3f5823613d11c8c217fcb2d29635867
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851344"
---
# <a name="create-custom-project-and-item-templates"></a>建立自訂專案和專案範本

Visual Studio SDK 包含專案範本，可建立自訂專案範本和自訂專案範本。 這些範本包含一些常見的參數替代，並以 zip 檔案的形式建立。 它們不會自動部署，而是在實驗實例中無法使用。 您必須將產生的 zip 檔案複製到使用者範本目錄。

範本建立範本可讓您將範本包含在較大的延伸模組中。 這可讓您在原始程式檔上執行版本控制，並將一組範本專案建立成一個 VSIX 套件。

您也可以設定範本來安裝 NuGet 套件。 如需詳細資訊，請參閱 [Visual Studio 範本中的 NuGet 套件](/nuget/visual-studio-extensibility/visual-studio-templates)。

在基本範本建立案例中，您應該使用匯出至壓縮檔案的 **匯出範本** wizard。 如需建立基本範本的詳細資訊，請參閱 [建立專案和專案範本](../ide/creating-project-and-item-templates.md)。

> [!NOTE]
> 從 Visual Studio 2017 開始，將不會再執行自訂專案和專案範本的掃描。 相反地，此延伸模組必須提供描述這些範本之安裝位置的範本資訊清單檔。 您可以使用 Visual Studio 2017 來更新 VSIX 擴充功能。 如果您使用 MSI 部署擴充功能，您必須手動產生範本資訊清單檔案。 如需詳細資訊，請參閱 [升級 Visual Studio 2017 的自訂專案和專案範本](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)。 範本資訊清單架構記載于 [Visual Studio 範本資訊清單架構參考](../extensibility/visual-studio-template-manifest-schema-reference.md)中。

## <a name="create-a-project-template"></a>建立專案範本

1. 建立專案範本專案。 您可以藉由搜尋「專案範本」並選取 c # 或 Visual Basic 版本，在 [ **新增專案** ] 對話方塊中找到專案範本。

     此範本會產生類別檔案、圖示、 *.vstemplate* 檔案、名為 *ProjectTemplate. vbproj* 或 *ProjectTemplate* 的可編輯專案檔，以及某些通常由其他專案類型產生的檔案，例如 *.resources* 檔案、 *AssemblyInfo* 檔和 *配置* 檔案。 每個程式碼檔案都包含適當的一般參數替代。

![專案範本專案選取專案](media/project-template-selection.png)

2. 視專案的需要，在專案中加入和移除專案。 請勿移除可編輯的專案檔、 *AssemblyInfo* 檔或 *.vstemplate* 檔案。

3. 更新 *.vstemplate* 檔案，以反映任何新增和刪除動作。 [專案專案](../extensibility/project-element-visual-studio-templates.md)必須包含範本中[](../extensibility/projectitem-element-visual-studio-item-templates.md)要包含之每個檔案的專案專案專案。

4. 修改您的程式碼檔案和其他使用者對應內容，並新增適當的參數替代。

5. 視需要修改產生的內容。

6. 建置專案。

     Visual Studio 建立包含您範本的 *.zip* 檔案。 它不會部署，而且在實驗實例中無法使用。

## <a name="create-an-item-template"></a>建立項目範本

1. 建立專案範本專案。

     此範本會產生類別檔案、圖示、 *.vstemplate* 檔案，以及 *AssemblyInfo* 檔案。 類別檔案包含一些常見的參數替代。

2. 視專案的需要，在專案中加入和移除專案。

3. 更新 *.vstemplate* 檔案，以反映任何新增和刪除動作。 [專案專案](../extensibility/project-element-visual-studio-templates.md)必須包含範本中[](../extensibility/projectitem-element-visual-studio-item-templates.md)要包含之每個檔案的專案專案專案。

4. 修改您的程式碼檔案和其他使用者對應內容，並新增適當的參數替代。

5. 視需要修改產生的內容。

6. 建置專案。

     Visual Studio 建立包含您範本的壓縮檔案。 它不會部署，而且在實驗實例中無法使用。

## <a name="deployment"></a>部署

### <a name="to-deploy-the-project-or-item-template"></a>若要部署專案或專案範本

1. 建立 VSIX 專案。 如需詳細資訊，請參閱 [VSIX 專案範本](../extensibility/vsix-project-template.md)。

2. 將 VSIX 專案設定為啟始專案。 在 [ **方案總管** 中，選取 [VSIX 專案] 節點、按一下滑鼠右鍵，然後選取 [ **設定為啟始專案**]。

3. 將專案範本專案設定為 VSIX 專案的資產。 開啟 *extension.vsixmanifest* 檔案。 移至 [ **資產** ] 索引標籤，然後選取 [ **新增**]。

    1. 將 **Type** 欄位設定為 **VisualStudio. ProjectTemplate** 或 **VisualStudio。**

    2. 針對 [來源]，選取 [ **目前方案中的專案** ] 選項，然後選取包含您範本的專案。

4. 建立方案，然後按下 **F5**。 實驗實例隨即出現。

5. 針對專案範本專案，您應該會在 [**新增專案**] 對話方塊中看到您的專案範本 **， (**  >  [檔案 **新增**  > ) **專案**] 對話方塊的 [Visual c #] 或 [Visual Basic] 節點中。 針對專案範本專案，您應該會看到專案範本列在 [ **加入新專案** ] 對話方塊中。 若要查看 [**加入新專案**] 對話方塊，請從 [**方案總管** 中選取專案節點，然後選取 [**加入**  >  **新專案**]) 。

## <a name="see-also"></a>另請參閱

- [Visual Studio 範本參考](../ide/creating-project-and-item-templates.md)
- [Visual Studio 範本中的 NuGet 套件](/nuget/visual-studio-extensibility/visual-studio-templates)
