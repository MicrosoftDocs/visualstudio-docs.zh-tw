---
title: "如何： 將實體加入至模型 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EntityTool
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 2ef3885f2a290fd1d4193daf9436a08ae5588a0d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-an-entity-to-a-model"></a>如何：將實體加入至模型
  若要建立實體時，將 Visual Studio 的實體控制項**工具箱**商務資料連線 (BDC) 設計工具上。  
  
### <a name="to-add-an-entity-to-the-model"></a>若要將實體加入至模型  
  
1.  建立 BDC 專案，或開啟現有的 BDC 專案。 如需詳細資訊，請參閱[建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
2.  在**工具箱**，從**BusinessDataCatalog**群組中，加入**實體**控制項拖曳至設計工具。  
  
     新的實體會出現在設計工具。 Visual Studio 會加入`<Entity>`BDC 模型檔案，在您的專案中的 xml 項目。 實體項目之屬性的相關資訊，請參閱[實體](http://go.microsoft.com/fwlink/?LinkId=169296)。  
  
3.  在設計工具中，開啟實體的捷徑功能表，選擇 **新增**，然後選擇 **識別碼**。  
  
     新的識別碼會出現在實體上。  
  
    > [!NOTE]  
    >  您可以變更實體和中的識別項名稱**屬性**視窗。  
  
4.  類別中定義實體的欄位。 您可以將新類別加入至專案，或使用現有的類別使用物件關聯式設計工具 （O/R 設計工具） 等其他工具所建立。 下列範例會示範名為連絡人的實體類別。  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]  
  
## <a name="see-also"></a>請參閱  
 [如何： 加入建立者方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何： 加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [如何： 加入 Updater 方法](../sharepoint/how-to-add-an-updater-method.md)   
 [如何： 加入搜尋方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何：新增特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)  
  
  