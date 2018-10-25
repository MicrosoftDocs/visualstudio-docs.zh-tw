---
title: 針對 SharePoint 方案進行疑難排解 |Microsoft Docs
ms.custom: ''
ms.date: 02/22/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9f029cad2b0c8cb215a054502de5bc693cce5df5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928954"
---
# <a name="troubleshoot-sharepoint-solutions"></a>SharePoint 方案進行疑難排解
  當您使用偵錯 SharePoint 方案時，則可能會發生下列問題或警示[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]偵錯工具。 如需詳細資訊，請參閱 <<c0> [ 偵錯 SharePoint 2007 工作流程方案](http://msdn.microsoft.com/en-us/3a5392f3-66f3-48be-956e-02de23fa6247)。
  
## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>沙箱化視覺 web 組件中的語彙基元限制
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
  
## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>專案和專案項目的名稱中的字元限制
 專案和專案項目的名稱只能包含在 SharePoint 2010 中的部署路徑內有效的字元。 不允許任何其他字元。  
  
### <a name="error-message"></a>錯誤訊息
 「 無效的字元 」 錯誤訊息。  
  
### <a name="resolution"></a>解決方式  
 SharePoint 專案和專案項目的名稱只能使用下列字元：  
  
- 英數字 ASCII 字元  
  
- 空格  
  
- 句號 （.）  
  
- 逗號 （，）  
  
- 底線 (_)  
  
- 虛線 （-）  
  
- 反斜線 (\\)  
  
  在封裝專案時，驗證規則會針對每一個您要部署的檔案驗證 deployment-path 屬性是否只包含這些有效的字元。  
  
## <a name="errors-when-creating-custom-fields"></a>建立自訂欄位時發生錯誤
 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中，自訂欄位會以 XML 定義。 如果未使用特定格式定義或參考欄位，則可能會發生錯誤。  
  
### <a name="error-message"></a>錯誤訊息
 在封裝階段的 「 無效的字元 」 錯誤訊息。  
  
### <a name="resolution"></a>解決方式  
 欄位定義的 ID 必須是以大括號括住的 GUID，如下列範例所示：  
  
```xml  
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Type="Note"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Group="A Custom Group">  
</Field>.  
```  
  
 使用空的項目格式如下列範例所示，必須定義內容類型中的欄位參考 (\<FieldRef / >)，不是使用開始/結束項目 (\<FieldRef >\</FieldRef >):  
  
```xml  
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Required="TRUE"/>  
```  
  
 如果欄位的來源 XML 格式錯誤或者不是有效的 XML 檔案，或出現其他問題，則會發生「無法剖析檔案」錯誤。  
  
## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>新的非英文網站定義未出現在 站台建立頁面在部署之後
 建立和部署網站定義所使用的非英文版之後[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)](也就是地區設定版本[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]不是 1033年)，則**SharePoint 自訂** 索引標籤不會出現在**範本選擇** 方塊中，新的網站範本不會出現在**新的 SharePoint 網站**頁面。  
  
### <a name="error-message"></a>錯誤訊息
 無。  
  
