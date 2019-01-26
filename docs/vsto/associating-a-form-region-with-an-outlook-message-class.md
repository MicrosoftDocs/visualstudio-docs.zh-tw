---
title: Outlook 訊息類別相關聯的表單區域
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 5ac0b74981b7e4a364bbc551be132b79cc432448
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875819"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>Outlook 訊息類別相關聯的表單區域
  您可以指定哪些 Microsoft Office Outlook 項目顯示表單區域的表單區域關聯至每個項目的訊息類別。 例如，如果您想要的郵件項目底部附加表單區域，您可以將表單區域`IPM.Note`訊息類別。  
  
 訊息類別相關聯的表單區域，指定中的訊息類別名稱**新的 Outlook 表單區域**精靈或屬性套用至表單區域 factory 類別。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="understand-outlook-message-classes"></a>了解的 Outlook 訊息類別  
 Outlook 訊息類別會識別 Outlook 項目類型。 下表列出這些項目和其訊息類別名稱的八個標準類型。  
  
|Outlook 項目類型|訊息類別名稱|  
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
>  為取代型和全部取代型表單區域，您可以指定新的自訂訊息類別名稱。 您不需要使用現有的自訂表單的訊息類別名稱。 自訂訊息類別名稱必須是唯一的。 若要確保名稱是唯一的一個方式是使用如下所示的命名慣例：\<*StandardMessageClassName*>。\<*公司*>。\<*MessageClassName*> (例如： `IPM.Note.Contoso.MyMessageClass`)。  
  
## <a name="associate-a-form-region-with-an-outlook-message-class"></a>Outlook 訊息類別相關聯的表單區域  
 有兩種方式，將表單區域關聯的訊息類別：  
  
-   使用**新的 Outlook 表單區域**精靈。  
  
-   適用於類別屬性。  
  
### <a name="use-the-new-outlook-form-region-wizard"></a>使用新的 Outlook 表單區域精靈  
 在最後一頁**新的 Outlook 表單區域**精靈，您可以選取標準訊息類別，並輸入您要與表單區域相關聯的自訂訊息類別名稱。  
  
 標準訊息類別不可以使用表單區域設計來取代整個表單的預設頁面。 您可以指定只能用於表單，表單中新增新的頁面或，就會附加至表單底部的標準訊息類別名稱。 如需詳細資訊，請參閱[＜How to：將表單區域加入 Outlook 增益集專案](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)。  
  
 要包含一個或多個自訂訊息類別，請輸入其名稱的**的自訂訊息類別會顯示此表單區域？**  方塊中。  
  
 您輸入的名稱必須遵守下列指導方針：  
  
- 使用完整的訊息類別名稱 (例如：「 IPM。Note.Contoso")。  
  
- 請使用分號來分隔多個訊息類別名稱。  
  
- 不包括標準的 Outlook 訊息類別，「 分號。附註 」 或者 「 IPM。連絡 」。 只包含自訂訊息類別，「 分號。Note.Contoso"。  
  
- 單獨使用時，未指定基底訊息類別 (例如：「 IPM")。  
  
- 不能超過 256 個字元的每個訊息類別名稱。  
  
  **新的 Outlook 表單區域**當您按一下時，精靈會驗證您輸入的格式**完成**。  
  
> [!NOTE]  
>  **新的 Outlook 表單區域**精靈不會驗證您提供的訊息類別名稱是否正確或無效。  
  
 當您完成精靈中，**新的 Outlook 表單區域**精靈會將屬性套用至表單區域類別包含指定的訊息類別名稱。 您也可以手動套用這些屬性。  
  
### <a name="apply-class-attributes"></a>套用屬性類別  
 您可以將表單區域與 Outlook 訊息類別，您在完成後**新的 Outlook 表單區域**精靈。 若要這樣做，請將屬性套用至表單區域 factory 類別。  
  
 下列範例示範兩個<xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute>已套用至名為表單區域 factory 類別的屬性`myFormRegion`。 第一個屬性會將表單區域關聯至郵件表單的標準訊息類別。 第二個屬性會將表單區域關聯的自訂訊息類別，名為`IPM.Task.Contoso`。  
  
 [!code-vb[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs#1)]  
  
 屬性必須遵守下列指導方針：  
  
- 自訂訊息類別，使用 完整格式的訊息類別名稱 (例如：「 IPM。Note.Contoso")。  
  
- 單獨使用時，未指定基底訊息類別 (例如：「 IPM")。  
  
- 不能超過 256 個字元的每個訊息類別名稱。  
  
- 如果表單區域取代整個表單的預設頁面不包含標準訊息類別的名稱。 您可以指定只能用於表單，表單中新增新的頁面或，就會附加至表單底部的標準訊息類別名稱。 如需詳細資訊，請參閱[＜How to：將表單區域加入 Outlook 增益集專案](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)。  
  
  當您建置專案時，visual Studio 就會驗證訊息類別名稱的格式。  
  
> [!NOTE]  
>  Visual Studio 不會驗證您提供的訊息類別名稱正確或無效。  
  
## <a name="see-also"></a>另請參閱  
 [存取表單區域在執行階段](../vsto/accessing-a-form-region-at-run-time.md)   
 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)   
 [逐步解說：設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [若要建立 Outlook 表單區域的指導方針](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [表單的名稱和訊息類別的概觀](/office/vba/outlook/Concepts/Forms/form-name-and-message-class-overview)   
 [Outlook 表單和項目如何一起運作](/office/vba/outlook/Concepts/Forms/how-outlook-forms-and-items-work-together)  
