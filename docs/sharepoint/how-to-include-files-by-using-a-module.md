---
title: 如何： 使用模組中包含的檔案 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: daea134298e84e7ddddf419da2124924fe9ef121
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
---
# <a name="how-to-include-files-by-using-a-module"></a>如何：使用模組來包含檔案
  *模組*(不到與混淆[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]模組) 是容器，可讓您將部署到 SharePoint 的檔案，例如 ASPX 主版頁面、 文字檔或影像。  
  
 您可以選擇將檔案部署到文件庫或一般檔案 (例如 default.aspx) 的文件庫之外。 若要將檔案加入至文件庫中，指定`Type="GhostableInLibrary"`做為屬性**檔案**項目。 此設定會指示建立清單項目加入至程式庫時，與您的檔案移至 SharePoint。 若要部署文件庫之外的檔案，也可以指定`Type="Ghostable"`或只省略**類型**屬性。  
  
## <a name="adding-a-module-to-a-sharepoint-solution"></a>將模組加入至 SharePoint 方案  
  
#### <a name="to-add-a-module"></a>若要加入的模組  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中開啟或建立 SharePoint 專案。  
  
     如需詳細資訊，請參閱[SharePoint 專案與專案項目範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。  
  
2.  在**方案總管] 中**，選擇專案節點，然後在功能表列上選擇 [**專案**，**加入新項目**。  
  
     [新增項目] 對話方塊隨即開啟。  
  
3.  在 SharePoint 範本清單中選擇**模組**範本，然後選擇 [**新增**] 按鈕。  
  
     這個步驟會在名為 Module1 的專案中建立一個節點。  
  
4.  在 Module1 底下，刪除 Sample.txt 檔。  
  
     Sample.txt 隨附於所有新模組，例如用途並不需要。 （請注意，刪除該檔案也會移除其項目從模組的 Elements.xml 檔案）。  
  
5.  若要讓您將部署到 SharePoint 中的特定資料夾結構的檔案，建立在 module1 底下，在這些資料夾[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]選擇 Module1 節點，然後在功能表列選擇**專案**，**新增資料夾**。  
  
6.  選擇您要加入檔案，，然後在功能表列上選擇的資料夾**專案**，**加入現有項目**。  
  
7.  選擇您想要部署至 SharePoint，然後選擇一或多個檔案**新增** 按鈕。  
  
     當您將檔案加入專案時，它的項目會自動加入至模組的 Elements.xml 檔案。 部署專案時，檔案會複製到 SharePoint 伺服器上，相對於專案的根目錄中，指定**檔案**項目的**Url**屬性，例如`Url="Module1/New Folder/SomeFile.doc`。 如果您想要變更檔案的部署位置，請將它移至另一個資料夾中**方案總管 中**或變更其**Url**設定。  
  
8.  針對您想要出現在文件庫中的任何檔案，請附加`Type="GhostableInLibrary"`Elements.xml 中其項目屬性。 例如，套用至物件的  
  
    ```xml  
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />  
    ```  
  
9. 部署專案。  
  
     將檔案複製到 SharePoint 中的指定位置。  
  
## <a name="see-also"></a>另請參閱  
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  