---
title: Outlook 物件模型總覽
description: 瞭解如何與 Outlook 物件模型提供的物件互動，以開發 Microsoft Outlook 的 VSTO 增益集。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.OutlookAddin
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], object model overview
- object models [Office development in Visual Studio], Office
- objects [Office development in Visual Studio], Office object models
- object models [Office development in Visual Studio], Outlook
- Office object models
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 83ada85ba346e83e5bc5ebc01e91b11be0e844e1
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528054"
---
# <a name="outlook-object-model-overview"></a>Outlook 物件模型總覽
  若要開發 Microsoft Office Outlook 的 VSTO 增益集，您可以與 Outlook 物件模型提供的物件進行互動。 Outlook 物件模型會提供表示使用者介面中各種項目的類別和介面。 例如， <xref:Microsoft.Office.Interop.Outlook.Application> 物件表示整個應用程式、 <xref:Microsoft.Office.Interop.Outlook.Folder> 物件表示含有電子郵件訊息或其他項目的資料夾，而 <xref:Microsoft.Office.Interop.Outlook.MailItem> 物件則表示電子郵件訊息。

 此主題提供 Outlook 物件模型中部分主要物件的簡要概觀。 如需可深入瞭解整個 Outlook 物件模型的資源，請參閱 [使用 outlook 物件模型檔](#refdoc)。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="access-objects-in-an-outlook-project"></a>存取 Outlook 專案中的物件
 Outlook 會提供許多您可以與之互動的物件。 若要有效使用物件模型，您應該熟悉下列最上層物件：

- <xref:Microsoft.Office.Interop.Outlook.Application>

- <xref:Microsoft.Office.Interop.Outlook.Explorer>

- <xref:Microsoft.Office.Interop.Outlook.Inspector>

- <xref:Microsoft.Office.Interop.Outlook.Folder>

- <xref:Microsoft.Office.Interop.Outlook.MailItem>

- <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>

- <xref:Microsoft.Office.Interop.Outlook.TaskItem>

- <xref:Microsoft.Office.Interop.Outlook.ContactItem>

### <a name="application-object"></a>應用程式物件
 <xref:Microsoft.Office.Interop.Outlook.Application> 物件表示 Outlook 應用程式，而且它是 Outlook 物件模型中的最上層物件。 這個物件中某些最重要的成員包括：

- [CreateItem](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) 方法，您可用來建立電子郵件訊息、工作或約會等新項目。

- <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> 屬性，您可用來存取在 Outlook 使用者介面 (UI) 中顯示資料夾內容的視窗。

- <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> 屬性，您可用來存取顯示單一項目內容的視窗，例如電子郵件訊息或會議邀請。

  若要取得物件的實例 <xref:Microsoft.Office.Interop.Outlook.Application> ，請在您的專案中使用類別的 [應用程式] 欄位 `ThisAddIn` 。 如需詳細資訊，請參閱 [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)。

> [!NOTE]
> 當您使用 Outlook 物件模型防護所封鎖的屬性和方法時，若要避免安全性警告，請從類別的 [應用程式] 欄位取得 Outlook 物件 `ThisAddIn` 。 如需詳細資訊，請參閱 [Office 方案的特定安全性考慮](../vsto/specific-security-considerations-for-office-solutions.md)。

### <a name="explorer-object"></a>Explorer 物件
 <xref:Microsoft.Office.Interop.Outlook.Explorer> 物件表示會顯示含有項目之資料夾內容的視窗，而這些項目包括電子郵件訊息、工作或約會。 <xref:Microsoft.Office.Interop.Outlook.Explorer> 物件含有一些方法和屬性，可讓您用來修改視窗，以及視窗變更時引發的事件。

 若要取得 <xref:Microsoft.Office.Interop.Outlook.Explorer> 物件，請進行下列其中一項動作：

- 使用 <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> 物件的 <xref:Microsoft.Office.Interop.Outlook.Application> 屬性來存取 Outlook 中的所有 <xref:Microsoft.Office.Interop.Outlook.Explorer> 物件。

- 使用 <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A> 物件的 <xref:Microsoft.Office.Interop.Outlook.Application> 方法來取得目前具有焦點的 <xref:Microsoft.Office.Interop.Outlook.Explorer> 。

- 使用 <xref:Microsoft.Office.Interop.Outlook.Folder> 物件的 `GetExplorer` 方法來取得目前資料夾的 <xref:Microsoft.Office.Interop.Outlook.Explorer>。

### <a name="inspector-object"></a>Inspector 物件
 <xref:Microsoft.Office.Interop.Outlook.Inspector> 物件是表示顯示單一項目的視窗，而這些項目包括電子郵件訊息、工作或約會。 <xref:Microsoft.Office.Interop.Outlook.Inspector> 物件含有一些方法和屬性，可讓您用來修改視窗，以及視窗變更時引發的事件。

 若要取得 <xref:Microsoft.Office.Interop.Outlook.Inspector> 物件，請進行下列其中一項動作：

- 使用 <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> 物件的 <xref:Microsoft.Office.Interop.Outlook.Application> 屬性來存取 Outlook 中的所有 <xref:Microsoft.Office.Interop.Outlook.Inspector> 物件。

- 使用 <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A> 物件的 <xref:Microsoft.Office.Interop.Outlook.Application> 方法來取得目前具有焦點的 <xref:Microsoft.Office.Interop.Outlook.Inspector> 。

- 使用特定項目 (例如 <xref:Microsoft.Office.Interop.Outlook.MailItem> 或 <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>) 的 `GetInspector` 方法來擷取與該項目相關聯的偵測器。

### <a name="folder-object"></a>Folder 物件
 <xref:Microsoft.Office.Interop.Outlook.Folder> 物件表示含有電子郵件訊息、連絡人、工作和其他項目的資料夾。 Outlook 會提供 16 個預設的 <xref:Microsoft.Office.Interop.Outlook.Folder> 物件。

 這些預設的 <xref:Microsoft.Office.Interop.Outlook.Folder> 物件是由 <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders> 列舉值所定義。 例如，

 OlDefaultFolders. olFolderInbox 對應至 Outlook 中的 [ **收件** 匣] 資料夾。

 如需示範如何存取預設 <xref:Microsoft.Office.Interop.Outlook.Folder> 並建立新的範例 <xref:Microsoft.Office.Interop.Outlook.Folder> ，請參閱 [如何：以程式設計方式建立自訂資料夾專案](../vsto/how-to-programmatically-create-custom-folder-items.md)。

### <a name="mailitem-object"></a>MailItem 物件
 <xref:Microsoft.Office.Interop.Outlook.MailItem> 物件表示電子郵件訊息。 <xref:Microsoft.Office.Interop.Outlook.MailItem> 物件通常是位於 [收件匣] 、[寄件備份] 和 [寄件匣] 這類資料夾中。 <xref:Microsoft.Office.Interop.Outlook.MailItem> 會公開可用來建立和傳送電子郵件訊息的屬性和方法。

 如需示範如何建立電子郵件訊息的範例，請參閱 [如何：以程式設計方式建立電子郵件專案](../vsto/how-to-programmatically-create-an-e-mail-item.md)。

### <a name="appointmentitem-object"></a>AppointmentItem 物件
 <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> 物件表示 [行事曆]  資料夾中的會議、一次性約會或是週期性約會或會議。 <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> 物件含有一些可執行回應或轉寄會議邀請等動作的方法，以及一些可指定地點和時間等會議細節的屬性。

 如需示範如何建立約會的範例，請參閱 [如何：以程式設計方式建立會議要求](../vsto/how-to-programmatically-create-a-meeting-request.md)。

### <a name="taskitem-object"></a>TaskItem 物件
 <xref:Microsoft.Office.Interop.Outlook.TaskItem> 物件表示要在指定的時間範圍內執行的工作。 <xref:Microsoft.Office.Interop.Outlook.TaskItem> 物件是位在 [工作]  資料夾中。

 若要建立工作，請使用 [物件的](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) CreateItem <xref:Microsoft.Office.Interop.Outlook.Application> 方法，並傳入 <xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem> 值做為參數。

### <a name="contactitem-object"></a>ContactItem 物件
 <xref:Microsoft.Office.Interop.Outlook.ContactItem>物件表示 [**連絡人**] 資料夾中的連絡人。 <xref:Microsoft.Office.Interop.Outlook.ContactItem> 物件含有它們所表示之人員的各種連絡資訊，例如街道地址、電子郵件地址和電話號碼。

 如需示範如何建立新連絡人的範例，請參閱 [如何：以程式設計方式將專案新增至 Outlook 連絡人](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)。 如需示範如何搜尋現有連絡人的範例，請參閱 [如何：以程式設計方式搜尋特定的連絡人](../vsto/how-to-programmatically-search-for-a-specific-contact.md)。

## <a name="use-the-outlook-object-model-documentation"></a><a name="refdoc"></a> 使用 Outlook 物件模型檔
 如需 Outlook 物件模型的完整資訊，您可以參閱 Outlook 主要 Interop 組件 (PIA) 參考和 VBA 物件模型參考。

### <a name="primary-interop-assembly-reference"></a>主要 interop 元件參考
 Outlook PIA 參考記載 Outlook 2010 主要 Interop 組件中的類型。 如需詳細資訊，請參閱 [Outlook 2010 主要 interop 元件參考](/previous-versions/office/developer/office-2010/bb652780(v=office.14))。

 這份文件除了提供 PIA 中所有類型的資訊以外，還提供其他有關 PIA 結構的資訊以及常見 Outlook 自動化工作的程式碼範例。

### <a name="vba-object-model-reference"></a>VBA 物件模型參考
 VBA 物件模型參考記載 Outlook 物件模型公開給 Visual Basic for Application (VBA) 程式碼時的資訊。 如需詳細資訊，請參閱 [Outlook 2010 物件模型參考](/office/vba/api/overview/Outlook/object-model)。

 VBA 物件模型參考中的所有物件和成員都會對應至 Outlook PIA 中的類型和成員。 例如，VBA 物件模型參考中的偵測器物件會對應至 <xref:Microsoft.Office.Interop.Outlook.Inspector> OUTLOOK PIA 中的物件。 雖然 VBA 物件模型參考會提供大部分屬性、方法和事件的程式碼範例，但如果您想要在以 Visual Studio 建立的 Outlook VSTO 增益集專案中使用這些程式碼範例，您必須將此參考中的 VBA 程式碼改成 Visual Basic 或 Visual C# 程式碼。

### <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[使用連絡人項目](../vsto/working-with-contact-items.md)|所提供的主題示範如何使用連絡人執行工作。|
|[使用訊息項目](../vsto/working-with-mail-items.md)|所提供的主題示範如何使用郵件項目執行工作。|
|[使用資料夾](../vsto/working-with-folders.md)|所提供的主題示範如何使用資料夾執行工作。|
|[使用行事曆專案](../vsto/working-with-calendar-items.md)|所提供的主題示範如何使用行事曆項目執行工作。|
|[如何：以程式設計方式判斷目前的 Outlook 專案](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|示範如何顯示目前資料夾的名稱以及已選取項目的某些相關資訊。|
