---
title: 如何：建立事件接收器 |Microsoft Docs
description: 建立事件接收器，讓您可以在使用者與 SharePoint 專案（例如清單或清單專案）互動時回應。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d0eebee6e37fbd6696923da0e470f05688fa0387
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216575"
---
# <a name="how-to-create-an-event-receiver"></a>如何：建立事件接收器
  藉由建立 *事件接收器*，您可以在使用者與 SharePoint 專案（例如清單或清單專案）互動時回應。 例如，當使用者變更行事曆或刪除連絡人清單中的名稱時，就會觸發事件接收器中的程式碼。 藉由遵循本主題，您可以瞭解如何將事件接收器新增至清單實例。

 若要完成這些步驟，您必須已安裝 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 和支援的 Windows 和 SharePoint 版本。 因為此範例需要 SharePoint 專案，所以您也必須完成本主題 [逐步解說：建立 SharePoint 的網站資料行、內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)中的程式。

## <a name="adding-an-event-receiver"></a>新增事件接收器
 您在 [逐步解說：建立 SharePoint 的網站資料行、內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) 中建立的專案包含自訂網站資料行、自訂清單和內容類型。 在下列程式中，您將擴充此專案，方法是將簡單的事件處理常式新增 (事件接收器) 至清單實例，以顯示如何處理 SharePoint 專案中發生的事件，例如清單。

#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>將事件接收器加入至清單實例

1. 開啟您在 [逐步解說：建立 SharePoint 的網站資料行、內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)中所建立的專案。

2. 在 **方案總管** 中， **選擇名為**[實務] 的 SharePoint 專案節點。

3. 在功能表列上，選擇 [ **Project**  >  **加入新專案**]。

4. 在 [ **Visual c #** ] 或 [ **Visual Basic**] 下，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 專案。

5. 在 [ **範本** ] 窗格中，選擇 [ **事件接收器**]，將它命名為 **TestEventReceiver1**，然後選擇 [ **確定]** 按鈕。

     [ **SharePoint 自訂] Wizard** 隨即出現。

6. 在 [ **您要哪一種類型的事件接收器？** ] 清單中，選擇 [ **清單專案事件**]。

7. 在 [ **哪個專案應該是事件來源？** ] 清單中，選擇 [ **患者 (Clinic\Patients)**。

8. 在 [ **處理下列事件** ] 清單中，選取 [ **新增專案**] 旁的核取方塊，然後選擇 [ **完成]** 按鈕。

     新事件接收器的程式碼檔案包含名為的單一方法 `ItemAdded` 。 在下一個步驟中，您會將程式碼加入至這個方法，讓每個連絡人依預設會命名為 Scott 棕色。

9. 以下列程式碼取代現有的 `ItemAdded` 方法，然後選擇 **F5** 鍵：

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb" id="Snippet1":::

     程式碼會執行，而且 SharePoint 網站會出現在網頁瀏覽器中。

10. 在 [快速啟動] 列上，選擇 [ **患者** ] 連結，然後選擇 [ **加入新專案** ] 連結。

     新專案的輸入表單隨即開啟。

11. 在欄位中輸入資料，然後選擇 [ **儲存** ] 按鈕。

     選擇 [ **儲存** ] 按鈕之後，[ **患者名稱** ] 欄會自動更新為 Scott 棕色的名稱。

## <a name="see-also"></a>另請參閱

- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)