---
title: 將表單區域與 Outlook 訊息類別產生關聯
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 45db262b6bf7843a3893c5d60f0b6eaea5fcb70b
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254568"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>將表單區域與 Outlook 訊息類別產生關聯
  您可以將表單區域與每個專案的訊息類別產生關聯，藉以指定哪些 Microsoft Office Outlook 專案顯示表單區域。 例如，如果您想要將表單區域附加至訊息項目的底部，您可以將表單區域與`IPM.Note` message 類別產生關聯。

 若要將表單區域與訊息類別產生關聯，請在 [新的**Outlook 表單區域**] 嚮導中指定訊息類別名稱，或將屬性套用至表單區域 factory 類別。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="understand-outlook-message-classes"></a>瞭解 Outlook 訊息類別
 Outlook 訊息類別可識別 Outlook 專案的類型。 下表列出這八種標準類型的專案及其訊息類別名稱。

|Outlook 專案類型|訊息類別名稱|
|-----------------------|------------------------|
|AppointmentItem|`IPM.Appointment`|
|ContactItem|`IPM.Contact`|
|DistListItem|`IPM.DistList`|
|JournalItem|`IPM.Activity`|
|MailItem|`IPM.Note`|
|PostItem|`IPM.Post` 或 `IPM.Post.RSS`|
|TaskItem|`IPM.Task`|

 您也可以指定自訂訊息類別的名稱。 自訂訊息類別會識別您在 Outlook 中定義的自訂表單。

> [!NOTE]
> 針對取代和全部取代表單區域，您可以指定新的自訂訊息類別名稱。 您不需要使用現有自訂表單的訊息類別名稱。 自訂訊息類別的名稱必須是唯一的。 確保名稱是唯一的其中一種方式，就是使用如下所示的命名慣例：\<*StandardMessageClassName*>。*公司 >* 。 \<MessageClassName > （例如： `IPM.Note.Contoso.MyMessageClass`）。 \<

## <a name="associate-a-form-region-with-an-outlook-message-class"></a>將表單區域與 Outlook 訊息類別產生關聯
 有兩種方式可讓表單區域與訊息類別產生關聯：

- 使用 [**新的 Outlook 表單區域**] wizard。

- 套用類別屬性。

### <a name="use-the-new-outlook-form-region-wizard"></a>使用新的 Outlook 表單區域 wizard
 在 [**新的 Outlook 表單區域**] wizard 的最後一頁，您可以選取 [標準訊息類別]，然後輸入您想要與表單區域產生關聯的自訂訊息類別名稱。

 如果表單區域是設計來取代表單的整個表單或預設頁面，則無法使用標準訊息類別。 您只能針對將新頁面新增至表單或附加至表單底部的表單，指定標準訊息類別名稱。 如需詳細資訊，請參閱[如何：將表單區域加入至 Outlook 增益集專案](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)。

 若要包含一或多個自訂訊息類別，請在 [**自訂訊息類別將顯示此表單區域？** ] 方塊中輸入其名稱。

 您輸入的名稱必須符合下列指導方針：

- 使用完整的訊息類別名稱（例如：IPM.TASK.TASKFORMREGION.請注意 Contoso "）。

- 請使用分號來分隔多個訊息類別名稱。

- 請勿包含標準的 Outlook 訊息類別，例如 "IPM。注意 "或" IPM。Contact "。 只包含自訂訊息類別，例如 "IPM。請注意 Contoso」。

- 請勿單獨指定基底訊息類別（例如："IPM"）。

- 針對每個訊息類別名稱，請勿超過256個字元。

  當您按一下 **[完成**] 時，[**新的 Outlook 表單區域**] wizard 會驗證您的輸入格式。

> [!NOTE]
> [**新的 Outlook 表單區域**] wizard 不會驗證您提供的訊息類別名稱是否正確或有效。

 當您完成嚮導時，[**新的 Outlook 表單區域**] 嚮導會將屬性套用至包含指定之訊息類別名稱的表單區域類別。 您也可以手動套用這些屬性。

### <a name="apply-class-attributes"></a>套用類別屬性
 完成 [**新的 Outlook 表單區域**] wizard 之後，您可以將表單區域與 Outlook 訊息類別產生關聯。 若要這麼做，請將屬性套用至表單區域 factory 類別。

 下列範例顯示兩個<xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute>已套用至名為`myFormRegion`之表單區域 factory 類別的屬性。 第一個屬性會將表單區域與郵件訊息表單的標準訊息類別產生關聯。 第二個屬性會將表單區域與名為`IPM.Task.Contoso`的自訂訊息類別產生關聯。

 [!code-vb[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs#1)]

 屬性必須符合下列指導方針：

- 針對自訂訊息類別，請使用完整的訊息類別名稱（例如：IPM.TASK.TASKFORMREGION.請注意 Contoso "）。

- 請勿單獨指定基底訊息類別（例如："IPM"）。

- 針對每個訊息類別名稱，請勿超過256個字元。

- 如果表單區域取代表單的整個表單或預設頁面，請勿包含標準訊息類別的名稱。 您只能針對將新頁面新增至表單或附加至表單底部的表單，指定標準訊息類別名稱。 如需詳細資訊，請參閱[如何：將表單區域加入至 Outlook 增益集專案](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)。

  當您建立專案時，Visual Studio 會驗證訊息類別名稱的格式。

> [!NOTE]
> Visual Studio 不會驗證您提供的訊息類別名稱是否正確或有效。

## <a name="see-also"></a>另請參閱
- [在執行時間存取表單區域](../vsto/accessing-a-form-region-at-run-time.md)
- [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)
- [逐步解說：設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [建立 Outlook 表單區域的指導方針](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [表單名稱和訊息類別總覽](/office/vba/outlook/Concepts/Forms/form-name-and-message-class-overview)
- [Outlook 表單和專案如何共同作業](/office/vba/outlook/Concepts/Forms/how-outlook-forms-and-items-work-together)
