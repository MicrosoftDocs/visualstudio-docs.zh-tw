---
title: "如何： 將篩選描述元加入至搜尋方法 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
ms.assetid: 228a6190-8cb8-4182-b6d9-d4c656f4a164
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ced25067161fe1429c14c4668d8b69a757080140
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>如何：將篩選描述元加入至搜尋方法
  篩選描述元可讓取用者的模型之前，它們執行，將值傳遞給方法。 如需詳細資訊，請參閱[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
 常見的案例之一是在 SharePoint 中的使用者想要擷取的外部內容類型符合某些準則的執行個體。 您可以將篩選描述元加入至搜尋方法，以支援此案例中。  
  
### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>若要將篩選描述元加入至搜尋方法  
  
1.  在**BDC 方法詳細資料**視窗中，展開搜尋方法的節點，展開 [**參數**] 節點，並將輸入的參數。 如需詳細資訊，請參閱[How to： 將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)。  
  
2.  在**方法詳細資料**視窗中，選擇參數的類型描述元。  
  
3.  在功能表列上選擇 [**檢視**，**屬性] 視窗**。  
  
4.  在**屬性**視窗中，將**型別名稱**適用於篩選的資料類型的屬性。  
  
     比方說，篩選可能會使用訂單日期來限制的方法所傳回的銷售訂單數目。 若要支援篩選，**型別名稱**類型描述元的屬性必須設定為**System.DateTime**。  
  
5.  在**方法詳細資料**視窗中，展開 **篩選描述元**節點。  
  
6.  在**新增篩選描述元**清單中，選擇**建立篩選器描述元**。  
  
     下方會出現新的篩選描述元**篩選描述元**節點。  
  
7.  在功能表列上選擇 [**檢視**，**屬性] 視窗**。  
  
8.  在**屬性**視窗中，選擇**類型**屬性。  
  
9. 在清單中所顯示**類型**屬性中，選擇您想要的篩選模式。  
  
     例如，若要建立使用訂單日期來限制搜尋工具方法中傳回的銷售訂單數量的篩選條件，請選擇**比較**。 比較篩選條件可確保搜尋工具方法傳回符合特定條件的執行個體。 如需每個篩選模式的詳細資訊，請參閱[類型的篩選條件受到 BDC](http://go.microsoft.com/fwlink/?LinkId=169287)。  
  
10. 在**屬性**視窗中，選擇**相關聯的類型描述元**屬性。  
  
11. 在清單中所顯示**相關聯的類型描述元**屬性中，選擇您稍早在此程序中建立的類型描述元。 這與篩選相關的搜尋方法的輸入參數。  
  
12. 加入程式碼會傳回資料的搜尋工具方法。 您可以做為條件選取查詢中使用的輸入的參數。  
  
     下列範例會傳回具有指定的訂購日期的銷售訂單。  
  
    > [!NOTE]  
    >  取代的值`ServerName`欄位與您的伺服器名稱。  
  
     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]  
  
## <a name="see-also"></a>請參閱  
 [如何： 加入搜尋方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何： 加入特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [如何： 將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何： 定義參數的類型描述元](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [將商業資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  