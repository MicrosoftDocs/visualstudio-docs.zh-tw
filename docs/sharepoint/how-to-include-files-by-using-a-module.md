---
title: 如何：使用模組包含檔案 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1ada86be30e207e36c7e0d84d3fd5dd877605e4d
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016301"
---
# <a name="how-to-include-files-by-using-a-module"></a>如何：使用模組來包含檔案
  *模組*（不會與模組混淆 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ）是容器，可讓您將 ASPX 主版頁面、文字檔或影像等檔案部署至 SharePoint。

 您可以選擇將檔案部署至文件庫，或做為檔庫外部的一般檔案（例如 default.aspx）。 若要將檔案加入至文件庫，請將指定 `Type="GhostableInLibrary"` 為**file**元素中的屬性。 這項設定會指示 SharePoint 在新增至程式庫時，建立要與您的檔案搭配使用的清單專案。 若要在文件庫外部部署檔案，請指定 `Type="Ghostable"` 或只省略**Type**屬性。

## <a name="add-a-module-to-a-sharepoint-solution"></a>將模組新增至 SharePoint 方案

#### <a name="to-add-a-module"></a>若要加入模組

1. 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中開啟或建立 SharePoint 專案。

     如需詳細資訊，請參閱[SharePoint 專案和專案專案範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。

2. 在**方案總管**中，選擇專案節點，然後在功能表列上選擇 [**專案**] [新增] [  >  **新專案**]。

     [新增項目]**** 對話方塊隨即開啟。

3. 在 SharePoint 範本清單中，選擇 [**模組**] 範本，然後選擇 [**新增**] 按鈕。

     這個步驟會在名為 Module1 的專案中建立一個節點。

4. 在 [Module1] 底下，刪除*Sample.txt*檔案。

     基於範例目的，Sample.txt 包含在所有新的模組中，因此不需要。 （請注意，刪除檔案也會從模組的*Elements.xml*檔案中移除它的專案）。

5. 如果您想要將檔案部署到 SharePoint 中的特定資料夾結構，請 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 選擇 [module1] 節點，然後在功能表列上選擇 [**專案**]、[**新增資料夾**]，在 [module1] 底下建立這些資料夾。

6. 選擇您要在其中新增檔案的資料夾，然後在功能表列上選擇 [**專案**]、[**加入現有專案**]。

7. 選擇要部署到 SharePoint 的一或多個檔案，然後選擇 [**新增**] 按鈕。

     當您將檔案新增至專案時，它的專案會自動加入至模組的 Elements.xml 檔案。 部署專案時，檔案會複製到 SharePoint server （相對於專案的根目錄），這是由**File**元素的**Url**屬性所指定，例如 `Url="Module1/New Folder/SomeFile.doc` 。 如果您想要變更檔案的部署位置，請將它移至**方案總管**中的另一個資料夾，或變更其**Url**設定。

8. 對於您想要出現在文件庫中的任何檔案，請將 `Type="GhostableInLibrary"` 屬性附加至*Elements.xml*中的專案。 例如，

    ```xml
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />
    ```

9. 部署專案。

     檔案會複製到 SharePoint 中的指定位置。

## <a name="see-also"></a>另請參閱
- [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
