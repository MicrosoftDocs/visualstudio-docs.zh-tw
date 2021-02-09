---
title: 疑難排解 SharePoint 方案 |Microsoft Docs
description: 查看當您使用 Visual Studio 偵錯工具來進行 SharePoint 方案的偵錯工具時，可能發生的問題或警示。
ms.custom: SEO-VS-2020
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Tools.SharePoint.Errors.Debugging
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, troubleshooting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c6b0e031e96d2543ae0bb109f243824125f431a3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892290"
---
# <a name="troubleshoot-sharepoint-solutions"></a>疑難排解 SharePoint 方案
  當您使用偵錯工具來進行 SharePoint 方案的偵錯工具時，可能會發生下列問題或警示 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。 如需詳細資訊，請參閱 [SharePoint 2007 工作流程解決方案的調試](/previous-versions/bb386166(v=vs.100))程式。

## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>沙箱化視覺 web 元件中的權杖限制
 沙箱化方案中的視覺 Web 組件無法處理標準語彙基元，例如 SharePoint 執行階段支援的 $SPUrl。 因此無法解析 URL，而且如果您直接在指令碼項目中參考內容，也無法在視覺 Web 組件設計工具的 [設計] 檢視中預覽該內容，如下列範例所示：

```xml
<script src="<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>
```

 若要解決這項限制並解析語彙基元，請使用常值參考語彙基元：

```xml
<asp:literal ID="Literal1" runat="server" Text="<script src='" />
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />
```

## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>專案和專案專案名稱的字元限制
 專案和專案項目的名稱只能包含在 SharePoint 2010 中的部署路徑內有效的字元。 不允許任何其他字元。

### <a name="error-message"></a>錯誤訊息
 「不正確字元」錯誤訊息。

### <a name="resolution"></a>解決方案
 SharePoint 專案和專案項目的名稱只能使用下列字元：

- 英數位元 ASCII 字元

- Space

- 期間 (。 ) 

- 逗號 (,)

- 底線 (_)

- 虛線 (-) 

- 反斜線 (\\)

  在封裝專案時，驗證規則會針對每一個您要部署的檔案驗證 deployment-path 屬性是否只包含這些有效的字元。

## <a name="errors-when-creating-custom-fields"></a>建立自訂欄位時發生錯誤
 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中，自訂欄位會以 XML 定義。 如果未使用特定格式定義或參考欄位，則可能會發生錯誤。

### <a name="error-message"></a>錯誤訊息
 封裝時出現「無效字元」的錯誤訊息。

### <a name="resolution"></a>解決方案
 欄位定義的 ID 必須是以大括號括住的 GUID，如下列範例所示：

```xml
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Type="Note"
    Name="PatientName"
    DisplayName="Patient Name"
    Group="A Custom Group">
</Field>.
```

 如下列範例所示，內容類型中的欄位參考必須使用空白元素格式 () 來定義 \<FieldRef /> ，而不是使用 () 的開始/結束元素 \<FieldRef> \</FieldRef> ：

```xml
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Name="PatientName"
    DisplayName="Patient Name"
    Required="TRUE"/>
```

 如果欄位的來源 XML 格式錯誤或者不是有效的 XML 檔案，或出現其他問題，則會發生「無法剖析檔案」錯誤。

## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>部署之後，新的非英文網站定義不會出現在網站建立頁面中
 當您使用非英文版的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (（也就是具有) 1033 以外的地區設定的版本）建立和部署網站定義之後 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] ，[ **sharepoint 自訂** ] 索引標籤不會出現在 [ **範本選擇** ] 方塊中，而且新的網站範本不會出現在 [ **新的 SharePoint 網站** ] 頁面中。

### <a name="error-message"></a>錯誤訊息
 無。

### <a name="resolution"></a>解決方案
 因為 webtemp 網站定義設定檔的 **Path** 屬性值不正確，例如 *webtemp_SiteDefinitionProject1.xml*，所以會發生此問題。 在 webtemp 檔案的 [ **路徑** ] 屬性（位於 **部署位置** 底下），將1033變更為適當的地區設定 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] 。 例如，若要使用日文地區設定，請將值變更為1041。 如需詳細資訊，請參閱 [Microsoft 指派的地區設定識別碼](/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c)。

## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>在乾淨的系統上部署工作流程專案時，出現錯誤
 如果您在乾淨系統上的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中部署工作流程專案，就會發生此問題。 乾淨系統為具有 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 和 SharePoint 全新安裝，但是沒有任何已部署工作流程專案的電腦。

### <a name="error-message"></a>錯誤訊息
 找不到 SharePoint 清單：工作流程歷程記錄。

### <a name="resolution"></a>解決方案
 發生此錯誤的原因是遺失工作流程歷程記錄清單。 由於開發環境是乾淨的系統，因此不會部署任何工作流程，而且工作流程歷程記錄清單還不存在。 若要解決此問題，請重新開啟工作流程 wizard，這會導致建立工作流程歷程記錄清單。

##### <a name="to-reenter-the-workflow-wizard"></a>重新輸入工作流程嚮導

1. 在 **方案總管** 中，選擇 [工作流程] 節點。

2. 在 [ **屬性** ] 視窗中，選擇具有省略號按鈕之任何屬性的省略號 ( ... ) 按鈕。

## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>使用者必須在偵錯工具時重新整理瀏覽器中的應用程式頁面，才能查看更新的影像
 如果您正在使用顯示影像的控制項（例如影像控制項）來對包含應用程式頁面的 SharePoint 方案進行偵錯工具 [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)] ，則必須重新整理瀏覽器中的頁面，以顯示對影像所做的任何變更。

## <a name="error-the-site-location-is-not-valid"></a>錯誤：網站位置無效
 如果未安裝，就會發生此問題 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] 。 如果您沒有在 [ **Sharepoint 自訂嚮導]** 中指定之 sharepoint 網站的系統管理員存取權，也可能會發生這種情況。

### <a name="error-message"></a>錯誤訊息

- SharePoint 網站位置無效。

### <a name="resolution"></a>解決方案

- 安裝 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]。

- 確定您擁有 SharePoint 網站的系統管理員存取權。 如需詳細資訊，請參閱 [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] 線上文章 [在 SharePoint Server 中指派或移除服務應用程式的系統管理員](/sharepoint/administration/assign-or-remove-administrators-of-service-applications)。

## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>事件接收器專案中不會發生網站刪除 web 事件
 當您建立事件接收器專案並選取某些 Web 事件（例如「正在刪除網站」）時，就不會發生此事件。

### <a name="error-message"></a>錯誤訊息
 無。

### <a name="resolution"></a>解決方案
 之所以發生此問題，是因為功能範圍必須是「網站」才能處理網站層級的事件，但事件接收器專案的預設功能範圍是「Web」。 受影響的 Web 事件如下：

- 正在刪除網站 (WebDeleting) 

- 網站已 (WebDeleted 刪除) 

- 正在將網站移 (WebMoving) 

- 網站已移動 (WebMoved) 

  若要修正此問題，請變更事件接收器的功能範圍，如下所示。

##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>變更事件接收器的功能範圍

1. 在 **方案總管** 中，按兩下檔案或開啟其快捷方式功能表，然後選擇 [**開啟**]，在 **功能設計** 工具中開啟事件接收器的 [*功能*] 檔案。

2. 選擇 [ **範圍**] 旁邊的箭號，然後在出現的清單中選擇 [ **網站** ]。

## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>在商務資料連線模型專案中的識別碼名稱變更之後，會出現部署錯誤
 如果您變更商務資料連線中實體的識別碼名稱 (BDC) 模型，然後嘗試部署方案，就會發生這個問題。

### <a name="error-messages"></a>錯誤訊息

- \<*model name*> 具有下列外部內容類型啟用錯誤 .。。

- 名稱為 ' ' 的 IMetadataObject \<*model name*> 有重複的欄位 ' Name ' 中的值 .。。

### <a name="resolution"></a>解決方案
 若要解決此問題，請手動刪除模型，然後重新部署方案。  您可以使用下列其中一種工具來刪除模型：

