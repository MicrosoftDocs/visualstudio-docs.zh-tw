---
title: 使用擴充性介面自訂 UI 功能
description: 瞭解 Visual Studio 中的 Office 開發工具提供可協助您自訂 UI 功能的擴充性介面。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], customizing
- application-level add-ins [Office development in Visual Studio], extensibility interfaces
- customizing UI features [Office development in Visual Studio]
- FormRegionStartup interface
- add-ins [Office development in Visual Studio], extensibility interfaces
- extensibility interfaces [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f84a694c9a18b6ec1c64204c8150ff721633278d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962466"
---
# <a name="customize-ui-features-by-using-extensibility-interfaces"></a>使用擴充性介面自訂 UI 功能
  當您使用 Visual Studio 中的 Office 開發工具，在 VSTO 增益集中建立自訂工作窗格、功能區自訂和 Outlook 表單區域時，這些工具提供可處理許多實作詳細資料的類別和設計工具。 不過，如果您有特殊需求，也可以針對每項功能自行實作 *「擴充性介面」* (Extensibility Interface)。

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="overview-of-extensibility-interfaces"></a>擴充性介面的總覽
 Microsoft Office 定義一組 COM VSTO 增益集可實作以自訂特定功能 (例如功能區) 的擴充性介面。 這些介面提供可存取功能的完整控制權。 然而，您需要對 Managed 程式碼中的 COM 互通性有些了解，才能實作這些介面。 在某些情況下，這些介面的程式撰寫模型對熟悉 .NET Framework 的開發人員而言，也不是那麼直接易懂。

 當您使用 Visual Studio 中的 Office 專案範本建立 VSTO 增益集時，您不需要實作擴充性介面來自訂功能區等功能。 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會為您實作這些介面。 相反地，您可以使用 Visual Studio 所提供之更直覺的類別和設計工具。 不過，如果需要，您仍可直接在 VSTO 增益集中實作擴充性介面。

 如需 Visual Studio 針對這些功能所提供之類別和設計工具的詳細資訊，請參閱 [自訂工作窗格](../vsto/custom-task-panes.md)、 [功能區設計](../vsto/ribbon-designer.md)工具和 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)。

## <a name="extensibility-interfaces-you-can-implement-in-a-vsto-add-in"></a>您可以在 VSTO 增益集中執行的擴充性介面
 下表列出您可以實作的擴充性介面，以及支援這些介面的應用程式。

|介面|描述|應用程式|
|---------------|-----------------|------------------|
|<xref:Microsoft.Office.Core.IRibbonExtensibility>|實作這個介面可自訂功能區 UI。 **注意：**  您可以將 **功能區 (XML)** 專案加入至專案，以在 VSTO 增益集中產生預設的 <xref:Microsoft.Office.Core.IRibbonExtensibility> 實值。 如需詳細資訊，請參閱 [Ribbon XML](../vsto/ribbon-xml.md)。|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> InfoPath 2010<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Visio<br /><br /> Word|
|<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>|實作這個介面可建立自訂工作窗格。|Excel<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|
|<xref:Microsoft.Office.Interop.Outlook.FormRegionStartup>|實作這個介面可建立 Outlook 表單區域。|Outlook|

 Microsoft Office 還定義其他幾個擴充性介面，例如 <xref:Microsoft.Office.Core.IBlogExtensibility>、 <xref:Microsoft.Office.Core.EncryptionProvider>和 <xref:Microsoft.Office.Core.SignatureProvider>。 Visual Studio 不支援在使用 Office 專案範本建立的 VSTO 增益集中實作這些介面。

## <a name="use-extensibility-interfaces"></a>使用擴充性介面
 若要使用擴充性介面自訂 UI 功能，請在您的 VSTO 增益集專案中實作適當的介面。 然後，覆寫 <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> 方法以傳回實作介面的類別執行個體。

 如需示範如何 <xref:Microsoft.Office.Core.IRibbonExtensibility> 在 OUTLOOK VSTO 增益集中執行、和介面的範例應用程式 <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> <xref:Microsoft.Office.Interop.Outlook.FormRegionStartup> ，請參閱 [Office 程式開發範例](../vsto/office-development-samples.md)中的 UI 管理員範例。

### <a name="example-of-implementing-an-extensibility-interface"></a>執行擴充性介面的範例
 下列程式碼範例示範 <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> 介面的簡單實作，以建立自訂工作窗格。 這個範例會定義兩個類別：

- `TaskPaneHelper` 類別實作 <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> ，以建立及顯示自訂工作窗格。

- `TaskPaneUI` 類別提供工作窗格的 UI。 `TaskPaneUI` 類別的屬性讓 COM 可以看見該類別，進而讓 Microsoft Office 應用程式可以探索該類別。 在這個範例中，UI 是空的 <xref:System.Windows.Forms.UserControl>，但是您可以透過修改程式碼來加入控制項。

  > [!NOTE]
  > 若要將 `TaskPaneUI` 類別公開至 COM，您也必須設定專案的 [註冊 COM Interop]  屬性。

  [!code-vb[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#1)]
  [!code-csharp[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#1)]

  如需有關如何執行的詳細資訊 <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> ，請參閱 Microsoft Office 檔中的在 [2007 Office 系統中建立自訂工作窗格](/previous-versions/office/developer/office-2007/aa338197(v=office.12)) 。

### <a name="example-of-overriding-the-requestservice-method"></a>覆寫 RequestService 方法的範例
 下列程式碼範例示範如何覆寫 <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> 方法，以從先前的程式碼範例傳回 `TaskPaneHelper` 類別的執行個體。 它會檢查 *serviceGuid* 參數的值以判斷所要求的介面，然後傳回實作該介面的物件。

 [!code-vb[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#2)]
 [!code-csharp[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#2)]

## <a name="see-also"></a>另請參閱
- [Office 開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)
- [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)
- [開發 Office 方案](../vsto/developing-office-solutions.md)
- [從其他 Office 方案呼叫 VSTO 增益集的程式碼](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)
