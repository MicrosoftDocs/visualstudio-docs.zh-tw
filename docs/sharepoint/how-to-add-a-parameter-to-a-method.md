---
title: HOW TO：新增參數至方法 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], adding a method to a parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter
- BDC [SharePoint development in Visual Studio], adding a method to a parameter
- BDC [SharePoint development in Visual Studio], parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], method parameters
- BDC [SharePoint development in Visual Studio], method parameters
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5f7d0e0ab164bf30c341ca093908be3661452d19
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866253"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>HOW TO：新增參數至方法
  若要將資訊傳遞至方法，或從方法傳回的資訊，請使用參數。 所有的方法必須有至少一個參數。 如需如何設計來支援您想要建立的方法的型別參數的詳細資訊，請參閱[設計 Business Data Connectivity 模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
 當您新增參數至方法時，Visual Studio 會將您的專案中的模型檔案的 XML 參數項目。 參數項目之屬性的相關資訊，請參閱[參數](http://go.microsoft.com/fwlink/?LinkId=169284)。  
  
### <a name="to-add-a-parameter-to-a-method"></a>若要將參數加入至方法  
  
1.  將方法新增至實體。  
  
2.  在功能表列上選擇 **檢視** > **其他 Windows** > **BDC 方法詳細資料**。  
  
     **BDC 方法詳細資料**視窗隨即開啟。 如需詳細資訊，請參閱 < [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)。  
  
3.  在 [ **BDC 方法詳細資料**] 視窗中，展開方法的節點，然後再展開**參數**節點。  
  
4.  在 **將參數加入**清單中，選擇**建立參數**。  
  
     新的參數會出現下方**參數**節點。  
  
5.  在功能表列上選擇 [**檢視** > **屬性] 視窗**。  
  
6.  在 **屬性**視窗中，將**名稱**任何有意義的名稱屬性。 比方說，如果此方法會傳回客戶，您可能會將方法命名**GetCustomers**。  
  
7.  在 [ **BDC 方法詳細資料**] 視窗中，開啟顯示方向之參數的清單，然後選擇**中**， **InOut**， **Out**，或**傳回**。  
  
     如需哪一個方向來選擇您要建立之型別方法的詳細資訊，請參閱[設計 business data connectivity 模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
8.  修改參數的類型描述元。 如需詳細資訊，請參閱[＜How to：定義參數的型別描述元](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。  
  
## <a name="see-also"></a>另請參閱
 [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何：將實體新增至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [如何：定義參數的型別描述元](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [如何：定義方法執行個體](../sharepoint/how-to-define-a-method-instance.md)   
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)  
