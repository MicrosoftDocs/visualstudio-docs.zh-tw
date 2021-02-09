---
title: 將表單區域與 Outlook 訊息類別產生關聯
description: 瞭解如何將表單區域與每個專案的 message 類別產生關聯，以指定哪些 Microsoft Office Outlook 專案顯示表單區域。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.InvalidMessageClassName
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FormRegionMessageClassAttribute
- form regions [Office development in Visual Studio], message classes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0bbbd381ff84714b780bbb817ccfea64ac05e949
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882540"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>將表單區域與 Outlook 訊息類別產生關聯
  您可以將表單區域與每個專案的 message 類別產生關聯，以指定哪些 Microsoft Office Outlook 專案顯示表單區域。 例如，如果您想要將表單區域附加到訊息項目的底部，您可以建立表單區域與 `IPM.Note` message 類別的關聯。

 若要建立表單區域與訊息類別之間的關聯，請在 [ **新的 Outlook 表單區域** ] 嚮導中指定訊息類別名稱，或將屬性套用至表單區域 factory 類別。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="understand-outlook-message-classes"></a>瞭解 Outlook 訊息類別
 Outlook 訊息類別會識別 Outlook 專案的類型。 下表列出這八種標準類型的專案及其訊息類別名稱。

|Outlook 專案類型|訊息類別名稱|
|-----------------------|------------------------|
|AppointmentItem|`IPM.Appointment`|
|ContactItem|`IPM.Contact`|
|DistListItem|`IPM.DistList`|
|JournalItem|`IPM.Activity`|
|MailItem|`IPM.Note`|
|PostItem|`IPM.Post` 或 `IPM.Post.RSS`|
| TaskItem|`IPM.Task`|

 您也可以指定自訂訊息類別的名稱。 自訂訊息類別會識別您在 Outlook 中定義的自訂表單。

> [!NOTE]
> 針對取代和全部取代表單區域，您可以指定新的自訂訊息類別名稱。 您不需要使用現有自訂表單的訊息類別名稱。 自訂訊息類別的名稱必須是唯一的。 確保名稱是唯一的方法之一，就是使用類似下列的命名慣例： \<*StandardMessageClassName*> ... \<*Company*>\<*MessageClassName*>  (例如： `IPM.Note.Contoso.MyMessageClass`) 。

## <a name="associate-a-form-region-with-an-outlook-message-class"></a>將表單區域與 Outlook 訊息類別產生關聯
 有兩種方式可以將表單區域與 message 類別產生關聯：

- 使用 [ **新的 Outlook 表單區域** ] wizard。

- 套用類別屬性。

### <a name="use-the-new-outlook-form-region-wizard"></a>使用新的 Outlook 表單區域 wizard
 在 [ **新的 Outlook 表單區域** ] 的最後一個頁面上，您可以選取 [標準訊息類別]，然後輸入您想要與表單區域產生關聯的自訂訊息類別名稱。

 如果表單區域是設計來取代整個表單或表單的預設頁面，則無法使用標準訊息類別。 您只能針對將新頁面新增至表單或附加至表單底部的表單，指定標準訊息類別名稱。 如需詳細資訊，請參閱 [如何：在 Outlook 增益集專案中加入表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)。

 若要包含一或多個自訂訊息類別，請在 [ **哪些自訂訊息類別將顯示此表單區域？** ] 方塊中輸入其名稱。

 您輸入的名稱必須符合下列指導方針：

- 使用完整訊息類別名稱 (例如： "IPM。請注意，Contoso ") 。

- 使用分號來分隔多個訊息類別名稱。

- 請勿包含標準的 Outlook 訊息類別，例如 "IPM。注意： "或" IPM。連絡人」。 只包含自訂訊息類別，例如 "IPM。請注意： Contoso」。

- 請勿指定 base message 類別本身 (例如： "IPM" ) 。

- 請勿超過每個訊息類別名稱256個字元。

  當您按一下 **[完成]** 時，**新的 Outlook 表單區域** wizard 會驗證您輸入的格式。

> [!NOTE]
> **新的 Outlook 表單區域** wizard 不會驗證您提供的訊息類別名稱是否正確或有效。

 當您完成嚮導時，[ **新的 Outlook 表單區域** ] wizard 會將屬性套用至包含指定之訊息類別名稱的表單區域類別。 您也可以手動套用這些屬性。

### <a name="apply-class-attributes"></a>套用類別屬性
 當您完成 **新的 Outlook 表單區域** wizard 之後，您可以將表單區域與 Outlook 訊息類別產生關聯。 若要這樣做，請將屬性套用至表單區域 factory 類別。

 下列範例顯示已 <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> 套用至名為之表單區域 factory 類別的兩個屬性 `myFormRegion` 。 第一個屬性會將表單區域與郵件訊息表單的標準訊息類別產生關聯。 第二個屬性會將表單區域與名為的自訂訊息類別產生關聯 `IPM.Task.Contoso` 。

 [!code-vb[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs#1)]

 屬性必須符合下列指導方針：

- 針對自訂訊息類別，請使用完整訊息類別名稱 (例如： "IPM。請注意，Contoso ") 。

- 請勿指定 base message 類別本身 (例如： "IPM" ) 。

- 請勿超過每個訊息類別名稱256個字元。

- 如果表單區域取代整個表單或表單的預設頁面，請勿包含標準訊息類別的名稱。 您只能針對將新頁面新增至表單或附加至表單底部的表單，指定標準訊息類別名稱。 如需詳細資訊，請參閱 [如何：在 Outlook 增益集專案中加入表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)。

  當您建立專案時，Visual Studio 會驗證訊息類別名稱的格式。

> [!NOTE]
> Visual Studio 不會驗證您提供的訊息類別名稱是否正確或有效。

## <a name="see-also"></a>另請參閱
- [在執行時間存取表單區域](../vsto/accessing-a-form-region-at-run-time.md)
- [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)
- [逐步解說：設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [建立 Outlook 表單區域的指導方針](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [表單名稱和訊息類別總覽](/office/vba/outlook/Concepts/Forms/form-name-and-message-class-overview)
- [Outlook 表單和專案如何一起運作](/office/vba/outlook/Concepts/Forms/how-outlook-forms-and-items-work-together)
