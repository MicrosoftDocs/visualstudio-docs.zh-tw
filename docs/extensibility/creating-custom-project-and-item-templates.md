---
title: 建立自訂專案與項目範本 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fc866c9a0cd5f3aaaa06e5bc59ea2427cc86268a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31104361"
---
# <a name="creating-custom-project-and-item-templates"></a>建立自訂專案與項目範本

Visual Studio SDK 包括專案範本建立自訂專案範本和自訂項目範本。 這些範本包含一些常見的參數替代項目，並建置為 zip 檔案。 自動部署，並不會出現在實驗執行個體。 您必須將產生的 zip 檔案複製到使用者範本目錄中。
  
範本建立範本可讓您範本包含在較大的延伸模組。 這可讓您實作上的原始程式檔的版本控制和建置成單一 VSIX 套件專案範本群組中。  
  
您也可以設定範本來安裝 NuGet 封裝。 如需詳細資訊，請參閱[NuGet 封裝在 Visual Studio 範本](/nuget/visual-studio-extensibility/visual-studio-templates)。

基本範本建立的情況下，您應該使用**匯出範本**精靈，將輸出至壓縮的檔案。 如需有關建立基本範本的詳細資訊，請參閱[建立專案和項目範本](../ide/creating-project-and-item-templates.md)。  

> [!NOTE]
> 從 Visual Studio 2017，掃描自訂專案與項目範本將不會再執行。 相反地，延伸模組必須提供範本資訊清單檔案來描述這些範本的安裝位置。 您可以使用 Visual Studio 2017 更新您的 VSIX 擴充功能。 如果您部署使用 MSI 延伸模組，您必須手動產生範本資訊清單檔案。 如需詳細資訊，請參閱[升級自訂專案與 Visual Studio 2017 的項目範本](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)。 範本資訊清單結構描述會記載在[Visual Studio 範本資訊清單結構描述參考](../extensibility/visual-studio-template-manifest-schema-reference.md)。

## <a name="creating-a-project-template"></a>建立專案範本  
  
1.  建立專案範本專案。 您可以找到中的專案範本**新專案**對話方塊中的，在 Visual Basic 或 Visual C#**擴充性**資料夾。  
  
     範本會產生類別檔案、 圖示、.vstemplate 檔案、 名為 ProjectTemplate.vbproj 或 ProjectTemplate.csproj，可以讓您編輯專案檔和其他專案類型，這類 resources.resx 檔案中，AssemblyInfo 通常會產生某些檔案檔案與.settings 檔案。 每個程式碼檔包含一般參數的替代適當的位置。  
  
2.  新增和移除專案對專案所需的項目。 請勿移除可編輯專案檔、 AssemblyInfo 檔案或.vstemplate 檔案。  
  
3.  更新以反映任何新增及刪除.vstemplate 檔案。 [專案](../extensibility/project-element-visual-studio-templates.md)元素必須包含[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)要併入範本中每個檔案的項目。  
  
4.  修改您的程式碼檔案和其他使用者對象的內容，並新增適當的參數替代項目。  
  
5.  修改視需要產生的內容。  
  
6.  建置專案。  
  
     Visual Studio 會建立包含您的範本的.zip 檔案。 未部署，而且不用於實驗執行個體。  
  
## <a name="creating-an-item-template"></a>建立項目範本  
  
1.  建立項目範本專案。  
  
     範本會產生類別檔案、 圖示、.vstemplate 檔案和 AssemblyInfo 檔案。 將類別檔案包含某些常見的參數替代。  
  
2.  新增和移除專案對專案所需的項目。  
  
3.  更新以反映任何新增及刪除.vstemplate 檔案。 [專案](../extensibility/project-element-visual-studio-templates.md)元素必須包含[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)要併入範本中每個檔案的項目。  
  
4.  修改您的程式碼檔案和其他使用者對象的內容，並新增適當的參數替代項目。  
  
5.  修改產生所需的內容。  
  
6.  建置專案。  
  
     Visual Studio 會建立壓縮的檔案，其中包含您的範本。 未部署，而且不用於實驗執行個體。  
  
## <a name="deployment"></a>部署  
  
#### <a name="to-deploy-the-project-or-item-template"></a>若要部署專案或項目範本  
  
1.  建立 VSIX 專案。 如需詳細資訊，請參閱[VSIX 專案範本](../extensibility/vsix-project-template.md)。  
  
2.  將 VSIX 專案設定為啟始專案。 在**方案總管] 中**，選取 [VSIX 專案節點、 按一下滑鼠右鍵，然後選取**設定為啟始專案**。  
  
3.  設定專案範本為 VSIX 專案的資產。 開啟的.vsixmanifest 檔案。 移至**資產**索引標籤上，按一下 **新增**。  
  
    1.  設定**類型**欄位設為**Microsoft.VisualStudio.ProjectTemplate**或**Microsoft.VisualStudio.ItemTemplate**。  
  
    2.  針對來源，請選取**目前方案中的專案**選項，然後再選取包含您的範本的專案。  
  
4.  建置方案，然後按 F5。 實驗執行個體隨即出現。  
  
5.  專案範本專案中，您應該會看到您的專案範本中所列**新專案**對話方塊 (**檔案 > 新增 > 專案**) 中的 Visual C# 或 Visual Basic 節點。 為項目範本專案中，您應該會看到您加入新項目對話方塊中列出的項目範本 (在**方案總管 中**，選取專案節點，然後按一下**新增 / 新項目**)。  
  
## <a name="see-also"></a>另請參閱

[Visual Studio 範本參考](../ide/visual-studio-template-reference.md)  
[在 Visual Studio 範本中的 NuGet 封裝](/nuget/visual-studio-extensibility/visual-studio-templates)