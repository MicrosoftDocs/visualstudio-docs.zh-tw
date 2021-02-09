---
title: 如何：為特定的清單實例建立事件接收器 |Microsoft Docs
titleSuffix: ''
description: 為特定的清單實例建立事件接收器。 清單實例事件接收器會回應任何清單定義實例中發生的事件。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
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
ms.openlocfilehash: 664a7ac4e763b2378cf30603c417aacde27c2e47
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925488"
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>如何：為特定的清單實例建立事件接收器
  清單實例事件接收器會回應任何清單定義實例中發生的事件。 雖然事件接收器範本未啟用特定清單實例的目標，但您可以修改範圍為清單定義的事件接收器，以回應特定清單實例中的事件。

 若要以特定清單實例為目標，請在事件接收器的 *Elements.xml* 中，將取代為 `ListTemplateId` `ListUrl` ，並加入清單實例的 URL。

## <a name="create-a-list-instance-event-receiver"></a>建立清單實例事件接收器
 下列步驟顯示如何修改清單專案事件接收器，以只回應自訂公告清單實例中發生的事件。

#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>若要修改事件接收器以回應特定清單實例

1. 在瀏覽器中開啟 SharePoint 網站。

2. 在 [流覽] 窗格中， **列出** 連結。

3. 在 [ **所有網站內容** ] 頁面中，選擇 [ **建立** ] 連結。

4. 在 [ **建立** ] 對話方塊中，選擇 [ **宣告** 類型]，將公告命名為 **TestAnnouncements**，然後選擇 [ **建立** ] 按鈕。

5. 在中 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，建立事件接收器專案。

6. 在 [ **您要哪一種類型的事件接收器？** ] 清單中，選擇 [ **清單專案事件**]。

    > [!NOTE]
    > 您也可以選取範圍為清單定義的任何其他類型的事件接收器，例如， **列出電子郵件事件** 或 **列出工作流程事件**。

7. 在 [ **哪個專案應該是事件來源？** ] 清單中，選擇 [ **宣告**]。

8. 在 [ **處理下列事件** ] 清單中，選取 [ **要加入的專案** ] 核取方塊，然後選擇 [ **完成]** 按鈕。

9. 在 **方案總管** 的 [EventReceiver1] 下，開啟 *Elements.xml*。

     事件接收器目前是使用下列程式碼行參考 [公告] 清單定義：

    ```xml
    <Receivers ListTemplateId="104">
    ```

     請將這行變更為以下文字：

    ```xml
    <Receivers ListUrl="Lists/TestAnnouncements">
    ```

     這會指示事件接收器只回應您剛才建立的新 **TestAnnouncements** 公告清單中發生的事件。 您可以將 `ListURL` 屬性變更為參考 SharePoint 伺服器上的任何清單實例。

10. 開啟事件接收器的程式碼檔案，並在 ItemAdding 方法中放入中斷點。

11. 選擇 **F5** 鍵來建立並執行方案。

12. 在 SharePoint 中，選擇流覽窗格中的 [ **TestAnnouncements** ] 連結。

13. 選擇 [ **加入新公告** ] 連結。

14. 輸入公告的標題，然後選擇 [ **儲存** ] 按鈕。

     請注意，當新專案新增至自訂公告清單時，就會叫用中斷點。

15. 選擇 **F5** 鍵以繼續。

16. 在流覽窗格中，選擇 [ **清單** ] 連結，然後選擇 [ **公告** ] 連結。

17. 加入新的公告。

     請注意，因為接收者設定為只回應自訂公告清單實例 **TestAnnouncements** 中的事件，所以不會在新的公告上觸發事件接收器。

## <a name="see-also"></a>另請參閱
- [如何：建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md)
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
