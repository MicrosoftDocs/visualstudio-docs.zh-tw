---
title: Outlook 表單區域中的自訂動作
description: 瞭解動作顯示按鈕（例如 [回復] 和 [全部回復]）可讓使用者回應 Microsoft Office Outlook 專案。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4fe77cddcfe810e73d13de81cc7280969c1d1b1c
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848192"
---
# <a name="custom-actions-in-outlook-form-regions"></a>Outlook 表單區域中的自訂動作
  動作會顯示可讓使用者回應 Microsoft Office Outlook 專案的按鈕。 例如，若要回應訊息項目，使用者可以按一下 [ **回復**]、[ **回復至全部**] 或 [ **轉寄** 動作] 按鈕。 上述每個動作都會建立新的訊息項目，並使用原始專案的資訊填入專案的欄位。

 您可以建立自訂動作來開啟任何種類的 Outlook 專案。 例如，您可以加入自訂動作，以開啟新的約會或工作專案。 設定自訂動作的屬性，或使用自訂程式碼來填入新專案的欄位。 自訂動作會出現在 [Outlook 偵測器] 視窗中開啟之專案的 [ **自訂動作** ] 下拉式清單中。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-custom-actions-to-a-form-region"></a>將自訂動作新增至表單區域
 若要將自訂動作加入至表單區域，請使用 [ **自訂動作** ] 對話方塊。 您可以開啟 [**自訂動作**] 對話方塊，方法是選取 **方案總管** 中的表單區域、展開 [**屬性] 視窗** 中的 [**資訊清單**] 節點、選取 [ **CustomActions** ] 屬性，然後按一下省略號按鈕 (![ASP.NET mobile 設計](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")工具]) 。

 您可以使用 [ **自訂動作** ] 對話方塊來指定 *目標表單*。 目標表單是使用者執行自訂動作時所顯示的表單。

 您也可以使用 [ **自訂動作** ] 對話方塊來指定要如何將原始專案中的資訊顯示在目標表單中。

 下表描述 [ **自訂動作** ] 對話方塊中可用的屬性。

|屬性|描述|
|--------------|-----------------|
|**AddressLike**|指定目標表單的定址方式。|
|**本文**|指定原始專案的主體如何附加至目標表單。|
|**啟用**|指出是否已啟用自訂動作。 如果這個屬性設定為 **false**，則會停用自訂動作。|
|**方法**|指定執行自訂動作時可使用的回應類型。 自訂動作可以傳送表單、開啟表單，或提示使用者是否要傳送或開啟表單。|
|**名稱**|指定您可以在程式碼中用來參考這個自訂動作的內部名稱。|
|**ShowOnRibbon**|指出是否要在原始專案的功能區上顯示自訂動作。|
|**SubjectPrefix**|指定在目標表單的主旨行開頭插入的文字。|
|**TargetForm**|指定目標表單的訊息類別名稱。 例如，輸入 **IPM。** 開啟工作表單的工作。|
|**標題**|指定自訂動作按鈕的標籤。|

## <a name="customize-a-custom-action-at-run-time"></a>在執行時間自訂自訂動作
 您也可以使用程式碼，將行為新增至自訂動作。 例如，您可以加入接受電子郵件收件者名稱的程式碼，並在新的約會專案中將這些名稱新增為出席者。 若要這樣做，請處理[MailItem 物件](/office/vba/api/Outlook.MailItem)的[CustomAction](/office/vba/api/Outlook.MailItem.CustomAction)事件。

## <a name="see-also"></a>另請參閱
- [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)
- [逐步解說：設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [將表單區域與 Outlook 訊息類別產生關聯](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
