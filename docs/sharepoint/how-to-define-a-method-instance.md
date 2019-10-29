---
title: 如何：定義方法實例 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method
- Business Data Connectivity service [SharePoint development in Visual Studio], method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0e21900e87278ad500ee8497d1dd0c49350695d1
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981802"
---
# <a name="how-to-define-a-method-instance"></a>如何：定義方法實例
  針對模型中的每個方法，您必須至少定義一個方法實例。

 使用 [ **BDC 方法詳細資料**] 視窗加入方法實例。 當您加入方法實例時，Visual Studio 會將 `<MethodInstance>` 元素加入至專案中模型檔案的 XML。 如需 `<MethodInstance>` 元素之屬性的詳細資訊，請參閱[MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14))。

### <a name="to-define-a-method-instance"></a>若要定義方法實例

1. 在 [ **BDC 方法詳細資料**] 視窗中，展開方法的節點，然後展開 [**實例**] 節點。

2. 在 [**加入方法實例**] 清單中，選擇 [**建立 Finder 實例**]。

     新的方法實例會出現在 [**實例**] 節點底下。

3. 在功能表列上，選擇 視圖 ** > 屬性視窗**。

4. 在 [**屬性**] 視窗中，設定方法實例的屬性。 如需每個屬性的詳細資訊，請參閱[MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14))。

## <a name="see-also"></a>請參閱
- [BDC 模型設計工具總覽](../sharepoint/bdc-model-design-tools-overview.md)
- [如何：將實體加入至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [如何：將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [如何：定義參數的類型描述元](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)
