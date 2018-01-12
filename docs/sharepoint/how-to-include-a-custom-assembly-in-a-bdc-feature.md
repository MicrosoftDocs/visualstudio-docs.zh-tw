---
title: "如何： 在 BDC 功能中包含自訂組件 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 32554a0456c34a3c8b1d96c471fd7ae8e9221943
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>如何：在 BDC 功能中包含自訂組件
  您的專案可以參考組件從相同方案中其他專案。 不過，您必須加入這些組件的功能檔案的專案使用**指派參考組件 Lobsystem 加入** 對話方塊。  
  
### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>商務資料連線 (BDC) 功能中包含自訂組件  
  
1.  在**方案總管 中**，選擇包含 BDC 模型的資料夾。  
  
2.  在 [ **檢視** ] 功能表中，按一下 [ **屬性視窗**]。  
  
3.  在**屬性**視窗中，選擇**組件**屬性，然後按一下 省略符號按鈕 (![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile設計工具橢圓形"))。  
  
     **指派參考組件 Lobsystem 加入** 對話方塊隨即出現。  
  
4.  在**選取的組件**清單中，選擇自訂組件。  
  
    > [!NOTE]  
    >  組件才會出現在**指派參考組件 Lobsystem 加入**對話方塊中，如果您已經加入至專案，其中包含組件的參考。 如需詳細資訊，請參閱[如何： 加入或移除參考使用加入參考對話方塊](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)。  
  
5.  在**參考屬性**群組中，開啟所顯示清單**LobSystem 範圍**屬性，選擇 LOB 系統的方法，使用自訂組件，然後選擇  **確定**  按鈕。  
  
    > [!NOTE]  
    >  偵錯自訂組件中的程式碼，您必須將組件加入至方案套件。 如需詳細資訊，請參閱[如何： 加入和移除其他組件](../sharepoint/how-to-add-and-remove-additional-assemblies.md)。  
  
## <a name="see-also"></a>請參閱  
 [如何： 使用資源檔來指定當地語系化的名稱、 屬性和權限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [如何： 將現有的 BDC 模型檔案加入至 SharePoint 專案](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [如何： 建立 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)   
 [將商業資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  