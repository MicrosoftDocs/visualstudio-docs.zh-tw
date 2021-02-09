---
title: 如何：將參數加入至方法 |Microsoft Docs
description: 瞭解如何將參數加入至商務資料連線 (BDC) 方法，這可讓您將資訊傳遞至方法，或從方法傳回信息。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d568d5ca2025f1467fa96387493b1e8b4ed1ec6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931691"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>如何：將參數加入至方法
  使用參數將資訊傳遞至方法，或是從方法傳回信息。 所有方法都必須至少有一個參數。 如需如何設計參數以支援您想要建立的方法類型的詳細資訊，請參閱 [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)。

 當您將參數加入至方法時，Visual Studio 會將參數專案加入至專案中模型檔案的 XML。 如需參數元素之屬性的詳細資訊，請參閱 [參數](/previous-versions/office/developer/sharepoint-2010/ee557705(v=office.14))。

### <a name="to-add-a-parameter-to-a-method"></a>若要將參數加入至方法

1. 將方法新增至實體。

2. 在功能表列上，選擇 [**查看**  >  **其他 Windows**  >  **BDC 方法詳細資料**]。

     [ **BDC 方法詳細資料** ] 視窗隨即開啟。 如需詳細資訊，請參閱 [BDC 模型設計工具總覽](../sharepoint/bdc-model-design-tools-overview.md)。

3. 在 [ **BDC 方法詳細資料** ] 視窗中，展開方法的節點，然後展開 [ **參數** ] 節點。

4. 在 [ **加入參數** ] 清單中，選擇 [ **建立參數**]。

     新的參數會出現在 [ **參數** ] 節點底下。

5. 在功能表列上，選擇 [**視圖**  >  **屬性視窗]**。

6. 在 [ **屬性** ] 視窗中，將 [ **名稱** ] 屬性設定為合理的任何名稱。 例如，如果方法會傳回客戶，您可能會將方法命名為 **GetCustomers**。

7. 在 [ **BDC 方法詳細資料** ] 視窗中，開啟針對參數的方向所顯示的清單，然後選擇 [ **In**]、[ **InOut**]、[ **Out**] 或 [ **Return**]。

     如需有關為您所建立的類型方法選擇何種方向的詳細資訊，請參閱 [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)。

8. 修改參數的類型描述元。 如需詳細資訊，請參閱 [如何：定義參數的類型描述](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)元。

## <a name="see-also"></a>另請參閱
- [BDC 模型設計工具總覽](../sharepoint/bdc-model-design-tools-overview.md)
- [如何：將實體加入至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [如何：定義參數的類型描述元](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [如何：定義方法實例](../sharepoint/how-to-define-a-method-instance.md)
- [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)
