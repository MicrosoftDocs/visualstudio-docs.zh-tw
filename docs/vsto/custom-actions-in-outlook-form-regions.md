---
title: Outlook 表單區域中的自訂動作
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], custom actions
- custom actions [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4e2ad8e1c3b55d479cb031fe920e3027dbc1788c
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671062"
---
# <a name="custom-actions-in-outlook-form-regions"></a>Outlook 表單區域中的自訂動作
  動作會顯示按鈕，讓使用者能夠回應 Microsoft Office Outlook 項目。 例如，若要回應的郵件項目，使用者按一下**回覆**，**全部回覆**，或**向前**動作按鈕。 每個動作建立新的郵件項目，並使用來自原始項目的資訊填入的項目欄位。  
  
 您可以建立自訂動作會開啟任何種類的 Outlook 項目。 比方說，您可以加入自訂動作會開啟新的約會或工作項目。 設定自訂動作的屬性，或使用自訂程式碼來填入新的項目中的欄位。 自訂動作會出現在**自訂動作**下拉式清單中的 Outlook 偵測器視窗開啟時的項目。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="add-custom-actions-to-a-form-region"></a>將自訂動作加入至表單區域  
 若要加入表單區域中的自訂動作，請使用**自訂動作** 對話方塊。 您可以開啟**自訂動作**對話方塊**方案總管 中**展開**資訊清單** 節點，選取**CustomActions**屬性，然後按一下 省略符號按鈕 (![ASP.NET 行動設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形"))。  
  
 您可以使用**自訂動作**對話方塊來指定*目標表單*。 目標表單是使用者執行自訂動作時出現的表單。  
  
 您也可以使用**自訂動作**對話方塊來指定您要如何從原始的項目，才會出現在目標表單的資訊。  
  
 下表描述中所提供的屬性**自訂動作** 對話方塊。  
  
|屬性|描述|  
|--------------|-----------------|  
|**AddressLike**|指定目標表單將會如何解決。|  
|**本文**|指定主體的原始項目附加至目標表單的方式。|  
|**已啟用**|指出是否已啟用的自訂動作。 如果這個屬性設定為**false**，自訂動作會停用。|  
|**方法**|執行自訂動作時，請指定可用的回應類型。 自訂動作可以傳送表單中，開啟表單，或提示使用者是否要傳送，或開啟表單。|  
|**名稱**|指定可供您參考此自訂動作，在程式碼中的內部名稱。|  
|**ShowOnRibbon**|指出是否要顯示原始項目的功能區上的 自訂動作。|  
|**SubjectPrefix**|指定插入目標表單的主旨列開頭的文字。|  
|**TargetForm**|指定目標表單的訊息類別名稱。 例如，輸入**IPM。工作**若要開啟的工作表單。|  
|**標題**|指定自訂動作按鈕的標籤。|  
  
## <a name="customize-a-custom-action-at-runtime"></a>自訂執行階段的自訂動作  
 您也可以將行為加入自訂動作使用的程式碼中。 例如，您可以加入接受的電子郵件收件者名稱，並將這些名稱加入為新的約會項目中的出席者的程式碼。 若要這樣做，請處理[CustomAction](/office/vba/api/Outlook.MailItem.CustomAction)事件[MailItem 物件](/office/vba/api/Outlook.MailItem)。  
  
## <a name="see-also"></a>另請參閱  
 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)   
 [逐步解說： 設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Outlook 訊息類別相關聯的表單區域](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  