### <a name="resolution"></a>解決方式  
 因為不正確的值中會發生這個問題**路徑**webtemp 站台定義設定的屬性檔，例如*webtemp_SiteDefinitionProject1.xml*。 在 **路徑**webtemp 檔案，位於屬性**部署位置**，將 1033年變更為適當的地區設定[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]。 例如，若要使用日本地區設定將值變更為 1041年。 如需詳細資訊，請參閱 <<c0> [ 由 Microsoft 指派的地區設定識別碼](http://go.microsoft.com/fwlink/?LinkID=165561)MSDN 網站上。  
  
## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>在乾淨系統上部署工作流程專案時，就會出現錯誤
 如果您在乾淨系統上的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中部署工作流程專案，就會發生此問題。 乾淨系統為具有 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 和 SharePoint 全新安裝，但是沒有任何已部署工作流程專案的電腦。  
  
### <a name="error-message"></a>錯誤訊息
 找不到 SharePoint 清單： 工作流程歷程記錄。  
  
### <a name="resolution"></a>解決方式  
 因為遺漏的工作流程歷程記錄清單，會發生此錯誤。 在開發環境是一個全新的系統，因為部署沒有工作流程，並且尚不存在的工作流程歷程記錄清單。 若要解決此問題，重新開啟工作流程精靈，這會導致建立工作流程歷程記錄清單。  
  
##### <a name="to-reenter-the-workflow-wizard"></a>若要重新輸入工作流程精靈  
  
1.  在 [**方案總管] 中**，選擇 [流程] 節點。  
  
2.  在 [**屬性**] 視窗中，選擇省略符號 （...） 按鈕，在任何具有省略符號按鈕的屬性。  
  
## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>使用者必須重新整理瀏覽器中的應用程式頁面來檢視更新的映像偵錯時
 如果您正在偵錯 SharePoint 方案，其中包含應用程式頁面會顯示映像，例如控制[!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)]影像控制項，您必須重新整理頁面，在瀏覽器中顯示映像所做的任何變更。  
  
## <a name="error-the-site-location-is-not-valid"></a>錯誤： 站台位置不正確
 如果發生此問題，可以[!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]未安裝。 如果您沒有 SharePoint 網站中所指定的系統管理員存取權，可能也會發生這**SharePoint 自訂精靈**。  
  
### <a name="error-message"></a>錯誤訊息
  
-   SharePoint 站台位置不是有效的。  
  
### <a name="resolution"></a>解決方式  
  
-   安裝 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]。  
  
