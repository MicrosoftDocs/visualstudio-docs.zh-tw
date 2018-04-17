---
title: 如何： 將資源檔 |Microsoft 文件
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
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 132a5b5933b1bc96244238570091e522f8af91d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-resource-file"></a>如何：新增資源檔
  將資源檔加入的命令所在的方案節點，在 [方案總管] 功能節點的捷徑功能表。 如需詳細資訊，請參閱[當地語系化 SharePoint 方案](../sharepoint/localizing-sharepoint-solutions.md)。  
  
### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>若要將全域資源檔案加入至 SharePoint 方案  
  
1.  在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，開啟 SharePoint 方案。  
  
2.  在**方案總管] 中**，選擇 SharePoint 專案節點，然後在功能表列上選擇 [**專案**，**加入新項目**。  
  
3.  在**加入新項目**對話方塊方塊中，選擇**全域資源檔案**範本，然後選擇 [**新增**] 按鈕。  
  
    > [!NOTE]  
    >  只有在選取 SharePoint 專案項目時，會出現 全域資源檔案的專案項目範本。  
  
4.  在**加入資源**對話方塊方塊中，選擇資源檔案，例如英文 （美國） 文化特性。  
  
     這個步驟會加入至您的方案中使用的格式，資源的全域資源檔案 * x***。***文化特性 ***。**例如，Resource1.en US.resx resx。  
  
5.  當**資源編輯器**中開啟[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，將資源加入至資源檔。  
  
### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>若要將功能資源檔加入至 SharePoint 功能  
  
1.  如果尚未開啟，在 SharePoint 方案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，開啟方案。  
  
2.  在**方案總管 中**，開啟快顯功能表下的功能名稱**功能** 節點，然後選擇 **加入功能資源**。  
  
     這個步驟會加入資源檔格式，功能 * ResourceFileName***。***文化特性 ***。**例如，Feature1.en US.resx resx。  
  
3.  當**資源編輯器**中開啟[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，將資源加入至資源檔。  
  
## <a name="see-also"></a>另請參閱  
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  