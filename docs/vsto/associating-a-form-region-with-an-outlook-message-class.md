---
title: "將表單區域與 Outlook 訊息類別產生關聯 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSTO.NewFormRegionWizard.InvalidMessageClassName
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FormRegionMessageClassAttribute
- form regions [Office development in Visual Studio], message classes
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2c09622189b335e58dc9cad15d415eb75385955f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="associating-a-form-region-with-an-outlook-message-class"></a>Associating a Form Region with an Outlook Message Class
  您可以指定哪些 Microsoft Office Outlook 項目顯示表單區域將表單區域與每個項目的訊息類別產生關聯。 例如，如果您想要的郵件項目底部附加表單區域，您就可以與 IPM 關聯表單區域。請注意訊息類別。  
  
 若要關聯與訊息類別的表單區域，指定中的訊息類別名稱**新的 Outlook 表單區域**精靈或將屬性套用至表單區域 factory 類別。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="understanding-outlook-message-classes"></a>了解 Outlook 訊息類別  
 Outlook 訊息類別來識別 Outlook 項目類型。 下表列出這些八個標準項目類型和其訊息類別名稱。  
  
|Outlook 項目類型|訊息類別名稱|  
|-----------------------|------------------------|  
|AppointmentItem|IPM。約會|  
|ContactItem|IPM。連絡人|  
|DistListItem|IPM。DistList|  
|JournalItem|IPM。活動|  
|MailItem|IPM。附註|  
|PostItem|IPM。Post 或 IPM。Post.RSS|  
|TaskItem|IPM。工作|  
  
 您也可以指定自訂訊息類別的名稱。 自訂訊息類別會識別您在 Outlook 中定義的自訂表單。  
  
> [!NOTE]  
>  為取代型和全部取代型表單區域，您可以指定新的自訂訊息類別名稱。 您不需要使用現有的自訂表單的訊息類別名稱。 自訂訊息類別名稱必須是唯一的。 為了確保名稱是唯一的一種方式為使用與下列類似的命名慣例： \< *StandardMessageClassName*>。\<*公司*>。\<*MessageClassName*> (例如： IPM。Note.Contoso.MyMessageClass)。  
  
## <a name="associating-a-form-region-with-an-outlook-message-class"></a>Associating a Form Region with an Outlook Message Class  
 有兩種方式可以將表單區域與訊息類別產生關聯：  
  
-   使用**新的 Outlook 表單區域**精靈。  
  
-   適用於類別屬性。  
  
### <a name="using-the-new-outlook-form-region-wizard"></a>使用新的 Outlook 表單區域精靈  
 最後一頁上**新的 Outlook 表單區域**精靈，您可以選取標準訊息類別，並輸入您想要與表單區域產生關聯的自訂訊息類別名稱。  
  
 無法使用，如果表單區域取代整個表單的預設頁面設計標準訊息類別。 您可以指定只能用於表單，將新頁面加入至表單或，就會附加至表單的下方的標準訊息類別名稱。 如需詳細資訊，請參閱[How to： 在 Outlook 增益集專案中加入表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)。  
  
 若要包含一個或多個自訂訊息類別，輸入其名稱中的**自訂訊息類別為何會顯示此表單區域？**方塊。  
  
 您輸入的名稱必須遵守下列指導方針：  
  
-   使用完整的訊息類別名稱 (例如:"IPM。Note.Contoso")。  
  
-   請使用分號分隔多個訊息類別名稱。  
  
-   不包括標準的 Outlook 訊息類別，"分號。請注意"或者"IPM。請連絡 」。 只包含自訂訊息類別，"分號。Note.Contoso"。  
  
-   單獨使用時，未指定基底訊息類別 (例如:"IPM")。  
  
-   不能超過 256 個字元，每個訊息類別名稱。  
  
 **新的 Outlook 表單區域**精靈會驗證您輸入的格式，當您按一下**完成**。  
  
> [!NOTE]  
>  **新的 Outlook 表單區域**精靈不會驗證您提供的訊息類別名稱是否正確，或為有效。  
  
 當您完成精靈，**新的 Outlook 表單區域**精靈會將屬性套用至包含指定的訊息類別名稱在表單區域類別。 您也可以手動套用這些屬性。  
  
### <a name="applying-class-attributes"></a>套用屬性類別  
 您可以將表單區域與 Outlook 訊息類別，在完成之後**新的 Outlook 表單區域**精靈。 若要這樣做，請將屬性套用至表單區域 factory 類別。  
  
 下列範例示範兩個<xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute>已套用至名為表單區域 factory 類別的屬性`myFormRegion`。 第一個屬性會將表單區域與郵件表單的標準訊息類別產生關聯。 第二個屬性會將表單區域名為的自訂訊息類別`IPM.Task.Contoso`。  
  
 [!code-vb[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs#1)]  
  
 屬性必須遵守下列指導方針：  
  
-   自訂訊息類別，使用完整的訊息類別名稱 (例如:"IPM。Note.Contoso")。  
  
-   單獨使用時，未指定基底訊息類別 (例如:"IPM")。  
  
-   不能超過 256 個字元，每個訊息類別名稱。  
  
-   請勿包含標準訊息類別的名稱，如果表單區域取代整個表單的預設頁面。 您可以指定只能用於表單，將新頁面加入至表單或，就會附加至表單的下方的標準訊息類別名稱。 如需詳細資訊，請參閱[How to： 在 Outlook 增益集專案中加入表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)。  
  
 當您建置專案時，visual Studio 就會驗證訊息類別名稱的格式。  
  
> [!NOTE]  
>  Visual Studio 不會驗證您提供的訊息類別名稱正確，或為有效。  
  
## <a name="see-also"></a>請參閱  
 [在執行階段存取表單區域](../vsto/accessing-a-form-region-at-run-time.md)   
 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)   
 [逐步解說： 設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [建立 Outlook 表單區域的指導方針](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [表單的名稱和訊息類別概觀](http://msdn.microsoft.com/library/office/ff867629.aspx)   
 [Outlook 表單和項目如何一起運作](http://msdn.microsoft.com/library/office/ff869706.aspx)  
  
  