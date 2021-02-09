---
title: 如何：定義參數的類型描述元 |Microsoft Docs
description: 瞭解如何在您的商務資料連線 (BDC) 模型中，為方法定義參數的類型描述元。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor
- BDC [SharePoint development in Visual Studio], parameter types
- BDC [SharePoint development in Visual Studio], type descriptor
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9dac5aa82b03887a11ba9ed3c76fe03fd85174cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913713"
---
# <a name="how-to-define-the-type-descriptor-of-a-parameter"></a>如何：定義參數的類型描述元
  類型描述元包含描述參數資料類型的屬性。 類型描述元可以定義欄位、實體或實體集合。 如需詳細資訊，請參閱 [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\))。

### <a name="to-define-the-type-descriptor-of-a-parameter"></a>定義參數的類型描述元

1. 在 [ **BDC 方法詳細資料** ] 視窗中，選擇參數的類型描述元。

2. 在功能表列上，選擇 [ **視圖**]、[ **屬性視窗]**。

3. 在 [ **屬性** ] 視窗中，設定類型描述項的屬性。

     下列程序描述如何將類型描述元定義為欄位、實體或實體集合。

### <a name="to-define-a-field"></a>定義欄位

1. 在 [ **屬性** ] 視窗中，將類型描述元的 [ **名稱** ] 屬性設定為代表實體 (類型中的功能變數名稱（例如： **FirstName**) ）。

2. 在 [ **TypeName** ] 屬性旁邊的清單中，選擇適當的資料類型 (例如， **Int32**) 。

     如需其他選擇性參數的詳細資訊，請參閱 [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\))。

### <a name="to-define-an-entity"></a>定義實體

1. 在 [ **屬性** ] 視窗中，將 [ **名稱** ] 屬性設定為描述實體 (的名稱，例如： **Contact**) 。

2. 將 [ **TypeName** ] 屬性設定為代表實體之類型的完整名稱。 此類型可以是您專案中的類別、您在方案中所參考組件中定義的類型或 BDC 物件模型中定義的類型。

    - 針對專案中的類別，選擇 [ **TypeName** ] 屬性旁邊的向下箭號，在出現的對話方塊中選擇 [ **目前的專案** ] 索引標籤，然後選擇您專案中的類別。

         完整名稱包含類別的命名空間和名稱，後面跟有 LOB 系統的名稱。 下列範例會將 [ **TypeName** ] 屬性的值設定為您專案中的類別。

         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`

    - 若為位於您方案之組件中的類型，完整名稱包含類型的名稱、組件的名稱、版本號碼、文化特性和公開金鑰語彙基元。

         下列範例會將 [ **TypeName** ] 屬性的值設定為您在方案中參考之元件中所定義的類型。

         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`

    - 若為 BDC 物件模型中定義的類型，完整名稱包含該類型的命名空間和名稱。

         下列範例會將 [ **TypeName** ] 屬性的值設定為 BDC 物件模型中的型別。

         `Microsoft.BusinessData.Runtime.DynamicType`

3. 在 [ **BDC 方法詳細資料** ] 視窗中，開啟針對類型描述元顯示的清單，然後選擇 [ **編輯**]。

     [ **BDC Explorer** ] 視窗隨即開啟。

4. 在 [ **BDC Explorer**] 中，開啟類型描述項的快捷方式功能表，然後選擇 [ **加入類型描述** 元]。

     新的類型描述元便會做為子類型描述元加入至實體類型描述元。 將此類型描述元設定為欄位。

5. 重複步驟 4，為該實體的每個欄位加入子類型描述元。

### <a name="to-define-a-collection-of-entities"></a>定義實體集合

1. 在 [ **BDC 方法詳細資料** ] 視窗中，選擇您想要之參數的類型描述元。

2. 在功能表列上，選擇 [ **視圖**]、[ **屬性視窗]**。

3. 在 [ **屬性** ] 視窗中，將 [ **名稱** ] 屬性設定為描述實體的名稱 (例如： **Contacts**) 。

4. 將 [ **IsCollection** ] 屬性設定為 [ **True**]。 這表示此類型描述元是實體的集合。

5. 將 [ **TypeName** ] 屬性設定為字串，其中包含介面的參考 <xref:System.Collections.Generic.IEnumerable%601> ，以及代表實體之類型的完整名稱。 此類型可以是您專案中的類別、您在方案中所參考組件中定義的類型或 BDC 物件模型中定義的類型。

   - 針對專案中的類別，選擇 [ **TypeName** ] 屬性旁邊的向下箭號，在出現的對話方塊中選擇 [ **目前的專案** ] 索引標籤，然後選擇您專案中的類別。

      完整名稱包含類別的命名空間和名稱，後面跟有 LOB 系統的名稱。

      下列範例會將 [ **TypeName** ] 屬性的值設定為專案中的類別集合。

      `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace. BdcModel1. Contact，BdcModel1] '

   - 若為位於您方案之組件中的類型，完整名稱包含類型的名稱、組件的名稱、版本號碼、文化特性和公開金鑰語彙基元。

      下列範例會將 [ **TypeName** ] 屬性的值設定為您在方案中參考之元件中的類型集合。

      `System.Collections.Generic.IEnumerable`1 [MyNamespace. Contact，myAssemblyName，Version = 4.0.0.0，Culture = 中性，PublicKeyToken = b77a5c561934e089] '

   - 若為 BDC 物件模型中定義的類型，完整名稱僅包含該類型的命名空間和名稱。

      下列範例會將 [ **TypeName** ] 屬性的值設定為 BDC 物件模型中定義的類型集合。

      `System.Collections.Generic.IEnumerable`1 [Microsoft. BusinessData. DynamicType] '

6. 在 [ **BDC 方法詳細資料** ] 視窗中，開啟針對類型描述元顯示的清單，然後選擇 [ **編輯**]。

    [ **BDC Explorer** ] 視窗隨即開啟。

7. 在 [ **BDC Explorer**] 中，開啟類型描述項的快捷方式功能表，然後選擇 [ **加入類型描述** 元]。

    新的類型描述元便會做為子類型描述元加入集合類型描述元。 將此類型描述元設定為實體。

## <a name="see-also"></a>另請參閱
- [BDC 模型設計工具總覽](../sharepoint/bdc-model-design-tools-overview.md)
- [如何：將實體加入至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [如何：將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [如何：定義方法實例](../sharepoint/how-to-define-a-method-instance.md)
- [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)
