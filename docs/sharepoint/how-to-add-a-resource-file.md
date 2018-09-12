---
title: 如何： 加入資源檔 |Microsoft Docs
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
ms.openlocfilehash: 2a2a89a0c838a91559c6066bea341924e5ca627e
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43774644"
---
# <a name="how-to-add-a-resource-file"></a>如何： 加入資源檔
  方案節點，然後在 [方案總管] 中的功能節點的捷徑功能表上，是將資源檔的命令。 如需詳細資訊，請參閱 <<c0> [ 當地語系化 SharePoint 方案](../sharepoint/localizing-sharepoint-solutions.md)。  
  
### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>若要將全域資源檔新增至 SharePoint 方案  
  
1.  在  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，開啟 SharePoint 方案。  
  
2.  在 **方案總管**，選擇 SharePoint 專案節點，然後在功能表列上選擇 **專案** > **加入新項目**。  
  
3.  中**加入新項目**對話方塊方塊中，選擇**全域資源檔**範本，然後選擇**新增** 按鈕。  
  
    > [!NOTE]  
    >  只有在選取 SharePoint 專案項目時，會出現全域資源檔案的專案項目範本。  
  
4.  在 **加入資源**對話方塊方塊中，選擇資源檔案，例如英文 （美國） 文化特性。  
  
     這個步驟會全域資源檔加入至您的方案中的格式，Resource_x_**。**_文化特性_**。** resx，例如*Resource1.en US.resx*。  
  
5.  當**資源編輯器**以開啟[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，將資源新增至資源檔。  
  
### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>若要將功能資源檔新增至 SharePoint 功能  
  
1.  如果尚未在中開啟 SharePoint 方案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，開啟方案。  
  
2.  在**方案總管 中**，開啟下的功能名稱的捷徑功能表**功能**節點，然後選擇**加入功能資源**。  
  
     這個步驟會加入資源檔格式的功能_ResourceFileName_**。**_文化特性_**.resx**，例如*Feature1.en US.resx*。  
  
3.  當**資源編輯器**以開啟[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，將資源新增至資源檔。  
  
## <a name="see-also"></a>另請參閱
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)  
  
 
