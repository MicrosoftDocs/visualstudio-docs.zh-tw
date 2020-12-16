---
title: 程式 VSTO 增益集
description: 瞭解如何使用 ThisAddIn 類別來執行工作，例如存取 Microsoft Office 主應用程式的物件模型。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Addin
- VST.ProjectItem.AddinProject
- thisAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- add-ins [Office development in Visual Studio], programming
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], application-level add-ins
- programming [Office development in Visual Studio], application-level add-ins
- ThisAddIn class
- user interfaces [Office development in Visual Studio], customizing
- writing code for Office solutions
- host items [Office development in Visual Studio], AddIn
- application development [Office development in Visual Studio], application-level add-ins
- add-ins [Office development in Visual Studio], ThisAddIn class
- application-level add-ins [Office development in Visual Studio], ThisAddIn class
- FormRegionStartup interface
- ThisAddIn_Startup
- application-level add-ins [Office development in Visual Studio], programming
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7c3a4b14a1935d1d276f0884234fcd121b838f39
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525116"
---
# <a name="program-vsto-add-ins"></a>程式 VSTO 增益集
  當您建立 VSTO 增益集來擴充 Microsoft Office 應用程式時，會直接針對專案中的 `ThisAddIn` 類別撰寫程式碼。 您可以使用這個類別來執行工作，例如存取 Microsoft Office 主應用程式的物件模型、自訂應用程式的使用者介面 (UI)，以及將 VSTO 增益集中的物件公開給其他 Office 解決方案。

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 撰寫 VSTO 增益集專案中的程式碼，在某些方面不同於撰寫 Visual Studio 中其他類型專案的程式碼。 其中有許多差異的原因來自於將 Office 物件模型公開給 Managed 程式碼的方式。 如需詳細資訊，請參閱 [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)。

 如需 VSTO 增益集和其他類型方案的一般資訊，您可以使用 Visual Studio 中的 Office 開發工具來建立，請參閱 [office 方案開發總覽 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)。

## <a name="use-the-thisaddin-class"></a>使用 ThisAddIn 類別
 您可以在 `ThisAddIn` 類別中開始撰寫 VSTO 增益集程式碼。 Visual Studio 會在 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] VSTO 增益集專案中，于 c # ) 程式碼檔案 (的) 或 *ThisAddIn.cs* (中，自動產生此類別。 當 Microsoft Office 應用程式載入您的 VSTO 增益集時， [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會自動為您具現化這個類別。

 `ThisAddIn` 類別有兩個預設事件處理常式。 若要在載入 VSTO 增益集時執行程式碼，請將程式碼加入 `ThisAddIn_Startup` 事件處理常式中。 若要在卸載 VSTO 增益集之前執行程式碼，請將程式碼加入 `ThisAddIn_Shutdown` 事件處理常式。 如需這些事件處理常式的詳細資訊，請參閱 [Office 專案中的事件](../vsto/events-in-office-projects.md)。

> [!NOTE]
> 在 Outlook 中，當卸載 VSTO 增益集時，預設不一定會呼叫 `ThisAddIn_Shutdown` 事件處理常式。 如需詳細資訊，請參閱 [Office 專案中的事件](../vsto/events-in-office-projects.md)。

### <a name="access-the-object-model-of-the-host-application"></a>存取主應用程式的物件模型
 若要存取主應用程式的物件模型，請使用 `Application` 類別的 `ThisAddIn` 欄位。 這個欄位會傳回代表主應用程式之目前執行個體的物件。 下表列出每個 VSTO 增益集專案中 `Application` 欄位的傳回值類型。

|主應用程式|傳回值類型|
|----------------------|-----------------------|
|Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|
|Microsoft Office InfoPath|<xref:Microsoft.Office.Interop.InfoPath.Application>|
|Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|
|Microsoft Office PowerPoint|[應用程式](/previous-versions/office/developer/office-2010/ff764034(v=office.14))|
|Microsoft Office Project|Microsoft.Office.Interop.MSProject.Application|
|Microsoft Office Visio|Microsoft.Office.Interop.Visio.Application|
|Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|

 下列程式碼範例示範如何使用 `Application` 欄位，在適用于 Microsoft Office Excel 的 VSTO 增益集中建立新的活頁簿。 這個範例適合從 `ThisAddIn` 類別執行。

```vb
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);
```

 若要從 `ThisAddIn` 類別外執行相同的動作，請使用 `Globals` 物件存取 `ThisAddIn` 類別。 如需物件的詳細資訊 `Globals` ，請參閱 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)。

```vb
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);
```

 如需特定的 Microsoft Office 應用程式之物件模型的詳細資訊，請參閱下列主題：

- [Excel 物件模型總覽](../vsto/excel-object-model-overview.md)

- [Word 物件模型總覽](../vsto/word-object-model-overview.md)

- [Outlook 物件模型總覽](../vsto/outlook-object-model-overview.md)

- [InfoPath 解決方案](../vsto/infopath-solutions.md)

- [PowerPoint 方案](../vsto/powerpoint-solutions.md)

- [專案解決方案](../vsto/project-solutions.md)

- [Visio 物件模型總覽](../vsto/visio-object-model-overview.md)

