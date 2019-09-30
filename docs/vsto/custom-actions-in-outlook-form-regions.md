---
title: Outlook 表單區域中的自訂動作
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], custom actions
- custom actions [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 817cf9fe8698c2908e873246a8971f90fe72b460
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254447"
---
# <a name="custom-actions-in-outlook-form-regions"></a>Outlook 表單區域中的自訂動作
  動作會顯示可讓使用者回應 Microsoft Office Outlook 專案的按鈕。 例如，若要回應訊息項目，使用者可以按一下 [**回復**]、[**全部回復**] 或 [**轉寄**動作] 按鈕。 所有這些動作都會建立新的訊息項目，並使用原始專案中的資訊填入專案的欄位。

 您可以建立自訂動作，以開啟任何種類的 Outlook 專案。 例如，您可以加入自訂動作，以開啟新的約會或工作專案。 設定自訂動作的屬性，或使用自訂程式碼來填入新專案的欄位。 自訂動作會出現在 [Outlook 偵測器] 視窗中開啟之專案的 [**自訂動作**] 下拉式集中。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-custom-actions-to-a-form-region"></a>將自訂動作新增至表單區域
 若要將自訂動作新增至表單區域，請使用 [**自訂動作**] 對話方塊。 您可以開啟 **自訂動作**] 對話方塊，方法是在**方案總管**中選取表單區域，展開 [**屬性] 視窗**中的 [**資訊清單**] 節點，選取 [ **CustomActions** ] 屬性，然後按一下 [省略號按鈕（![ASP.NET mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET mobile 設計工具橢圓形")）。

 您可以使用 [**自訂動作**] 對話方塊來指定*目標表單*。 目標表單是使用者執行自訂動作時所顯示的表單。

 您也可以使用 [**自訂動作**] 對話方塊，指定要如何在目標表單中顯示原始專案的資訊。

 下表描述 [**自訂動作**] 對話方塊中可用的屬性。

|屬性|描述|
|--------------|-----------------|
|**AddressLike**|指定目標表單的定址方式。|
|**本文**|指定原始專案的主體如何附加至目標表單。|
|**已啟用**|指出是否已啟用自訂動作。 如果此屬性設定為**false**，則會停用自訂動作。|
|**方法**|指定自訂動作執行時可用的回應類型。 自訂動作可以傳送表單、開啟表單，或提示使用者是否要傳送或開啟表單。|
|**名稱**|指定您可以在程式碼中用來參考此自訂動作的內部名稱。|
|**ShowOnRibbon**|指出是否要在原始專案的功能區上顯示自訂動作。|
|**SubjectPrefix**|指定在目標表單的主旨行開頭插入的文字。|
|**TargetForm**|指定目標表單的訊息類別名稱。 例如，輸入**IPM。用來開啟**工作表單的工作。|
|**標題**|指定自訂動作按鈕的標籤。|

## <a name="customize-a-custom-action-at-run-time"></a>在執行時間自訂自訂動作
 您也可以使用程式碼，將行為新增至自訂動作。 例如，您可以加入接受電子郵件收件者名稱的程式碼，並在新的約會專案中將這些姓名新增為出席者。 若要這麼做，請處理[MailItem 物件](/office/vba/api/Outlook.MailItem)的[CustomAction](/office/vba/api/Outlook.MailItem.CustomAction)事件。

## <a name="see-also"></a>另請參閱
- [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)
- [逐步解說：設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [將表單區域與 Outlook 訊息類別產生關聯](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
