---
title: SharePoint 方案的調試 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.WebConfigModificationDialog
- VS.SharePointTools.Project.DebuggingNotEnabled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d83c8ffd4fe5ebb627b70fa07f010bdc713225dd
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984504"
---
# <a name="debug-sharepoint-solutions"></a>Debug SharePoint 方案
  您可以使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 偵錯工具來調試 SharePoint 方案。 當您啟動偵錯工具時，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將專案檔案部署到 SharePoint 伺服器，然後在網頁瀏覽器中開啟 SharePoint 網站的實例。 下列各節說明如何在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中，對 SharePoint 應用程式進行 debug。

- [啟用調試](#enable-debugging)

- [F5 偵錯工具和部署程式](#f5-debug-and-deployment-process)

- [SharePoint 專案功能](#sharepoint-project-features)

- [Debug 工作流程](#debug-workflows)

- [Debug 功能事件接收器](#debug-feature-event-receivers)

- [啟用 ehanced 的調試資訊](#enable-enhanced-debugging-information)

## <a name="enable-debugging"></a>啟用偵錯
 當您第一次在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中進行 SharePoint 方案的偵錯工具時，對話方塊會通知您 web.config 檔案未設定為啟用偵測。 （當您安裝 SharePoint server 時，會建立 web.config 檔案。 如需詳細資訊，請參閱[使用](/previous-versions/office/developer/sharepoint-2010/ms460914(v=office.14))web.config 檔案）。對話方塊可讓您選擇是否要執行專案，而不需要進行偵測或修改 web.config 檔案以啟用調試。 如果您選擇第一個選項，專案將會正常執行。 如果您選擇第二個選項，則 web.config 檔案會設定為：

- 開啟呼叫堆疊（`CallStack="true"`）

- 停用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的自訂錯誤（`<customErrors mode="Off" />`）

- 啟用編譯調試（`<compilation debug="true">`）

  產生的 web.config 檔案如下所示：

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <configuration>
        ...
        <SharePoint>
            <SafeMode MaxControls="200"
                CallStack="true"
                DirectFileDependencies="10"
                TotalFileDependencies="50"
                AllowPageLevelTrace="false">
                ...
            </SafeMode>
        ...
        </SharePoint>
        <system.web>
            ...
            <customErrors mode="Off" />
            ...
            <compilation debug="true">
            ...
            </compilation>
            ...
        </system.web>
        ...
    </configuration>
```

 若要反轉變更並停用調試，請在 web.config 檔案中變更下列 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]：

- 關閉呼叫堆疊（`CallStack="false"`）

- 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] （`<customErrors mode="On" />`）中啟用自訂錯誤

- 停用編譯調試（`<compilation debug="false">`）

## <a name="f5-debug-and-deployment-process"></a>F5 偵錯工具和部署程式
 當您在 [偵錯工具] 模式中執行 SharePoint 專案時，SharePoint 部署程式會執行下列工作：

1. 執行可自訂的預先部署命令。

2. 使用 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 命令建立 Web 方案套件（.wsp）檔案。 .Wsp 檔案包含所有必要的檔案和功能。 如需詳細資訊，請參閱[解決方案總覽](/previous-versions/office/developer/sharepoint-2010/aa543214(v=office.14))。

3. 如果 SharePoint 方案是伺服器陣列方案，則會回收指定網站 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]的 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 應用程式集區。 此步驟會釋放由 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 工作者進程鎖定的檔案。

4. 如果先前版本的封裝已存在，則會撤銷 .wsp 檔案中舊版的功能和檔案。 此步驟會停用功能、卸載方案套件，然後刪除 SharePoint 伺服器上的方案套件。

5. 在 .wsp 檔案中安裝目前版本的功能和檔案。 此步驟會在 SharePoint 伺服器上新增和安裝方案。

6. 針對工作流程，會安裝工作流程元件。 您可以使用 [*元件位置*] 屬性來變更其位置。

7. 如果範圍是 Site 或 Web，就會在 SharePoint 中啟用專案的功能。 伺服器陣列和 WebApplication 範圍中的功能不會啟用。

8. 針對工作流程，會將工作流程與您在**Sharepoint 自訂嚮導**中選取的 sharepoint 文件庫、清單或網站產生關聯。

   > [!NOTE]
   > 只有當您在 wizard 中選取了 [**自動關聯工作流程**] 時，才會發生此關聯。

9. 執行可自訂的部署後命令。

10. 將 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 偵錯工具附加至 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 進程（*w3wp.exe .exe*）。 如果專案類型可讓您變更*沙箱化方案*屬性，且其值設定為**true**，則偵錯工具會附加至不同的進程（*spucworkerprocess.exe*）。 如需詳細資訊，請參閱[沙箱化方案考慮](../sharepoint/sandboxed-solution-considerations.md)。

11. 如果 SharePoint 方案是伺服器陣列方案，則啟動 JavaScript 偵錯工具。

12. 在網頁瀏覽器中顯示適當的 [程式庫]、[清單] 或 [網站] 頁面。

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 在每個工作完成後，在 [輸出] 視窗中顯示狀態訊息。 如果無法完成工作，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會在 [錯誤清單] 視窗中顯示錯誤訊息。

## <a name="sharepoint-project-features"></a>SharePoint 專案功能
 功能是可移植且模組化的功能單元，可使用網站定義來簡化網站的修改。 它也是 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] （WSS）元素的封裝，可以針對特定範圍啟用，並協助使用者完成特定的目標或工作。 範本會部署為功能。

 當您在 [debug] 模式中執行專案時，部署程式會在 *%COMMONPROGRAMFILES%\Microsoft Shared\web server extensions\14\TEMPLATE\FEATURES*的*功能*目錄中建立資料夾。 功能名稱的格式*專案名稱*為 _Feature*x*，例如 TestProject_Feature1。

 功能目錄中的解決方案資料夾包含*功能定義*檔和*工作流程定義*檔。 功能定義檔（Feature .xml）描述專案功能中的檔案。專案定義檔（*Elements .xml*）描述專案範本。 可以在**方案總管**中找到*Elements* ，但是在建立方案套件時，就會產生 xml 功能。 如需這些檔案的詳細資訊，請參閱[SharePoint 專案和專案專案範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。

## <a name="debug-workflows"></a>偵錯工作流程
 當您對工作流程專案進行調試時，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將工作流程範本（根據其類型）新增至文件庫或清單。 接著，您可以手動或藉由新增或更新專案來啟動工作流程範本。 然後，您可以使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 來進行工作流程的 debug。

> [!NOTE]
> 如果您將參考加入至其他元件，請確定這些元件安裝在全域組件快取中（[!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]）。 否則，工作流程方案將會失敗。 如需如何安裝元件的詳細資訊，請參閱[在檔或專案上手動啟動工作流程](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963)。

 不過，部署程式並不會啟動工作流程。 您必須從 SharePoint 網站啟動工作流程。 您也可以使用用戶端應用程式（例如 Microsoft Office Word 2010），或使用個別的伺服器端程式碼來啟動工作流程。 使用**SharePoint 自訂嚮導**中指定的其中一種方法。

 例如，如果您指定可以手動啟動工作流程，請直接從程式庫或清單中的專案啟動工作流程。 如需如何手動啟動工作流程的詳細資訊，請參閱在[檔專案上手動啟動工作流程](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963)。

## <a name="debug-feature-event-receivers"></a>Debug 功能事件接收器
 根據預設，當您執行 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 應用程式時，系統會在 SharePoint 伺服器上自動為您啟用其功能。 不過，這會導致您在偵錯工具功能事件接收器時發生問題，因為當功能是由 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]啟動時，它會在與偵錯工具不同的進程中執行。 這表示某些偵錯工具功能（例如中斷點）將無法正常運作。

 若要在 SharePoint 中停用自動啟動功能，並允許適當的功能事件接收器偵錯工具，請將專案的 [作用中**部署**設定] 屬性值設為 [**不啟用**]，然後再進行偵錯工具。 接著，您在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中開始對 SharePoint 應用程式進行偵錯之後，請手動啟用 SharePoint 中的功能。 若要啟用此功能，請在 SharePoint 中開啟 [**網站動作**] 功能表，選擇 [**網站設定**]，選擇 [**管理網站功能**] 連結，然後選擇功能旁的 [**啟動**] 按鈕，以正常方式繼續進行調試。

## <a name="enable-enhanced-debugging-information"></a>啟用增強的調試資訊
 由於在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 程式（devenv）、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 主機進程（*vssphost4*）、SHAREPOINT 和 WCF 層之間，有時會有複雜的互動，因此在建立、部署等等時，診斷所發生的錯誤可能是相當. 為了協助您解決這類錯誤，您可以啟用增強的調試資訊。 若要這麼做，請移至 Windows 登錄中的下列登錄機碼：

 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools**

 如果 "EnableDiagnostics" **REG_DWORD**值尚不存在，請手動建立。 將 "EnableDiagnostics" 值設為 "1"。

 如果將此索引鍵值設定為1，每當您在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中執行時，發生專案系統錯誤時，堆疊追蹤資訊就會出現在 [**輸出**] 視窗中。 若要停用增強型偵錯資訊，請將 EnableDiagnostics 設定回 0，或刪除該值。

 如需有關其他 SharePoint 登錄機碼的詳細資訊，請參閱[Visual Studio 中 sharepoint 工具的偵錯工具延伸](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)模組。

## <a name="see-also"></a>請參閱
- [SharePoint 方案疑難排解](../sharepoint/troubleshooting-sharepoint-solutions.md)