### <a name="access-a-document-when-the-office-application-starts"></a><a name="AccessingDocuments"></a> 在 Office 應用程式啟動時存取檔
 當您啟動 [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] 應用程式時，並非所有應用程式都會自動開啟文件；而當您啟動 [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 應用程式時，所有應用程式都不會開啟文件。 因此， `ThisAdd-In_Startup` 如果程式碼需要開啟檔，就不會在事件處理常式中加入程式碼。 相反地，請將程式碼加入 Office 應用程式在使用者建立或開啟文件時所引發的事件。 如此可確保程式碼對文件執行作業之前，該文件已處於開啟狀態。

 下列程式碼範例只有在使用者建立文件或開啟現有文件時，才適用於 Word 文件。

 [!code-csharp[Trin_WordAddIn_Menus#3](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#3)]

### <a name="thisaddin-members-to-use-for-other-tasks"></a>要用於其他工作的 ThisAddIn 成員
 下表說明其他常見工作，並顯示可以用來執行這些工作的 `ThisAddIn` 類別。

|工作|要使用的成員|
|----------|-------------------|
|載入 VSTO 增益集時，執行程式碼以初始化 VSTO 增益集。|將程式碼加入 `ThisAddIn_Startup` 方法。 這是 <xref:Microsoft.Office.Tools.AddInBase.Startup> 事件的預設事件處理常式。 如需詳細資訊，請參閱 [Office 專案中的事件](../vsto/events-in-office-projects.md)。|
|卸載 VSTO 增益集之前，執行程式碼以清除 VSTO 增益集所使用的資源。|將程式碼加入 `ThisAddIn_Shutdown` 方法。 這是 <xref:Microsoft.Office.Tools.AddInBase.Shutdown> 事件的預設事件處理常式。 如需詳細資訊，請參閱 [Office 專案中的事件](../vsto/events-in-office-projects.md)。 **注意：**  在 Outlook 中， `ThisAddIn_Shutdown` 當 VSTO 增益集卸載時，預設不一定會呼叫事件處理常式。 如需詳細資訊，請參閱 [Office 專案中的事件](../vsto/events-in-office-projects.md)。|
|顯示自訂工作窗格。|使用 `CustomTaskPanes` 欄位。 如需詳細資訊，請參閱 [自訂工作窗格](../vsto/custom-task-panes.md)。|
|將 VSTO 增益集中的物件公開給其他 Microsoft Office 方案。|覆寫 <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> 方法。 如需詳細資訊，請參閱 [從其他 Office 方案呼叫 VSTO 增益集](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)的程式碼。|
|實作擴充性介面來自訂 Microsoft Office system 中的功能。|覆寫 <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> 方法以傳回實作介面的類別執行個體。 如需詳細資訊，請參閱使用擴充性 [介面自訂 UI 功能](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)。 **注意：**  若要自訂功能區 UI，您也可以覆寫 <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> 方法。|

### <a name="understand-the-design-of-the-thisaddin-class"></a>瞭解 ThisAddIn 類別的設計
 在以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]為目標的專案中， <xref:Microsoft.Office.Tools.AddIn> 是一種介面。 `ThisAddIn` 類別衍生自 <xref:Microsoft.Office.Tools.AddInBase> 類別。 這個基底類別會將其成員的所有呼叫重新導向至 <xref:Microsoft.Office.Tools.AddIn> 中 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]介面的內部實作。

 在 Outlook VSTO 增益集專案中，`ThisAddIn` 類別是衍生自以 .NET Framework 3.5 為目標之專案中的 `Microsoft.Office.Tools.Outlook.OutlookAddIn` 類別，以及以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 為目標之專案中的 <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase>。 這些基底類別提供了一些額外的功能來支援表單區域。 如需表單區域的詳細資訊，請參閱 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)。

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>自訂 Microsoft Office 應用程式的使用者介面
 您可以使用 VSTO 增益集，以程式設計方式自訂 Microsoft Office 應用程式的 UI。 例如，您可以自訂功能區、顯示自訂工作窗格，或建立 Outlook 的自訂表單區域。 如需詳細資訊，請參閱 [OFFICE UI 自訂](../vsto/office-ui-customization.md)。

 Visual Studio 提供可用來建立自訂工作窗格、功能區自訂和 Outlook 表單區域的設計工具和類別。 這些設計工具和類別有助於簡化自訂這些功能的程序。 如需詳細資訊，請參閱 [自訂工作窗格](../vsto/custom-task-panes.md)、 [功能區設計](../vsto/ribbon-designer.md)工具和 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)。

 如果您想要使用類別和設計工具不支援的方式，來自訂上述其中一項功能，您也可以透過在 VSTO 增益集中實作 *「擴充性介面」* (Extensibility Interface)，來自訂這些功能。 如需詳細資訊，請參閱使用擴充性 [介面自訂 UI 功能](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)。

 此外，您也可以藉由產生可擴充文件和活頁簿行為的主項目，來修改 Word 文件和 Excel 活頁簿的 UI。 這可讓您將 Managed 控制項加入文件和工作表。 如需詳細資訊，請參閱 [在 VSTO 增益集中，于執行時間擴充 Word 檔和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。

## <a name="call-code-in-vsto-add-ins-from-other-solutions"></a>從其他方案呼叫 VSTO 增益集的程式碼
 您可以將 VSTO 增益集中的物件公開給其他方案 (包括其他 Office 方案)。 如果您想要讓其他方案也能使用 VSTO 增益集提供的服務，這就很有用。 例如，如果您有 Microsoft Office Excel 的 VSTO 增益集，該增益集會在 web 服務的財務資料上執行計算，則其他方案可以在執行時間呼叫 Excel VSTO 增益集來執行這些計算。

 如需詳細資訊，請參閱 [從其他 Office 方案呼叫 VSTO 增益集](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)的程式碼。

## <a name="see-also"></a>另請參閱
- [開發 Office 方案](../vsto/developing-office-solutions.md)
- [在 VSTO 增益集的執行時間中擴充 Word 檔和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [從其他 Office 方案呼叫 VSTO 增益集的程式碼](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [逐步解說：從 VBA 呼叫 VSTO 增益集中的程式碼](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [使用擴充性介面自訂 UI 功能](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
- [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)
- [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)
