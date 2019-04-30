---
title: 建立自訂專案與項目範本 |Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01af6001bd116fd2b523668eddbdc68d2dd5beab
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926428"
---
# <a name="create-custom-project-and-item-templates"></a>建立自訂專案和項目範本

Visual Studio SDK 包含專案範本，可建立自訂專案範本和自訂項目範本。 這些範本包含一些常見的參數替代項目，並建置的 zip 檔案。 它們不會自動部署，並不提供在實驗執行個體。 您必須將產生的 zip 檔案複製到使用者範本目錄中。

範本建立範本可讓您在較大的擴充功能中包含範本。 這可讓您實作在原始程式檔的版本控制和建置成單一 VSIX 套件的一組範本專案。

您也可以設定範本，以安裝 NuGet 套件。 如需詳細資訊，請參閱 < [Visual Studio 範本中的 NuGet 套件](/nuget/visual-studio-extensibility/visual-studio-templates)。

基本的範本建立的情況下，您應該使用**匯出範本**精靈，將輸出到壓縮的檔案。 如需有關建立基本範本的詳細資訊，請參閱 <<c0> [ 建立專案和項目範本](../ide/creating-project-and-item-templates.md)。

> [!NOTE]
> 啟動 Visual Studio 2017 中，自訂專案與項目範本的掃描將不會再執行。 相反地，延伸模組必須提供範本資訊清單檔案來描述這些範本的安裝位置。 您可以使用 Visual Studio 2017 更新您的 VSIX 擴充功能。 如果您部署使用 MSI 延伸模組，您必須以手動方式產生範本資訊清單檔。 如需詳細資訊，請參閱 < [Visual Studio 2017 的升級自訂專案與項目範本](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)。 範本資訊清單結構描述記載於[Visual Studio 範本資訊清單結構描述參考](../extensibility/visual-studio-template-manifest-schema-reference.md)。

## <a name="create-a-project-template"></a>建立專案範本

1. 建立專案範本專案。 您可以找到中的專案範本**新的專案**對話方塊中的，搜尋 「 專案範本 」，然後選取C#或 Visual Basic 版本。

     範本會產生類別檔案圖示 *.vstemplate*檔案，名為可編輯專案檔*ProjectTemplate.vbproj*或*ProjectTemplate.csproj*，而有些其他專案類型，通常會產生檔案這類*resources.resx*檔案， *AssemblyInfo*檔案，並 *.settings*檔案。 每個程式碼檔案包含通用的參數替代項目，在適當的地方。

2. 新增和移除專案中視需要為您的專案中的項目。 請勿移除可編輯專案檔中， *AssemblyInfo*檔案，或有 *.vstemplate*檔案。

3. 更新 *.vstemplate*檔案以反映任何新增及刪除。 [專案](../extensibility/project-element-visual-studio-templates.md)項目必須包含[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)每個檔案要包含在範本中的項目。

4. 修改您的程式碼檔案和其他使用者端的內容，並加入適當的參數替代項目。

5. 修改視需要產生的內容。

6. 建置專案。

     Visual Studio 會建立 *.zip*檔案，其中包含您的範本。 中未部署，但它不適用於實驗的執行個體。

## <a name="create-an-item-template"></a>建立項目範本

1. 建立項目範本專案。

     範本會產生類別檔案圖示 *.vstemplate*檔案，以及*AssemblyInfo*檔案。 類別檔案包含一些常見的參數替代項目。

2. 新增和移除專案中視需要為您的專案中的項目。

3. 更新 *.vstemplate*檔案以反映任何新增及刪除。 [專案](../extensibility/project-element-visual-studio-templates.md)項目必須包含[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)每個檔案要包含在範本中的項目。

4. 修改您的程式碼檔案和其他使用者端的內容，並加入適當的參數替代項目。

5. 修改產生所需的內容。

6. 建置專案。

     Visual Studio 會建立壓縮的檔案，其中包含您的範本。 中未部署，但它不適用於實驗的執行個體。

## <a name="deployment"></a>部署

### <a name="to-deploy-the-project-or-item-template"></a>若要部署專案或項目範本

1. 建立 VSIX 專案。 如需詳細資訊，請參閱 < [VSIX 專案範本](../extensibility/vsix-project-template.md)。

2. 將 VSIX 專案設定為啟始專案。 在 **方案總管**，選取 VSIX 專案節點、 按一下滑鼠右鍵，然後選取**設定為啟始專案**。

3. 設定專案範本為 VSIX 專案的資產。 開啟 *.vsixmanifest*檔案。 移至**資產**索引標籤，然後按一下**新增**。

    1. 設定**型別**欄位設為**Microsoft.VisualStudio.ProjectTemplate**或是**Microsoft.VisualStudio.ItemTemplate**。

    2. 針對來源，選取**目前的方案中的專案**選項，然後再選取包含您範本的專案。

4. 建置方案，然後按**F5**。 實驗執行個體隨即出現。

5. 專案範本專案中，您應該會看到您的專案範本中所列**新的專案** 對話方塊 (**檔案** > **新增** >  **專案**) 中的 Visual C# 或 Visual Basic 節點。 項目範本專案，您應該會看到您中所列的項目範本**加入新項目**對話方塊。 若要檢視**加入新項目** 對話方塊中，從**方案總管**，選取專案節點，然後按一下**新增** > **新項目**).

## <a name="see-also"></a>另請參閱

- [Visual Studio 範本參考](../ide/creating-project-and-item-templates.md)
- [Visual Studio 範本中的 NuGet 套件](/nuget/visual-studio-extensibility/visual-studio-templates)
