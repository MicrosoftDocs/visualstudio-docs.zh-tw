---
title: 如何：將篩選描述元加入至 Finder 方法 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f9dd853142d970cd14de20f4782accb3ce3e17eb
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986242"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>如何：將篩選描述元加入至 Finder 方法
  篩選描述元可讓模型的取用者在執行之前，將值傳遞給方法。 如需詳細資訊，請參閱[設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)。

 其中一個常見的案例是，SharePoint 中的使用者想要抓取符合某些準則的外部內容類型實例。 您可以藉由將篩選描述元新增至搜尋工具方法來支援此案例。

### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>若要將篩選描述元加入至 Finder 方法

1. 在 [ **BDC 方法詳細資料**] 視窗中，展開搜尋工具方法的節點，展開 [**參數**] 節點，然後加入輸入參數。 如需詳細資訊，請參閱[如何：將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)。

2. 在 [**方法詳細資料**] 視窗中，選擇參數的類型描述元。

3. 在功能表列上，選擇 視圖 ** > 屬性視窗**。

4. 在 [**屬性**] 視窗中，將 [**類型名稱**] 屬性設定為適用于篩選準則的資料類型。

     例如，篩選可能會使用訂單日期來限制方法所傳回的銷售訂單數目。 若要支援該篩選，類型描述元的**類型名稱**屬性必須**設定為 system.string。**

5. 在 [**方法詳細資料**] 視窗中，展開 [**篩選描述**項] 節點。

6. 在 [**加入篩選描述**項] 清單中，選擇 [**建立篩選描述**項]。

     新的篩選描述項會出現在 [**篩選器描述**項] 節點底下。

7. 在功能表列上，選擇 視圖 ** > 屬性視窗**。

8. 在 [**屬性**] 視窗中，選擇 [**類型**] 屬性。

9. 在 [**類型**] 屬性出現的清單中，選擇您想要的篩選模式。

     例如，若要建立使用訂單日期來限制搜尋工具方法中傳回之銷售訂單數目的篩選準則，請選擇 [**比較**]。 比較篩選準則可確保 finder 方法只會傳回符合特定條件的實例。 如需每個篩選模式的詳細資訊，請參閱[BDC 支援的篩選類型](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14))。

10. 在 [**屬性**] 視窗中，選擇 [**關聯的類型描述**元] 屬性。

11. 在出現于 [**關聯的類型描述**元] 屬性的清單中，選擇您稍早在此程式中建立的類型描述元。 這會使篩選器與搜尋工具方法的輸入參數產生關聯。

12. 將程式碼加入至會傳回資料的搜尋工具方法。 您可以在 select 查詢中使用輸入參數作為條件。

     下列範例會傳回具有指定之訂單日期的銷售訂單。

    > [!NOTE]
    > 將 [`ServerName`] 欄位的值取代為您的伺服器名稱。

     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]

## <a name="see-also"></a>請參閱
- [如何：加入 Finder 方法](../sharepoint/how-to-add-a-finder-method.md)
- [如何：加入特定的 Finder 方法](../sharepoint/how-to-add-a-specific-finder-method.md)
- [如何：將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [如何：定義參數的類型描述元](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)
- [將商務資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