-   請確定您需要 SharePoint 網站的系統管理員存取權。 如需詳細資訊，請參閱 <<c0> [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] 線上文章[指派或移除服務應用程式的系統管理員在 SharePoint Server](https://docs.microsoft.com/en-us/sharepoint/administration/assign-or-remove-administrators-of-service-applications)。  
  
## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>站台刪除網頁事件不會發生在事件接收器專案
 當您建立事件接收器專案時，您選取特定 Web 事件，例如"正在刪除站台 」 時永遠不會發生這個事件。  
  
### <a name="error-message"></a>錯誤訊息
 無。  
  
### <a name="resolution"></a>解決方式  
 功能範圍必須是 「 網站 」 來處理網站層級的事件，但事件接收者專案的預設功能範圍為"Web"，就會發生此問題。 受影響的 Web 事件如下：  
  
- 正在站台刪除 (WebDeleting)  
  
- 已刪除網站 (WebDeleted)  
  
- 站台正在移動 (WebMoving)  
  
- 已移動站台 (WebMoved)  
  
  若要修正此問題，變更功能範圍的事件接收器中，如下所示。  
  
##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>若要變更的功能範圍的事件接收器  
  
1.  在**方案總管 中**，開啟事件接收器 *.feature*中的檔案**功能設計工具**藉由按兩下檔案，或開啟其捷徑功能表，然後選擇**開啟**。  
  
2.  選擇箭號旁**範圍**，然後選擇**站台**中出現的清單。  
  
## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>商務資料連接模型專案中的識別項名稱變更之後，就會出現部署錯誤
 如果您變更商務資料連接 (BDC) 模型中實體的識別項名稱，然後再嘗試部署方案，就會發生這個問題。  
  
### <a name="error-messages"></a>錯誤訊息
  
-   \<*模型名稱*> 具有下列的外部內容類型啟用錯誤...  
  
-   IMetadataObject 名稱 '\<*模型名稱*>' 中欄位 'name' 是複製其值...  
  
### <a name="resolution"></a>解決方式  
 若要解決此問題，以手動的方式，刪除模型，並再重新部署解決方案。  您可以使用下列工具來刪除模型：  
  
-   SharePoint 2010 管理中心。 如需詳細資訊，請參閱 < [BDC 模型管理](http://go.microsoft.com/fwlink/?LinkID=181472)Microsoft TechNet 網站上。  
  
-   Windows PowerShell 您可以在命令提示字元中輸入下列命令來刪除模型：**移除 SPBusinessDataCatalogModel**。 如需詳細資訊，請參閱 <<c0> [ 一般 cmdlet (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkID=182375) Microsoft TechNet 網站上。  
  
## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>當您嘗試檢視 SharePoint 中的視覺 web 組件時，就會出現錯誤
 發生此問題時**路徑**使用者控制項屬性的開頭不是字串"CONTROLTEMPLATES\\"。  
  
### <a name="error-messages"></a>錯誤訊息
  
-   檔案 ' /_CONTROLTEMPLATES/*\<專案名稱 >*/*\<Web 組件名稱 >*/*\<使用者控制項名稱 >*.ascx' 不存在。  
  
-   '/' 應用程式中的伺服器錯誤。  
  
### <a name="resolution"></a>解決方式  
  
##### <a name="to-resolve-this-issue"></a>若要解決此問題  
  
1.  在 **方案總管**，選擇使用者控制項檔案，其副檔名 *.ascx*。  
  
2.  在功能表列上選擇 [**檢視** > **屬性] 視窗**。  
  
3.  在 [**屬性**] 視窗中，展開**部署位置**節點。  
  
4.  請確認的值**路徑**屬性開頭為字串"CONTROLTEMPLATES\\"。  
  
## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>包含工作表單欄位的匯入可重複使用工作流程執行時，就會出現錯誤
 如果您匯入包含一份工作表單，有一個欄位，工作流程，然後執行從中您將它匯入相同的系統上的 新的工作流程，就會發生此問題。  
  
### <a name="error-message"></a>錯誤訊息
 部署步驟啟用功能時發生錯誤: [識別碼] 欄位 [*Guid*] 功能中所定義 [*Guid*] 在目前網站集合或子網站中，找不到。  
  
### <a name="resolution"></a>解決方式  
 此錯誤是發生，因為匯入可重複使用工作流程專案中的欄位識別碼衝突的結果[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]不會變更工作表單欄位識別碼。 如果您部署包含原始工作流程的相同伺服器上匯入工作流程時，會發生欄位 ID 衝突。  
  
 若要解決此問題，使用 [尋找和取代] 功能來變更欄位 ID 屬性值中的所有匯入的工作流程檔案。  
  
## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>就會出現錯誤已重新命名匯入清單執行個體都會執行
 如果您重新命名匯入的清單執行個體，然後將它設為執行中，就會發生這個問題[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
### <a name="error-message"></a>錯誤訊息
 建置錯誤： 在部署步驟啟用功能時發生錯誤： 檔案 Template\Features\\[*匯入專案*<em>功能</em>*名稱*] \Files\Lists\\[*舊*<em>清單名稱</em>] \Schema.xml 不存在。  
  
### <a name="resolution"></a>解決方式  
 當您匯入的清單執行個體時，名為 CustomSchema 屬性就會加入至清單執行個體的 Elements.xml 檔案中。 Elements.xml 包含自訂的 schema.xml 清單執行個體的路徑。 當您重新命名使用中的清單執行個體[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、 自訂 schema.xml 的部署路徑變更，但是不會更新 CustomSchema 屬性的路徑值。 如此一來，清單執行個體找*schema.xml*舊啟用此功能時，會將 CustomSchema 屬性所指定的路徑中的檔案。  
  
 若要解決此問題，更新的部署位置的路徑*schema.xml* CustomSchema 屬性中的檔案。  
  
## <a name="sharepoint-debugging-session-terminated-by-iis"></a>SharePoint 偵錯工作階段被 IIS 終止
 如果您在中設定中斷點，就會發生這個問題[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 方案中，選擇**F5**鍵以執行它，然後停留在中斷點的時間超過 90 秒。  
  
### <a name="error-message"></a>錯誤訊息
 正在進行偵錯 Web 伺服器處理序已終止由網際網路資訊服務 (IIS)。 您可以在 IIS 中設定應用程式集區 Ping 設定來避免這個問題發生。 請參閱說明以取得詳細資料。  
  
### <a name="resolution"></a>解決方式  
 根據預設，IIS 應用程式集區會等候 90 秒，讓應用程式回應之後關閉應用程式。 這個程序稱為 「 ping 」 應用程式。 若要解決此問題，您可以增加等候時間，或停用應用程式完全 ping。  
  
##### <a name="to-access-the-iis-app-pool-settings"></a>若要存取 IIS 應用程式集區設定  
  
1.  開啟 [IIS Manager]。  
  
2.  在 **連線**窗格中，展開 SharePoint 伺服器節點，，然後選擇**應用程式集區**節點。  
  
3.  在 **應用程式集區**頁面上，選擇 SharePoint 應用程式集區 (通常是"SharePoint-80")，然後在**動作**窗格中，選擇**進階設定**連結。  
  
4.  若要增加 IIS 逾時之前的等待時間，變更的值**Ping 回應時間上限 （秒）** 大於 90 秒的值。  
  
5.  若要停用 IIS ping，請設定**已啟用 Ping**要**False**。  
  
## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>在 SharePoint 中會自動撤銷保留被遺棄的清單執行個體
 如果您執行下列步驟，就會發生這個問題。  
  
1.  建立的清單定義中包含的清單執行個體[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  選擇**F5**鍵執行方案。  
  
3.  停止偵錯，或關閉 SharePoint 網站。  
  
4.  重新開啟 SharePoint 網站，然後開啟的清單執行個體。  
  
### <a name="error-message"></a>錯誤訊息
 '/' 應用程式中的伺服器錯誤。  
  
### <a name="resolution"></a>解決方式  
 這是因為您在關閉 SharePoint 方案的偵錯工作階段之後自動撤銷功能撤銷方案。 撤銷從 SharePoint 刪除清單定義，但不會刪除清單執行個體。 基礎清單定義所需的清單執行個體。  
  
 若要解決此問題，部署解決方案，在功能表列選擇**建置** > **部署**。 (不偵錯方案，選擇**F5**索引鍵。)然後，刪除在 SharePoint 中的清單執行個體。  
  
## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>匯出的版本會取代原始的 SharePoint 方案
 如果您匯出 SharePoint 方案時，匯入到方案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，然後將解決方案部署回復至相同的網站從中匯出，就會取代原始的 SharePoint 方案。 如果您將解決方案部署到沒有原始解決方案在其上啟用的伺服器，則不會發生此問題。  
  
### <a name="error-message"></a>錯誤訊息
 無。  
  
### <a name="resolution"></a>解決方式  
 若要避免覆寫已匯出站台上的解決方案，變更方案識別碼的 Guid 和 Id 中的所有匯入功能，功能[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]專案。  
  
## <a name="error-appears-when-debugging-starts"></a>偵錯開始時，就會出現錯誤
 當您在 Visual Studio 中開始對 SharePoint 方案進行偵錯時出現錯誤，指出 Visual Studio 無法載入 Web.config 組態檔，因為所指的金鑰不在目錄中。  
  
### <a name="error-message"></a>錯誤訊息
 無法載入 Web.config 組態檔。 檢查任何格式不正確的 XML 項目的檔案，並再試一次。 發生下列錯誤： 指定的索引鍵不存在於字典。  
  
### <a name="resolution"></a>解決方式  
 若要解決此問題，請確定 Visual Studio 中 SharePoint 專案的 [網站 URL] 屬性值符合指派給 Web 應用程式之備用存取對應預設區域的 URL。 使用另一個區域 (例如內部網路) 做為 URL 無法解決此錯誤。 專案的網站 URL 和預設區域中的 URL 必須相符。 若要存取備用存取對應，開啟 SharePoint 2010 管理中心公用程式中，選擇**應用程式管理**連結，然後在**Web 應用程式**，選擇  **設定備用存取對應**連結。 如需詳細資訊，請參閱 <<c0> [ 建立 Web 應用程式的區域](http://go.microsoft.com/fwlink/?LinkId=192274)。  
  
## <a name="see-also"></a>另請參閱
 [針對 SharePoint 封裝和部署進行疑難排解](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)   
 [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Visual Studio 偵錯](/visualstudio/debugger/debugging-in-visual-studio)  
  
  