- SharePoint 2010 管理中心。 如需詳細資訊，請參閱 Microsoft TechNet 網站上的 [BDC 模型管理](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14)#delete-a-bdc-model) 。

- Windows PowerShell 您可以在命令提示字元中輸入下列命令來刪除模型： **SPBusinessDataCatalogModel**。 如需詳細資訊，請參閱 Microsoft TechNet 網站上的 [一般 Cmdlet (SharePoint Server 2010) ](/powershell/module/sharepoint-server) 。

## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>當您嘗試在 SharePoint 中查看視覺網頁元件時，會出現錯誤
 當使用者控制項的 **Path** 屬性不是以字串 "CONTROLTEMPLATES" 開頭時，就會發生這個問題 \\ 。

### <a name="error-messages"></a>錯誤訊息

- 檔案 '/_CONTROLTEMPLATES/ *\<project name>* / *\<Web Part name>* / *\<user control name>* .ascx ' 不存在。

- '/' 應用程式中有伺服器錯誤。

### <a name="resolution"></a>解決方案

##### <a name="to-resolve-this-issue"></a>若要解決此問題

1. 在 **方案總管** 中，選擇使用者控制項檔案，其副檔名為 *.ascx*。

2. 在功能表列上，選擇 [**視圖**  >  **屬性視窗]**。

3. 在 [ **屬性** ] 視窗中，展開 [ **部署位置** ] 節點。

4. 確定 **Path** 屬性的值開頭為 "CONTROLTEMPLATES \\ " 字串。

## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>執行包含工作表單域的匯入可重複使用工作流程時，出現錯誤
 如果您匯入的工作流程包含具有欄位的工作表單，然後在匯入它的相同系統上執行新的工作流程，就會發生這個問題。

### <a name="error-message"></a>錯誤訊息
 部署步驟「啟動功能」發生錯誤：在目前網站集合或子網站中找到功能 [*guid*] 中定義的欄位 *識別碼 [guid*]。

### <a name="resolution"></a>解決方案
 此錯誤是因為中的 [匯入可重複使用的工作流程] 專案 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 未變更工作表單域識別碼所發生的欄位識別碼衝突所造成。 如果您在包含原始工作流程的相同伺服器上部署匯入的工作流程，就會發生欄位識別碼衝突。

 若要解決這個問題，請使用 [尋找和取代] 功能，在所有匯入的工作流程檔案中變更 [欄位識別碼] 屬性的值。

## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>當重新命名的匯入清單實例執行時，出現錯誤
 如果您重新命名匯入的清單實例，然後在中執行它，就會發生這個問題 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。

### <a name="error-message"></a>錯誤訊息
 組建錯誤：部署步驟「啟動功能」發生錯誤：檔案 Template\Features [匯 \\ *入專案*<em>功能</em>*名稱*] \Files\Lists \\ [*舊* 的 <em>清單名稱</em>] \Schema.xml 不存在。

### <a name="resolution"></a>解決方案
 當您匯入清單實例時，名為 CustomSchema 的屬性會加入至清單實例的 Elements.xml 檔案中。 Elements.xml 包含清單實例的自訂 schema.xml 路徑。 當您在中重新命名清單實例時 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，自訂 schema.xml 的部署路徑會變更，但 CustomSchema 屬性的路徑值不會更新。 因此，當此功能啟動時，清單實例無法在 CustomSchema 屬性所指定的舊路徑中找到 *schema.xml* 的檔案。

 若要解決此問題，請在 CustomSchema 屬性中更新 *schema.xml* 檔案的部署位置路徑。

## <a name="sharepoint-debugging-session-terminated-by-iis"></a>IIS 終止 SharePoint 偵錯工具會話
 如果您在 SharePoint 方案中設定中斷點 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 、選擇 **F5** 鍵來執行它，然後維持在超過90秒的中斷點，就會發生這個問題。

### <a name="error-message"></a>錯誤訊息
 Internet Information Services (IIS) 終止正在進行調試的 Web 服務器進程。 您可以在 IIS 中設定應用程式集區 Ping 設定來避免這個問題發生。 如需詳細資訊，請參閱說明。

