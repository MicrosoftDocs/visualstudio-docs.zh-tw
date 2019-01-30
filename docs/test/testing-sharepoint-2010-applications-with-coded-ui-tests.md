---
title: 使用自動程式化 UI 測試來測試 SharePoint 應用程式
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: a4b79531948310d0f2628b6ade334d6ea9df35ca
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946007"
---
# <a name="test-sharepoint-applications-with-coded-ui-tests"></a>使用自動程式化 UI 測試來測試 SharePoint 應用程式

在 SharePoint 應用程式中包含自動程式碼 UI 測試，可讓您驗證整個應用程式 (包括其 UI 控制項) 是否正常運作。 自動程式碼 UI 測試也可以驗證使用者介面中的值和邏輯。

若要深入了解使用自動程式化 UI 測試的優點，請參閱[使用 UI 自動化來測試您的程式碼](../test/use-ui-automation-to-test-your-code.md)。

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**需求**

- Visual Studio 企業版

## <a name="create-a-coded-ui-test-for-a-sharepoint-app"></a>建立 SharePoint 應用程式的自動程式化 UI 測試

為您的 SharePoint 應用程式[建立自動程式化 UI 測試](../test/use-ui-automation-to-test-your-code.md)的方式，與為其他類型應用程式建立測試的方式相同。 所有控制項都可在 [Web 編輯] 介面上錄製和播放。 選取分類和 Web 組件的介面都是標準的 Web 控制項。

![SharePoint 網頁組件](../test/media/cuit_sharepoint.png)

> [!NOTE]
> 如果您正在錄製動作，請在產生程式碼之前驗證動作。 由於有多個行為與滑鼠停留建立關聯，因此它預設為開啟狀態。 從您的自動程式碼 UI 測試中移除多餘的停留動作時務必小心。 您可以編輯用於測試的程式碼來進行這項作業，或是使用 [自動程式碼 UI 測試編輯器](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)。

## <a name="test-office-controls-within-a-sharepoint-app"></a>測試 SharePoint 應用程式中的 Office 控制項

若要在 SharePoint 應用程式中啟用某些 Office Web 組件的自動化，則必須稍微修改程式碼。

> [!NOTE]
> SharePoint 應用程式中不支援測試 Visio 和 PowerPoint 控制項。

### <a name="excel-cell-controls"></a>Excel 儲存格控制項

若要包括 Excel 儲存格控制項，您必須在自動程式化 UI 測試的程式碼中進行一些變更。

> [!WARNING]
> 若在任何 Excel 儲存格中輸入文字，後面接著方向鍵動作，則這類動作無法正確錄製。 使用滑鼠選取儲存格。

如果您錄製空儲存格上的動作，則必須按兩下儲存格然後執行一組文字作業，藉此修改程式碼。 由於在儲存格中按一下，然後接著任何鍵盤動作都會啟動儲存格內的 `textarea`，因此必須這樣做。 僅錄製空儲存格上的 `setvalue` 會搜尋 `editbox` ，但是在按下儲存格之前它並不存在。 例如：

```csharp
Mouse.DoubliClick(uiItemCell,new Point(31,14));
uiGridKeyboardInputEdit.Text=value;
```

如果您在非空白儲存格上錄製動作，則錄製過程會變得較複雜，因為您將文字加入至儲存格時，會加入一個新的 \<div> 控制項做為儲存格的子系。 新的 \<div> 控制項會包含您剛輸入的文字。 錄製器需要錄製新 \<div> 控制項上的動作，但是卻無法錄製，因為在輸入測試之前，新的 \<div> 控制項並不存在。 您必須手動進行下列程式碼變更，才能解決這個問題。

1. 移至儲存格初始化，並將 `RowIndex` 和 `ColumnIndex` 設為主要屬性：

    ```csharp
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";
    ```

2. 搜尋儲存格的 `HtmlDiv` 子系：

    ```csharp
    private UITestControl getControlToDoubleClick(HtmlCell cell)
    {
         if (String.IsNullOrEmpty(cell.InnerText)) return cell;
         HtmlDiv pane = new HtmlDiv(cell);
         pane.FilterProperties[HtmlDiv.PropertyNames.InnerText] = cell.InnerText;
         // Class is an important property in finding pane
         pane.FilterProperties[HtmlDiv.PropertyNames.Class] = "cv-nwr";
         UITestControlCollection panes = pane.FindMatchingControls();
         return panes[0];
    }
    ```

3. 在 `HtmlDiv`上加入滑鼠按兩下動作的程式碼：

    ```csharp
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )
    ```

4. 加入程式碼設定 `TextArea`上的文字：

    ```csharp
    uIGridKeyboardInputEdit.Text = value; }
    ``

## See also

- [Use UI automation to test your code](../test/use-ui-automation-to-test-your-code.md)
- [Create SharePoint solutions](../sharepoint/create-sharepoint-solutions.md)
- [Verify and debug SharePoint code](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [Build and debug SharePoint solutions](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Profile the performance of SharePoint applications](../sharepoint/profiling-the-performance-of-sharepoint-applications.md)
