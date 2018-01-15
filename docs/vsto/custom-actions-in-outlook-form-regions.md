---
title: "自訂動作，在 Outlook 表單區域 |Microsoft 文件"
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
helpviewer_keywords:
- form regions [Office development in Visual Studio], custom actions
- custom actions [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 66a4d81728d438a749b46e42b003c02d08f13d67
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="custom-actions-in-outlook-form-regions"></a>Outlook 表單區域中的自訂動作
  動作顯示按鈕，可讓使用者回應的 Microsoft Office Outlook 項目。 例如，若要回應的郵件項目，使用者按一下**回覆**，**全部回覆**，或**向前**動作按鈕。 每個動作會建立新的郵件項目，並使用來自原始項目的資訊填入的項目欄位。  
  
 您可以建立自訂動作可開啟任何種類的 Outlook 項目。 例如，您可以加入自訂動作會開啟新的約會或工作項目。 設定自訂動作的屬性，或使用自訂程式碼來填入新的項目欄位。 自訂動作會出現在**自訂動作**Outlook 檢查 視窗中開啟的項目 下拉式清單。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="adding-custom-actions-to-a-form-region"></a>將自訂動作加入至表單區域  
 若要將自訂動作加入至表單區域，使用**自訂動作** 對話方塊。 您可以開啟**自訂動作**對話方塊**方案總管中**展開**資訊清單**] 節點，選取**CustomActions**屬性，然後按一下 [省略符號按鈕 (![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形"))。  
  
 您可以使用**自訂動作**對話方塊來指定*目標表單*。 目標表單是使用者執行自訂動作時出現的表單。  
  
 您也可以使用**自訂動作**對話方塊來指定您要如何從原始的項目出現在目標表單中的資訊。  
  
 下表描述中可用的屬性**自訂動作** 對話方塊。  
  
|屬性|描述|  
|--------------|-----------------|  
|**AddressLike**|指定如何將解決目標表單。|  
|**本文**|指定主體的原始項目附加至目標表單的方式。|  
|**已啟用**|指出是否已啟用自訂的動作。 如果這個屬性設定為**false**，自訂動作會停用。|  
|**方法**|執行自訂動作時，請指定可用的回應類型。 自訂動作可以傳送表單、 開啟表單，或提示使用者是否要傳送，或開啟表單。|  
|**名稱**|指定可用來參考這個程式碼中的自訂動作的內部名稱。|  
|**ShowOnRibbon**|指出是否要顯示的原始項目功能區上的自訂動作。|  
|**SubjectPrefix**|指定插入目標表單的主旨列開頭的文字。|  
|**TargetForm**|指定目標表單的訊息類別名稱。 例如，輸入**IPM。工作**若要開啟的工作表單。|  
|**標題**|指定自訂動作按鈕標籤。|  
  
## <a name="customizing-a-custom-action-at-run-time"></a>自訂執行階段的自訂動作  
 您也可以使用程式碼的自訂動作來新增行為。 例如，您可以加入接受的電子郵件收件者名稱，並將這些名稱在新的約會項目出席者的程式碼。 若要這樣做，請處理[CustomAction](http://msdn.microsoft.com/library/office/ff862186.aspx)事件[MailItem 物件](http://msdn.microsoft.com/library/office/ff861332.aspx)。  
  
## <a name="see-also"></a>請參閱  
 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)   
 [逐步解說： 設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [讓表單區域與 Outlook 訊息類別產生關聯](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  