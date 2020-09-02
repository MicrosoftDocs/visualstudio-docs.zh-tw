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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197393"
---
# <a name="creating-custom-project-and-item-templates"></a>建立自訂專案和項目範本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK 包含專案範本，可建立自訂專案範本和自訂專案範本。 這些範本包含一些常見的參數替代，並以 zip 檔案的形式建立。 它們不會自動部署，而是在實驗實例中無法使用。 將 zip 檔案複製到您的位置

範本建立範本可讓您將範本包含在較大的延伸模組中。 在擴充功能中包含範本，可讓您在原始程式檔上執行版本控制，並將一組範本專案建立成一個 VSIX 套件。

在基本範本建立案例中，您應該使用匯出至壓縮檔案的 **匯出範本** wizard。 如需建立基本範本的詳細資訊，請參閱 [建立專案和專案範本](../ide/creating-project-and-item-templates.md)。

從 Visual Studio 2017 開始，已不再執行自訂專案和專案範本的掃描。 相反地，此延伸模組必須提供描述這些範本之安裝位置的範本資訊清單檔。 您可以使用 Preview 2 安裝來更新您的 VSIX 擴充功能。 如果您使用 MSI 部署擴充功能，您必須手動產生範本資訊清單檔案。 如需詳細資訊，請參閱 [升級自訂 Visual Studio 的專案與項目範本 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015)。 範本資訊清單架構記載于 [Visual Studio 範本資訊清單架構參考](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference)中。

## <a name="create-a-project-template"></a>建立專案範本

1. 建立專案範本專案。 您可以在 [ **新增專案** ] 對話方塊的 [Visual Basic] 或 [ **Visual c #** 擴充性] 資料夾中找到專案範本。

     此範本會產生類別檔案、圖示、.vstemplate 檔案、名為 ProjectTemplate. vbproj 或 ProjectTemplate 的可編輯專案檔，以及某些通常由其他專案類型產生的檔案，例如 .resources 檔案、AssemblyInfo 檔和設定檔案。 每個程式碼檔案都包含適當的一般參數替代。

2. 視專案的需要，在專案中加入和移除專案。 請勿移除可編輯的專案檔、AssemblyInfo 檔或 .vstemplate 檔案。

3. 更新 .vstemplate 檔案，以反映任何新增和刪除動作。 [專案專案](../extensibility/project-element-visual-studio-templates.md)必須包含範本中[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)要包含之每個檔案的專案專案專案。

4. 修改您的程式碼檔案和其他使用者對應內容，並新增適當的參數替代。

5. 視需要修改產生的內容。

6. 建置專案。

     Visual Studio 建立包含您範本的 .zip 檔案。 它不會部署，而且在實驗實例中無法使用。

## <a name="create-an-item-template"></a>建立專案範本

1. 建立專案範本專案。

     此範本會產生類別檔案、圖示、.vstemplate 檔案，以及 AssemblyInfo 檔案。 類別檔案包含一些常見的參數替代。

2. 視專案的需要，在專案中加入和移除專案。

3. 更新 .vstemplate 檔案，以反映任何新增和刪除動作。 [專案專案](../extensibility/project-element-visual-studio-templates.md)必須包含範本中[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)要包含之每個檔案的專案專案專案。

4. 修改您的程式碼檔案和其他使用者對應內容，並新增適當的參數替代。

5. 視需要修改產生的內容。

6. 建置專案。

     Visual Studio 建立包含您範本的壓縮檔案。 它不會部署，而且在實驗實例中無法使用。

## <a name="deploy-the-project-or-item-template"></a>部署專案或專案範本

1. 建立 VSIX 專案。 如需詳細資訊，請參閱 [VSIX 專案範本](../extensibility/vsix-project-template.md)。

2. 將 VSIX 專案設定為啟始專案。 在 [ **方案總管**中，選取 [VSIX 專案] 節點、按一下滑鼠右鍵，然後選取 [ **設定為啟始專案**]。

3. 將專案範本專案設定為 VSIX 專案的資產。 開啟 extension.vsixmanifest 檔案。 移至 [ **資產** ] 索引標籤，然後按一下 [ **新增**]。

    1. 將**Type**欄位設定為**VisualStudio. ProjectTemplate**或**VisualStudio。**

    2. 針對 [來源]，選取 [ **目前方案中的專案** ] 選項，然後選取包含您範本的專案。

4. 建立方案，然後按下 F5。 實驗實例隨即出現。

5. 針對專案範本專案，您應該會在 [ **新增專案** ] 對話方塊中看到您的專案範本， ([檔案] **/[新增]/** [) 專案] 對話方塊中的 Visual c # 或 Visual Basic 節點。 針對專案範本專案，您應該會在 [加入新專案] 對話方塊中看到您的專案範本 (在 **方案總管**中，選取專案節點，然後按一下 [新增 **/新增專案**) 。

## <a name="see-also"></a>另請參閱

- [Visual Studio 範本參考](../ide/visual-studio-template-reference.md)