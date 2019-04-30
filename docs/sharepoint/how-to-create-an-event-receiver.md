---
title: HOW TO：建立事件接收器 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.EventReceiver
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bc42a92e1d7dcc73bb6bc0433da4e6a31d7fefb2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62966753"
---
# <a name="how-to-create-an-event-receiver"></a>HOW TO：建立事件接收器
  藉由建立*事件接收器*，您可以回應使用者互動 SharePoint 項目，例如清單或清單項目時。 例如，當使用者將行事曆變更或刪除連絡人清單中的名稱，會觸發事件接收器中的程式碼。 遵循本主題，您可以了解如何將事件接收器加入至清單執行個體。

 若要完成這些步驟，您必須已安裝[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]和支援的 Windows 和 SharePoint 版本。 因為此範例需要 SharePoint 專案，您也必須已經完成本主題中的程序[逐步解說：建立 SharePoint 網站資料行、 內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)。

## <a name="adding-an-event-receiver"></a>加入事件接收器
 您在建立專案[逐步解說：建立 SharePoint 網站資料行、 內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)包含自訂的網站資料行、 自訂清單和內容類型。 在下列程序中，您會藉由新增一個簡單的事件處理常式 （事件接收器） 展開這個專案的清單執行個體，以示範如何處理 SharePoint 項目，例如清單中所發生事件。

#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>若要加入的清單執行個體中的事件接收器

1. 開啟您在中建立的專案[逐步解說：建立 SharePoint 網站資料行、 內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)。

2. 在 [**方案總管] 中**，選擇 SharePoint 專案節點，稱為**Clinic**。

3. 在功能表列中，選擇 [專案] > [加入新項目]。

4. 之下**Visual C#** 或**Visual Basic**，展開**SharePoint**  節點，然後選擇**2010年**項目。

5. 中**範本**窗格中，選擇**事件接收器**，其命名**TestEventReceiver1**，然後選擇**確定**  按鈕。

     **SharePoint 自訂精靈**隨即出現。

6. 在 **何種類型的事件接收器？** 清單中，選擇**清單項目事件**。

7. 在 **何種項目應該做為事件來源？** 清單中，選擇**病患 (Clinic\Patients)**。

8. 中**處理下列事件**清單中，選取旁邊的核取方塊**已加入的項目**，然後選擇**完成**按鈕。

     新的事件接收器的程式碼檔案包含的單一方法，名為`ItemAdded`。 在下一個步驟中，會將程式碼新增至這個方法，讓每個連絡人將會命名為 Scott Brown 預設。

9. 取代現有`ItemAdded`方法，以下列程式碼，然後選擇  **F5**機碼：

     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]

     在程式碼執行後，SharePoint 網站會出現在網頁瀏覽器。

10. 在 [快速啟動] 列中，選擇**病患**連結，然後再選擇**加入新項目**連結。

     新項目的項目表單隨即開啟。

11. 在欄位中，輸入資料，然後選擇**儲存** 按鈕。

     您選擇後**儲存** 按鈕，**病患名稱**Scott Brown 的名稱會自動更新資料行。

## <a name="see-also"></a>另請參閱

- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)