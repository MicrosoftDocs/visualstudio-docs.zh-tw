---
title: "使用自動程式化 UI 測試來測試 SharePoint 2010 應用程式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: fbda836ec423d9a86b51b2334a3015589512d816
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2018
---
# <a name="testing-sharepoint-2010-applications-with-coded-ui-tests"></a>使用自動程式化 UI 測試來測試 SharePoint 2010 應用程式
在 SharePoint 應用程式中包含自動程式碼 UI 測試，可讓您驗證整個應用程式 (包括其 UI 控制項) 是否正常運作。 自動程式碼 UI 測試也可以驗證使用者介面中的值和邏輯。  
  
 **需求**  
  
-   Visual Studio 企業版  
  
## <a name="what-else-should-i-know-about-coded-ui-tests"></a>有關自動程式碼 UI 測試，還有什麼是我應該知道的?  
 若要深入了解使用自動程式化 UI 測試的優點，請參閱[使用使用者介面自動化測試程式碼](../test/use-ui-automation-to-test-your-code.md)和[使用 Visual Studio 2012 測試持續傳遞 - 第 5 章：自動化系統測試](http://go.microsoft.com/fwlink/?LinkID=255196)。  
  
 **備註**  
  
-   ![必要條件](../test/media/prereq.png "Prereq") 只有 SharePoint 2010 才支援 SharePoint 應用程式的自動程式化 UI 測試。  
  
-   ![必要條件](../test/media/prereq.png "Prereq") SharePoint 應用程式中不支援 Visio 和 PowerPoint 2010 控制項。  
  
## <a name="creating-a-coded-ui-test-for-your-sharepoint-app"></a>建立 SharePoint 應用程式的自動程式碼 UI 測試  
 為您的 SharePoint 2010 應用程式[建立自動程式碼 UI 測試](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) 的方式，與為其他類型應用程式建立測試的方式相同。 所有控制項都可在 Web 編輯介面上錄製和播放。 選取分類和 Web 組件的介面都是標準的 Web 控制項。  
  
 ![SharePoint 網頁組件](../test/media/cuit_sharepoint.png "CUIT_SharePoint")  
  
> [!NOTE]
>  如果您正在錄製動作，請在產生程式碼之前驗證動作。 由於有多個行為與滑鼠停留相關聯，因此它預設為開啟狀態。 從您的自動程式碼 UI 測試中移除多餘的停留動作時務必小心。 您可以編輯用於測試的程式碼來進行這項作業，或是使用 [自動程式碼 UI 測試編輯器](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)。  
  
## <a name="including-testing-of-office-2010-controls-within-your-sharepoint-app"></a>在 SharePoint 應用程式中包含 Office 2010 控制項的測試  
 若要在 SharePoint 應用程式中啟用某些 Office 2010 Web 組件的自動化，則必須稍微修改程式碼。  
  
> [!WARNING]
>  不支援 Visio 和 PowerPoint 2010 控制項。  
  
### <a name="excel-2010-cell-controls"></a>Excel 2010 儲存格控制項  
 若要包括 Excel 儲存格控制項，您必須在自動程式化 UI 測試的程式碼中進行一些變更。  
  
> [!WARNING]
>  若在任何 Excel 儲存格中輸入文字，後面接著方向鍵動作，則這類動作無法正確錄製。 使用滑鼠選取儲存格。  
  
 如果您錄製空儲存格上的動作，則必須按兩下儲存格然後執行一組文字作業，藉此修改程式碼。 由於在儲存格中按一下，再接著任何鍵盤動作都會啟動儲存格內的 `textarea` ，因此必須這樣做。 僅錄製空儲存格上的 `setvalue` 會搜尋 `editbox` ，但是在按下儲存格之前它並不存在。 例如:   
  
```csharp  
Mouse.DoubliClick(uiItemCell,new Point(31,14));  
uiGridKeyboardInputEdit.Text=value;  
```  
  
 如果您在非空白儲存格上錄製動作，則錄製過程會變得較複雜，因為您將文字加入至儲存格時，會加入一個新的 \<div> 控制項做為儲存格的子系。 新的 \<div> 控制項會包含您剛輸入的文字。 錄製器需要錄製新 \<div> 控制項上的動作，但是卻無法錄製，因為在輸入測試之前，新的 \<div> 控制項並不存在。 您必須手動進行下列程式碼變更，才能解決這個問題。  
  
1.  移至儲存格初始化，並將 `RowIndex` 和 `ColumnIndex` 設為主要屬性：  
  
    ```csharp  
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";   
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";  
    ```  
  
2.  搜尋儲存格的 `HtmlDiv` 子系：  
  
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
  
3.  在 `HtmlDiv`上加入滑鼠按兩下動作的程式碼：  
  
    ```csharp  
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )  
    ```  
  
4.  加入程式碼設定 `TextArea`上的文字：  
  
    ```csharp  
    uIGridKeyboardInputEdit.Text = value; }  
    ```  
  
## <a name="enabling-coded-ui-testing-of-silverlight-web-parts-in-your-sharepoint-2010-app"></a>啟用 SharePoint 2010 應用程式中 Silverlight Web 組件的自動程式碼 UI 測試  
 Visual Studio 2012 及更新版本不支援 Silverlight 測試。 不過，若要在 SharePoint 2010 應用程式中測試 Silverlight Web 組件，您可以從 Visual Studio 組件庫個別安裝 Silverlight 外掛程式。  
  
#### <a name="setting-up-your-machine"></a>設定您的電腦  
  
1.  確定您已安裝 Visual Studio 2012.1 或更新版本。  
  
2.  安裝 [適用於 Silverlight 的 Microsoft Visual Studio UI 測試外掛程式](http://visualstudiogallery.msdn.microsoft.com/28312a61-9451-451a-990c-c9929b751eb4)。  
  
3.  安裝 [Fiddler](http://www.fiddler2.com/fiddler2/)。 這是擷取和記錄 HTTP 流量的簡單工具。  
  
4.  下載 [fiddlerXap 專案](http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-components-postattachments/00-10-36-48-70/FiddlerXapProxy.zip)。 將它解壓縮、進行建置，並執行 "CopySLHelper.bat" 指令碼，安裝使用 Fiddler 工具測試 Silverlight Web 組件時所需的協助程式 DLL。  
  
 設定電腦之後，依照下列步驟，開始測試您的 SharePoint 2010 應用程式與 Silverlight Web 組件：  
  
#### <a name="testing-silverlight-web-parts"></a>測試 Silverlight Web 組件  
  
1.  啟動 Fiddler。  
  
2.  清除瀏覽器快取。 由於通常會快取包含 Silverlight UI 自動化協助程式 DLL 的 XAP 檔，因此必須這樣做。 我們必須確定選取的是修改過的 XAP 檔，因此要清除瀏覽器快取。  
  
3.  開啟網頁。  
  
4.  啟動錄製器並產生程式碼，就像進行一般 Web 應用程式測試一樣。  
  
5.  您應該確認產生的程式碼參考 Microsoft.VisualStudio.TestTools.UITest.Extension.Silverlight.dll。  
  
     如需詳細資訊，請參閱 [使用 Visual Studio 2012 進行 SharePoint 2010 UI 測試](http://blogs.msdn.com/b/visualstudioalm/archive/2012/11/01/ui-testing-sharepoint-2010-with-visual-studio-2012.aspx)  
  
## <a name="external-resources"></a>外部資源  
  
### <a name="blogs"></a>部落格  
 [使用 Visual Studio 2012 進行 SharePoint 2010 UI 測試](http://blogs.msdn.com/b/visualstudioalm/archive/2012/11/01/ui-testing-sharepoint-2010-with-visual-studio-2012.aspx)  
  
 [了解自動程式碼 UI 測試中 Silverlight 控制項的搜尋邏輯](http://blogs.msdn.com/b/tapas_sahoos_blog/archive/2010/11/16/understanding-the-search-logic-for-silverlight-controls-in-coded-ui-test.aspx)  
  
 [擷取 Silverlight 控制項的屬性](http://blogs.msdn.com/b/tapas_sahoos_blog/archive/2010/11/16/fetching-property-of-a-silverlight-control.aspx)  
  
 [自動程式碼 UI 測試的內容索引](http://blogs.msdn.com/b/mathew_aniyan/archive/2010/02/11/content-index-for-coded-ui-test.aspx)  
  
### <a name="guidance"></a>指引  
 [使用 Visual Studio 2012 測試持續傳遞 - 第 5 章：自動化系統測試](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
### <a name="forum"></a>論壇  
 [Visual Studio ALM + Team Foundation Server 部落格](http://go.microsoft.com/fwlink/?LinkID=254496)  
  
## <a name="see-also"></a>另請參閱

[使用 UI 自動化來測試您的程式碼](../test/use-ui-automation-to-test-your-code.md)  
[建立 SharePoint 方案](/office-dev/office-dev/create-sharepoint-solutions)   
[驗證及偵錯 SharePoint 程式碼](/office-dev/office-dev/verifying-and-debugging-sharepoint-code)   
[建置和偵錯 SharePoint 方案](/office-dev/office-dev/building-and-debugging-sharepoint-solutions)   
[剖析 SharePoint 應用程式的效能](/office-dev/office-dev/profiling-the-performance-of-sharepoint-applications)
