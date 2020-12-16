---
title: 將已遷移的 Excel 或 Word 專案更新為 .NET Framework 4。5
description: 當您擁有使用特定功能的 Excel 或 Word 專案時，如果目標 framework 變更為 .NET Framework 4 或更新版本，您就必須修改程式碼。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7bc79a53b62cf9fb0ca0ba533a2ce0d542b08c72
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528425"
---
# <a name="update-excel-and-word-projects-that-you-migrate-to-the-net-framework-45"></a>更新您遷移至 .NET Framework 4.5 的 Excel 和 Word 專案
  如果您有使用下列任何功能的 Excel 或 Word 專案，當目標 Framework 變更為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本時，即必須修改程式碼：

- [GetVstoObject 和 HasVstoObject 方法](#GetVstoObject)

- [文件層級專案中之產生的類別](#generatedclasses)

- [文件上的 Windows Form 控制項](#winforms)

- [Word 內容控制項事件](#ccevents)

- [OLEObject 和 OLEControl 類別](#ole)

- [Controls.Item(Object) 屬性](#itemproperty)

- [衍生自 CollectionBase 的集合](#collections)

  您也必須 `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` 從目標為或更新版本的 Excel 專案中，移除類別的和參考 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 。 Visual Studio 不會為您移除此屬性或類別參考。

## <a name="remove-the-excellocale1033-attribute-from-excel-projects"></a>從 Excel 專案中移除 ExcelLocale1033 屬性
 已 `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` 從適用于 Office 執行時間的 Visual Studio 2010 工具部分移除，以用於以或更新版本為目標的方案 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 。 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 和更新版本中的 Common Language Runtime (CLR) 會一律將地區設定 ID 1033 傳遞給 Excel 物件模型，而您也無法再使用這個屬性停用此行為。 如需詳細資訊，請參閱 [Excel 方案的全球化與當地語系化](../vsto/globalization-and-localization-of-excel-solutions.md)。

### <a name="to-remove-the-excellocale1033attribute"></a>移除 ExcelLocale1033Attribute

1. 請使用在 Visual Studio 中開啟的專案，開啟 [方案總管] 。

2. 在 [屬性]  節點 (C#) 或 [我的專案]  節點 (Visual Basic) 下，按兩下 AssemblyInfo 程式碼檔，以在程式碼編輯器中加以開啟。

    > [!NOTE]
    > 在 Visual Basic 專案中，您必須按一下 [方案總管]  中的 [顯示所有檔案]  按鈕，才能查看 AssemblyInfo 程式碼檔。

3. 找出 `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute`，並將它從檔案移除或加上註解。

    ```vb
    <Assembly: ExcelLocale1033Proxy(True)>
    ```

    ```csharp
    [assembly: ExcelLocale1033Proxy(true)]
    ```

## <a name="remove-a-reference-to-the-excellocal1033proxy-class"></a>移除 ExcelLocal1033Proxy 類別的參考
 使用 Microsoft Visual Studio 2005 Tools for Microsoft Office System 所建立的專案，使用 `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` 類別具現化 Excel <xref:Microsoft.Office.Interop.Excel.Application> 物件。 此類別已從適用于 Office 執行時間的 Visual Studio 2010 工具部分中移除，以用於以或更新版本為目標的方案 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 。 因此，您必須移除或註解化參考此類別的程式碼行。

### <a name="to-remove-the-reference-to-the-excellocal1033proxy-class"></a>移除 ExcelLocal1033Proxy 類別的參考

1. 請在 Visual Studio 中開啟專案，再開啟 [方案總管] 。

2. 在 **方案總管** 中，開啟 c # ) 的 *ThisAddin.cs* (的快捷方式功能表，或針對 Visual Basic) 開啟 [ *ThisAddin* ] (，然後選擇 [ **視圖程式碼**]。

3. 在程式碼編輯器的 `VSTO generated code` 區域中，移除或註解化下列程式碼行。

    ```vb
    Me.Application = CType(Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(GetType(Excel.Application), Me.Application), Excel.Application)

    ```

    ```csharp
    this.Application = (Excel.Application)Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(typeof(Excel.Application), this.Application);

    ```

## <a name="update-code-that-uses-the-getvstoobject-and-hasvstoobject-methods"></a><a name="GetVstoObject"></a> 更新使用 GetVstoObject 和 HasVstoObject 方法的程式碼
 在以 .NET Framework 3.5 為目標的專案中，`GetVstoObject` 或 `HasVstoObject` 方法在專案下列其中一個原生物件上可用為擴充方法：<xref:Microsoft.Office.Interop.Word.Document>、<xref:Microsoft.Office.Interop.Excel.Workbook>、<xref:Microsoft.Office.Interop.Excel.Worksheet> 或 <xref:Microsoft.Office.Interop.Excel.ListObject>。 當您呼叫這些方法時，不需要傳遞參數。 下列程式碼範例示範如何在以 .NET Framework 3.5 為目標的 Word VSTO 增益集中使用 GetVstoObject 方法。

```vb
Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject()
```

```csharp
Microsoft.Office.Tools.Word.Document vstoDocument =
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject();
```

 在以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標的專案中，您必須修改程式碼，以下列方式之一存取這些方法：

- 您仍然可以在後列物件上存取這些方法當成擴充方法： <xref:Microsoft.Office.Interop.Word.Document>、 <xref:Microsoft.Office.Interop.Excel.Workbook>、 <xref:Microsoft.Office.Interop.Excel.Worksheet>或 <xref:Microsoft.Office.Interop.Excel.ListObject> 物件。 不過，您現在必須將 `Globals.Factory` 屬性傳回的物件傳遞給這些方法。

  ```vb
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory)
  ```

  ```csharp
  Microsoft.Office.Tools.Word.Document vstoDocument =
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory);
  ```

- 或者，您可以存取位於 `Globals.Factory` 屬性傳回之物件上的這些方法。 當您以這種方式存取這些方法時，您必須將想要擴充的原生物件傳遞給方法。

  ```vb
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument)
  ```

  ```csharp
  Microsoft.Office.Tools.Word.Document vstoDocument =
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument);
  ```

  如需詳細資訊，請參閱 [在 VSTO 增益集中，于執行時間擴充 Word 檔和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。

## <a name="update-code-that-uses-instances-of-the-generated-classes-in-document-level-projects"></a><a name="generatedclasses"></a> 在檔層級專案中更新使用產生的類別實例的程式碼
 在以 .NET Framework 3.5 為目標的文件層級專案中，專案中的產生的類別衍生自 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]的下列類別：

- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.Document>

- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.Workbook>

- `Sheet`*n*：<xref:Microsoft.Office.Tools.Excel.Worksheet>

- `Chart`*n*：<xref:Microsoft.Office.Tools.Excel.ChartSheet>

  在以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標的專案中，上文列出的 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 類型是介面，而不是類別。 以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標的專案中之產生的類別，衍生自 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]的下列新類別：

- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>

- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>

- `Sheet`*n*：<xref:Microsoft.Office.Tools.Excel.WorksheetBase>

- `Chart`*n*：<xref:Microsoft.Office.Tools.Excel.ChartSheetBase>

  如果專案中的程式碼將參考的其中一個產生的類別執行個體，視為其衍生來源的基底類別，您必須修改程式碼。

  例如，在以 .NET Framework 3.5 為目標的 Excel 活頁簿專案中，您可能有個 helper 方法，會對專案中之產生的 `Sheet`*n* 類別執行個體執行一些工作。

```vb
Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.Worksheet)
    ' Do something to the worksheet object.
End Sub
```

```csharp
private void DoSomethingToSheet(Microsoft.Office.Tools.Excel.Worksheet worksheet)
{
    // Do something to the worksheet object.
}
```

 如果專案重定目標為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本，您必須對程式碼進行下列一種變更：

- 修改專案中呼叫 `DoSomethingToSheet` 方法以傳遞 <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Base%2A> 物件之 <xref:Microsoft.Office.Tools.Excel.WorksheetBase> 屬性的所有程式碼。 這個屬性會傳回 <xref:Microsoft.Office.Tools.Excel.Worksheet> 物件。

    ```vb
    DoSomethingToSheet(Globals.Sheet1.Base)
    ```

    ```csharp
    DoSomethingToSheet(Globals.Sheet1.Base);
    ```

- 修改 `DoSomethingToSheet` 方法參數，預期會改為 <xref:Microsoft.Office.Tools.Excel.WorksheetBase> 物件。

    ```vb
    Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.WorksheetBase)
        ' Do something to the worksheet object.
    End Sub
    ```

    ```csharp
    private void DoSomethingToSheet (Microsoft.Office.Tools.Excel.WorksheetBase worksheet)
    {
        // Do something to the worksheet object.
    }
    ```

## <a name="update-code-that-uses-windows-forms-controls-on-documents"></a><a name="winforms"></a> 更新在檔上使用 Windows Forms 控制項的程式碼
 您必須 **使用** (c # ) 或將或命名空間的 (Visual Basic) 語句，匯 **入** <xref:Microsoft.Office.Tools.Excel> <xref:Microsoft.Office.Tools.Word> 至任何使用 Controls 屬性的程式碼檔案頂端，以程式設計方式將 Windows Forms 控制項加入檔或工作表。

 在以 .NET Framework 3.5 為目標的專案中，加入 Windows Form 控制項的方法(例如 `AddButton` 方法)，都是在 <xref:Microsoft.Office.Tools.Excel.ControlCollection> 和 <xref:Microsoft.Office.Tools.Word.ControlCollection> 類別中所定義。

 在以或更新版本為目標的專案中 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ，這些方法是可在 [控制項] 屬性上使用的擴充方法。 若要使用這些擴充方法，方法使用所在的程式碼檔中必須有 **N:Microsoft.Office.Tools.Excel** 或 **N:Microsoft.Office.Tools.Word** 命名空間的 <xref:Microsoft.Office.Tools.Excel> 或 <xref:Microsoft.Office.Tools.Word> 陳述式。 以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標的新專案中，會自動產生這個陳述式。 不過，以 .NET Framework 3.5 為目標的專案不會自動加入這個陳述式，所以您必須在重定專案目標時將其加入。

 如需詳細資訊，請參閱 [在執行時間將控制項加入 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)。

## <a name="update-code-that-handles-word-content-control-events"></a><a name="ccevents"></a> 更新處理 Word 內容控制項事件的程式碼
 在以 .NET Framework 3.5 為目標的專案中，Word 內容控制項的事件是由泛型 <xref:System.EventHandler%601> 委派所處理。 在以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標的專案中，這些事件是由其他委派處理。

 下表列出在以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標的專案中，與它們相關聯的 Word 內容控制項事件和委派。

|事件|在 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 及更新版本的專案中要使用的委派|
|-----------| - |
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>|<xref:Microsoft.Office.Tools.Word.ContentControlAddedEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlContentUpdatingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>|<xref:Microsoft.Office.Tools.Word.ContentControlDeletingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>|<xref:Microsoft.Office.Tools.Word.ContentControlEnteringEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>|<xref:Microsoft.Office.Tools.Word.ContentControlExitingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlStoreUpdatingEventHandler>|

## <a name="update-code-that-uses-the-oleobject-and-olecontrol-classes"></a><a name="ole"></a> 更新使用 OLEObject 和 OLEControl 類別的程式碼
 在以 .NET Framework 3.5 為目標的專案中，您可以使用 `Microsoft.Office.Tools.Excel.OLEObject` 和 `Microsoft.Office.Tools.Word.OLEControl` 類別，將自訂控制項 (例如 Windows Form 使用者控制項) 加入文件或工作表。

 在以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標的專案中， <xref:Microsoft.Office.Tools.Excel.ControlSite> 和 <xref:Microsoft.Office.Tools.Word.ControlSite> 介面已取代這些類別。 您必須修改原參考 `Microsoft.Office.Tools.Excel.OLEObject` 和 `Microsoft.Office.Tools.Word.OLEControl` 的程式碼，改為參考 <xref:Microsoft.Office.Tools.Excel.ControlSite> 和 <xref:Microsoft.Office.Tools.Word.ControlSite>。 除了新名稱以外，這些控制項的行為方式和它們在以 .NET Framework 3.5 為目標的專案中一樣。

 如需詳細資訊，請參閱 [在執行時間將控制項加入 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)。

## <a name="update-code-that-uses-the-controlsitemobject-property"></a><a name="itemproperty"></a> 更新使用 Controls (物件) 屬性的程式碼
 在以 .NET Framework 3.5 為目標的專案中，您可以使用 Microsoft.Office.Tools.Word.Doc>ument 的專案 (物件) 屬性。 `Microsoft.Office.Tools.Excel.Worksheet.Controls` 用來判斷檔或工作表是否有指定控制項的控制項或集合。

 在以或更新版本為目標的專案中 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ，已從這些集合中移除 (物件) 屬性的專案。 若要判斷檔或工作表是否包含指定的控制項，請 <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> 改用或集合的 contains (system.object) 方法 <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> 。

 如需檔和工作表之控制項集合的詳細資訊，請參閱 [在執行時間將控制項加入 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)。

## <a name="update-code-that-uses-collections-that-derive-from-collectionbase"></a><a name="collections"></a> 更新程式碼，以使用衍生自 CollectionBase 的集合
 在以 .NET Framework 3.5 為目標的專案中，中的數個集合類型 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 衍生自 <xref:System.Collections.CollectionBase> 類別，例如 `Microsoft.Office.Tools.SmartTagCollection` 、 `Microsoft.Office.Tools.Excel.ControlCollection` 和 `Microsoft.Office.Tools.Word.ControlCollection` 。

 在以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標的專案中，這些集合類型現在是非衍生自 <xref:System.Collections.CollectionBase>的介面。 這些集合類型也不再提供某些成員，例如 <xref:System.Collections.CollectionBase.Capacity%2A>、 <xref:System.Collections.CollectionBase.List%2A>和 <xref:System.Collections.CollectionBase.InnerList%2A>。

## <a name="see-also"></a>另請參閱
- [將 Office 方案遷移至 .NET Framework 4 或更新版本](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [內容控制項](../vsto/content-controls.md)
- [在 VSTO 增益集的執行時間中擴充 Word 檔和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [在執行時間將控制項新增至 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)
