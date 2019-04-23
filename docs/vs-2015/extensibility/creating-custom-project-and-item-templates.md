---
title: 建立自訂專案和項目範本
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c6875e13baa83d349020f50a3fe448a87ec5fd30
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60114817"
---
# <a name="creating-custom-project-and-item-templates"></a>建立自訂專案和項目範本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK 包含專案範本，可建立自訂專案範本和自訂項目範本。 這些範本包含一些常見的參數替代項目，並建置的 zip 檔案。 它們不會自動部署，並不提供在實驗執行個體。 複製的 zip 檔案的位置

範本建立範本可讓您在較大的擴充功能中包含範本。 包括 擴充功能中的 範本，可讓您實作在原始程式檔的版本控制和建置成單一 VSIX 套件的一組範本專案。

基本的範本建立的情況下，您應該使用**匯出範本**精靈，將輸出到壓縮的檔案。 如需有關建立基本範本的詳細資訊，請參閱 <<c0> [ 建立專案和項目範本](../ide/creating-project-and-item-templates.md)。

從 Visual Studio 2017 中，自訂專案和項目範本已不再執行掃描。 相反地，延伸模組必須提供範本資訊清單檔案來描述這些範本的安裝位置。 若要更新您的 VSIX 擴充功能，您可以使用 Preview 2 安裝。 如果您部署使用 MSI 延伸模組，您必須以手動方式產生範本資訊清單檔。 如需詳細資訊，請參閱 <<c0> [ 升級自訂專案與項目範本，適用於 Visual Studio 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015)。 範本資訊清單結構描述記載於[Visual Studio 範本資訊清單結構描述參考](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference)。

## <a name="create-a-project-template"></a>建立專案範本

1. 建立專案範本專案。 您可以找到中的專案範本**新的專案**對話方塊中的，在 Visual Basic 或 Visual C#**擴充性**資料夾。

     範本會產生類別檔案、 圖示、.vstemplate 檔案，名為 ProjectTemplate.vbproj 或 ProjectTemplate.csproj，可以讓您編輯專案檔和一些通常由其他專案類型，這類 resources.resx 檔案中，AssemblyInfo 所產生的檔案檔案和.settings 檔案。 每個程式碼檔案包含通用的參數替代項目，在適當的地方。

2. 新增和移除專案中視需要為您的專案中的項目。 請勿移除可編輯專案檔、 AssemblyInfo 檔案或.vstemplate 檔案。

3. 更新以反映任何新增及刪除.vstemplate 檔案。 [專案](../extensibility/project-element-visual-studio-templates.md)項目必須包含[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)每個檔案要包含在範本中的項目。

4. 修改您的程式碼檔案和其他使用者端的內容，並加入適當的參數替代項目。

5. 修改視需要產生的內容。

6. 建置專案。

     Visual Studio 會建立包含您的範本.zip 檔案。 中未部署，但它不適用於實驗的執行個體。

## <a name="create-an-item-template"></a>建立項目範本

1. 建立項目範本專案。

     範本會產生類別檔案、 圖示、.vstemplate 檔案和 AssemblyInfo 檔案。 類別檔案包含一些常見的參數替代項目。

2. 新增和移除專案中視需要為您的專案中的項目。

3. 更新以反映任何新增及刪除.vstemplate 檔案。 [專案](../extensibility/project-element-visual-studio-templates.md)項目必須包含[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)每個檔案要包含在範本中的項目。

4. 修改您的程式碼檔案和其他使用者端的內容，並加入適當的參數替代項目。

5. 修改產生所需的內容。

6. 建置專案。

     Visual Studio 會建立壓縮的檔案，其中包含您的範本。 中未部署，但它不適用於實驗的執行個體。

## <a name="deploy-the-project-or-item-template"></a>部署專案或項目範本

1. 建立 VSIX 專案。 如需詳細資訊，請參閱 < [VSIX 專案範本](../extensibility/vsix-project-template.md)。

2. 將 VSIX 專案設定為啟始專案。 在 **方案總管**，選取 VSIX 專案節點、 按一下滑鼠右鍵，然後選取**設定為啟始專案**。

3. 設定專案範本為 VSIX 專案的資產。 開啟的.vsixmanifest 檔案。 移至**資產**索引標籤，然後按一下**新增**。

    1. 設定**型別**欄位設為**Microsoft.VisualStudio.ProjectTemplate**或是**Microsoft.VisualStudio.ItemTemplate**。

    2. 針對來源，選取**目前的方案中的專案**選項，然後再選取包含您範本的專案。

4. 建置方案，然後按 F5。 實驗執行個體隨即出現。

5. 專案範本專案中，您應該會看到您的專案範本中所列**新的專案** 對話方塊 (**檔案 / 新增 / 專案**) 中的 Visual C# 或 Visual Basic 節點。 項目範本專案，您應該會看到您加入新項目 對話方塊中所列的項目範本 (在**方案總管**，選取專案節點，然後按一下**新增 / 新項目**)。

## <a name="see-also"></a>另請參閱

- [Visual Studio 範本參考](../ide/visual-studio-template-reference.md)