### <a name="resolution"></a>解決方案
 根據預設，IIS 應用程式集區會等待90秒，讓應用程式在關閉應用程式之前回應。 此處理程式稱為「ping」應用程式。 若要解決此問題，您可以增加等候時間或完全停用應用程式 ping。

##### <a name="to-access-the-iis-app-pool-settings"></a>存取 IIS 應用程式集區設定

1. 開啟 IIS 管理員。

2. 在 [ **連接** ] 窗格中，展開 [SharePoint 伺服器] 節點，然後選擇 [ **應用程式** 集區] 節點。

3. 在 [ **應用程式** 集區] 頁面上，選擇 SharePoint 應用程式集區 (通常是 "sharepoint-80" ) ，然後在 [ **動作** ] 窗格中，選擇 [ **Advanced Settings** ] 連結。

4. 若要增加 IIS timeout 之前的等候時間，請將 [ **Ping 回應時間上限] (秒)** 值變更為大於90秒的值。

5. 若要停用 IIS ping，請將 [ **啟用 ping** ] 設定為 [ **False**]。

## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>自動撤銷會在 SharePoint 中保留孤立清單實例
 如果您採取下列步驟，就會發生此問題。

1. 在中建立具有清單實例的清單定義 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。

2. 選擇 **F5** 鍵以執行方案。

3. 停止調試或關閉 SharePoint 網站。

4. 重新開啟 SharePoint 網站，然後開啟清單實例。

### <a name="error-message"></a>錯誤訊息
 '/' 應用程式中有伺服器錯誤。

### <a name="resolution"></a>解決方案
 發生這種情況的原因是，當您關閉 SharePoint 方案的偵測會話之後，自動撤銷功能就會撤銷方案。 收回會從 SharePoint 刪除清單定義，但不會刪除清單的實例。 清單實例需要基礎清單定義。

 若要解決此問題，請在功能表列上選擇 [**組建** 部署] 來部署解決方案  >  ****。  (不要藉由選擇 **F5** 鍵來將方案進行偵錯工具。 ) 然後刪除 SharePoint 中的清單實例。

## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>原始 SharePoint 方案會取代為匯出的版本
 如果您匯出 SharePoint 方案、將方案匯入，然後將 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 方案部署回匯出的相同網站，則會取代原始的 SharePoint 方案。 如果您將方案部署到未在其上啟動原始方案的伺服器，就不會發生這個問題。

### <a name="error-message"></a>錯誤訊息
 無。

### <a name="resolution"></a>解決方案
 若要避免覆寫匯出的來源網站上的方案，請變更 SolutionID 的 Guid，以及專案中所有匯入功能的功能識別碼 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。

## <a name="error-appears-when-debugging-starts"></a>啟動調試時出現錯誤
 當您在 Visual Studio 中開始對 SharePoint 方案進行偵錯時出現錯誤，指出 Visual Studio 無法載入 Web.config 組態檔，因為所指的金鑰不在目錄中。

### <a name="error-message"></a>錯誤訊息
 無法載入 Web.config 設定檔。 請檢查檔案中是否有任何格式不正確的 XML 元素，然後再試一次。 發生下列錯誤：指定的索引鍵不存在於字典中。

### <a name="resolution"></a>解決方案
 若要解決此問題，請確定 Visual Studio 中 SharePoint 專案的 [網站 URL] 屬性值符合指派給 Web 應用程式之備用存取對應預設區域的 URL。 使用另一個區域 (例如內部網路) 做為 URL 無法解決此錯誤。 專案的網站 URL 和預設區域中的 URL 必須相符。 若要存取備用存取對應，請開啟 SharePoint 2010 管理中心公用程式，選擇 [ **應用程式管理** ] 連結，然後在 [ **Web 應用程式**] 下，選擇 [ **設定備用存取** 對應] 連結。 如需詳細資訊，請參閱 [建立 Web 應用程式的區域](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263087(v=office.12))。

## <a name="see-also"></a>另請參閱

- [針對 SharePoint 封裝和部署進行疑難排解](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)
- [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Visual Studio 偵錯](../debugger/debugger-feature-tour.md)