---
title: HOW TO：將篩選描述元加入至搜尋方法 |Microsoft Docs
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
ms.openlocfilehash: ee555376a2943cb29344aad2ed94da2b8ab2ae36
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56617778"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>HOW TO：將篩選描述元加入至搜尋方法
  篩選描述元，讓取用者模型的執行之前，將值傳遞給方法。 如需詳細資訊，請參閱 <<c0> [ 設計 business data connectivity 模型](../sharepoint/designing-a-business-data-connectivity-model.md)。

 一個常見的案例是在 SharePoint 中的使用者想要擷取的外部內容類型符合某些準則的執行個體。 您可以將篩選描述元加入至搜尋方法，以支援此案例。

### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>若要將篩選描述元加入至搜尋方法

1.  在**BDC 方法詳細資料**視窗中，展開搜尋方法的節點，展開**參數** 節點，然後新增一個輸入的參數。 如需詳細資訊，請參閱[如何：新增參數至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)。

2.  在 [**方法的詳細資料**] 視窗中，選擇該參數的類型描述元。

3.  在功能表列上選擇 [**檢視** > **屬性] 視窗**。

4.  在 **屬性**視窗中，將**型別名稱**適用於篩選的資料類型的屬性。

     比方說，篩選可能會使用訂單日期來限制的方法所傳回的銷售訂單數目。 若要支援篩選，**型別名稱**的型別描述項的屬性必須設為**System.DateTime**。

5.  在 [**方法的詳細資料**] 視窗中，展開**篩選描述元**節點。

6.  在 **加入篩選描述元**清單中，選擇**建立的篩選描述元**。

     下方會出現新的篩選描述元**篩選描述元**節點。

7.  在功能表列上選擇 [**檢視** > **屬性] 視窗**。

8.  在 [**屬性**] 視窗中，選擇**型別**屬性。

9. 在清單中會出現**型別**屬性中，選擇您想要的篩選模式。

     例如，若要建立使用來限制搜尋方法中傳回的銷售訂單數量的訂單日期的篩選條件，請選擇**比較**。 比較篩選條件可確保搜尋方法會傳回符合特定條件的執行個體。 如需有關每個篩選模式的詳細資訊，請參閱 <<c0> [ 類型的支援篩選器的 BDC](http://go.microsoft.com/fwlink/?LinkId=169287)。

10. 在 [**屬性**] 視窗中，選擇**相關聯的型別描述項**屬性。

11. 在清單中會出現**相關聯的型別描述項**屬性中，選擇您稍早在此程序中建立的類型描述元。 這與篩選相關搜尋方法的輸入參數。

12. 加入程式碼會傳回資料的搜尋工具方法。 您可以做為條件選取查詢中使用的輸入的參數。

     下列範例會傳回具有指定的訂購日期的銷售訂單。

    > [!NOTE]
    >  值取代`ServerName`欄位與您伺服器的名稱。

     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]

## <a name="see-also"></a>另請參閱
- [如何：新增搜尋方法](../sharepoint/how-to-add-a-finder-method.md)
- [如何：新增特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)
- [如何：新增參數至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [如何：定義參數的型別描述元](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)
- [將商務資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
