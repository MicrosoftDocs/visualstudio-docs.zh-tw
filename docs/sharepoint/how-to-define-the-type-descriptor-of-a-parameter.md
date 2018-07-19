---
title: 如何： 定義參數的型別描述元 |Microsoft Docs
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
- Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor
- BDC [SharePoint development in Visual Studio], parameter types
- BDC [SharePoint development in Visual Studio], type descriptor
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d1709ea21fa785a573dae03ad8c89814c9952b50
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118614"
---
# <a name="how-to-define-the-type-descriptor-of-a-parameter"></a>如何： 定義參數的型別描述元
  類型描述元包含描述參數資料類型的屬性。 類型描述元可以定義欄位、實體或實體集合。 如需詳細資訊，請參閱 < [TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx)。  
  
### <a name="to-define-the-type-descriptor-of-a-parameter"></a>定義參數的類型描述元  
  
1.  在 [ **BDC 方法詳細資料**] 視窗中，選擇該參數的類型描述元。  
  
2.  在功能表列上選擇 [**檢視**，**屬性] 視窗**。  
  
3.  在 [**屬性**] 視窗中，設定屬性的型別描述項。  
  
     下列程序描述如何將類型描述元定義為欄位、實體或實體集合。  
  
### <a name="to-define-a-field"></a>定義欄位  
  
1.  在**屬性**視窗中，將**名稱**屬性的型別描述項，表示實體的型別中的欄位名稱 (例如： **FirstName**)。  
  
2.  在清單中下一步**TypeName**屬性，選擇適當的資料類型 (例如**Int32**)。  
  
     如需其他選擇性參數資訊，請參閱[TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx)。  
  
### <a name="to-define-an-entity"></a>定義實體  
  
1.  在 **屬性**視窗中，將**名稱**屬性來描述實體的名稱 (例如：**連絡人**)。  
  
2.  設定**TypeName**代表實體類型的完整名稱的屬性。 此類型可以是您專案中的類別、您在方案中所參考組件中定義的類型或 BDC 物件模型中定義的類型。  
  
    -   針對您的專案中的類別，選擇向下箭號旁**TypeName** ] 屬性中，選擇**目前專案**在對話方塊中，隨即出現，然後選擇 [在您的專案中的 [類別] 索引標籤。  
  
         完整名稱包含類別的命名空間和名稱，後面跟有 LOB 系統的名稱。 下列範例會設定的值**TypeName**屬性，以您的專案中的類別。  
  
         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`  
  
    -   若為位於您方案之組件中的類型，完整名稱包含類型的名稱、組件的名稱、版本號碼、文化特性和公開金鑰語彙基元。  
  
         下列範例會設定的值**TypeName**您方案中參考的組件中定義的類型屬性。  
  
         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
    -   若為 BDC 物件模型中定義的類型，完整名稱包含該類型的命名空間和名稱。  
  
         下列範例會設定的值**TypeName**屬性設為 BDC 物件模型中的類型。  
  
         `Microsoft.BusinessData.Runtime.DynamicType`  
  
3.  在 [ **BDC 方法詳細資料**] 視窗中，開啟類型描述元，出現的清單，然後選擇**編輯**。  
  
     **BDC 總管**視窗隨即開啟。  
  
4.  在  **BDC 總管**，開啟型別描述項的捷徑功能表，然後選擇**加入類型描述元**。  
  
     新的類型描述元便會做為子類型描述元加入至實體類型描述元。 將此類型描述元設定為欄位。  
  
5.  重複步驟 4，為該實體的每個欄位加入子類型描述元。  
  
### <a name="to-define-a-collection-of-entities"></a>定義實體集合  
  
1.  在 [ **BDC 方法詳細資料**] 視窗中，選擇您想要的參數的類型描述元。  
  
2.  在功能表列上選擇 [**檢視**，**屬性] 視窗**。  
  
3.  在 **屬性**視窗中，將**名稱**屬性來描述實體的名稱 (例如：**連絡人**)。  
  
4.  設定**IsCollection**屬性設 **，則為 True**。 這表示此類型描述元是實體的集合。  
  
5.  設定**TypeName**屬性設為字串，其中包含參考<xref:System.Collections.Generic.IEnumerable%601>介面，並在代表實體類型的完整的名稱。 此類型可以是您專案中的類別、您在方案中所參考組件中定義的類型或 BDC 物件模型中定義的類型。  
  
    -   針對您的專案中的類別，選擇向下箭號旁**TypeName** ] 屬性中，選擇**目前專案**在對話方塊中，隨即出現，然後選擇 [在您的專案中的 [類別] 索引標籤。  
  
         完整名稱包含類別的命名空間和名稱，後面跟有 LOB 系統的名稱。  
  
         下列範例會設定的值**TypeName**專案中的類別集合的屬性。  
  
         `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace。` `BdcModel1.Contact，BdcModel1]'  
  
    -   若為位於您方案之組件中的類型，完整名稱包含類型的名稱、組件的名稱、版本號碼、文化特性和公開金鑰語彙基元。  
  
         下列範例會設定的值**TypeName**您方案中參考的組件中的型別集合的屬性。  
  
         `System.Collections.Generic.IEnumerable`1 [MyNamespace.Contact、 myAssemblyName，版本 version=4.0.0.0，Culture = neutral，publickeytoken=b77a5c561934e089]'  
  
    -   若為 BDC 物件模型中定義的類型，完整名稱僅包含該類型的命名空間和名稱。  
  
         下列範例會設定的值**TypeName** BDC 物件模型中定義的型別集合的屬性。  
  
         `System.Collections.Generic.IEnumerable`1 [Microsoft.BusinessData.Runtime.DynamicType]'  
  
6.  在 [ **BDC 方法詳細資料**] 視窗中，開啟類型描述元，出現的清單，然後選擇**編輯**。  
  
     **BDC 總管**視窗隨即開啟。  
  
7.  在  **BDC 總管**，開啟型別描述項的捷徑功能表，然後選擇**加入類型描述元**。  
  
     新的類型描述元便會做為子類型描述元加入集合類型描述元。 將此類型描述元設定為實體。  
  
## <a name="see-also"></a>另請參閱
 [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何： 將實體新增至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [如何： 將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何： 定義方法執行個體](../sharepoint/how-to-define-a-method-instance.md)   
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
