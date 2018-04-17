---
title: 如何： 定義方法執行個體 |Microsoft 文件
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
- Business Data Connectivity service [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method
- Business Data Connectivity service [SharePoint development in Visual Studio], method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 44a31af455b09db5fb359339cee8da7b3ca0c77e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-define-a-method-instance"></a>如何：定義方法執行個體
  在模型中，您必須定義至少一個的方法執行個體的每個方法。  
  
 使用新增方法執行個體**BDC 方法詳細資料**視窗。 當您新增方法執行個體時，Visual Studio 會加入`<MethodInstance>`至您的專案中的模型檔案的 XML 項目。 如需有關的屬性`<MethodInstance>`項目，請參閱[MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282)。  
  
### <a name="to-define-a-method-instance"></a>若要定義的方法執行個體  
  
1.  在**BDC 方法詳細資料**視窗中，展開節點的方法，然後再展開**執行個體**節點。  
  
2.  在**新增方法執行個體**清單中，選擇**建立 Finder 執行個體**。  
  
     新的方法執行個體隨即出現在下方**執行個體**節點。  
  
3.  在功能表列上選擇 [**檢視**，選擇**屬性] 視窗**。  
  
4.  在**屬性**視窗中，將方法執行個體的屬性。 如需有關每一個屬性的詳細資訊，請參閱[MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282)。  
  
## <a name="see-also"></a>另請參閱  
 [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何： 將實體加入至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [如何： 將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何： 定義參數的類型描述元](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  