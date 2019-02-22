---
title: 偵錯 SharePoint 方案 |Microsoft Docs
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
ms.openlocfilehash: d375386da4d62117105bc732425a2678e0a48d0a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56640229"
---
# <a name="debug-sharepoint-solutions"></a>偵錯 SharePoint 方案
  您可以使用偵錯 SharePoint 方案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]偵錯工具。 當您啟動偵錯，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]專案會將檔案部署到 SharePoint 伺服器，然後開啟 網頁瀏覽器中的 SharePoint 網站的執行個體。 下列各節將說明如何偵錯 SharePoint 應用程式[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

-   [啟用偵錯](#EnableDebug)

-   [F5 偵錯和部署程序](#Deployment)

-   [SharePoint 專案功能](#Features)

-   [偵錯工作流程](#Workflow)

-   [偵錯功能事件接收器](#FeatureEvents)

-   [啟用增強型偵錯資訊](#EnhancedDebug)

## <a name="enable-debugging"></a>啟用偵錯
 當您第一次偵錯 SharePoint 方案中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，對話方塊中，系統會通知您，web.config 檔案未設定為啟用偵錯。 （當您安裝 SharePoint server 時，會建立 web.config 檔案。 如需詳細資訊，請參閱 <<c0> [ 處理 Web.config 檔案](http://go.microsoft.com/fwlink/?LinkID=149266)。)對話方塊可讓您選擇執行專案但不偵錯，或修改的 web.config 檔案，以啟用偵錯。 如果您選擇第一個選項，專案將會正常執行。 如果您選擇第二個選項，則 web.config 檔案會設定為：

- 開啟 呼叫堆疊 (`CallStack="true"`)

- 停用中的自訂錯誤[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)](`<customErrors mode="Off" />`)

- 啟用編譯偵錯 (`<compilation debug="true">`)

  產生的 web.config 檔案如下：

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

 若要反向變更，並停用偵錯，變更下列[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]web.config 檔案中：

-   關閉 呼叫堆疊 (`CallStack="false"`)

-   啟用自訂錯誤[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)](`<customErrors mode="On" />`)

-   停用編譯偵錯 (`<compilation debug="false">`)

## <a name="f5-debug-and-deployment-process"></a>F5 偵錯和部署程序
 當您在偵錯模式中執行您的 SharePoint 專案時，在 SharePoint 部署程序會執行下列工作：

1. 執行可自訂的預先部署命令。

2. 建立 Web 方案套件 (.wsp) 檔案使用[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]命令。 .Wsp 檔案包含的所有必要的檔案和功能。 如需詳細資訊，請參閱 <<c0> [ 解決方案概觀](http://go.microsoft.com/fwlink/?LinkID=128154)。

3. 如果伺服器陣列方案為 SharePoint 方案，回收[!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]指定的站台的應用程式集區[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]。 此步驟中釋放鎖定的檔案[!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]背景工作處理序。

4. 如果舊版的封裝已經存在，撤銷舊版本的.wsp 檔案中的功能。 此步驟中會停用功能、 方案套件時，會解除安裝，然後刪除 SharePoint 伺服器上的方案套件。

5. 安裝目前版本的功能和檔案的.wsp 檔案中。 此步驟中新增，並在 SharePoint 伺服器上安裝解決方案。

6. 工作流程，會安裝工作流程組件。 您可以使用，以變更其位置*組件位置*屬性。

7. 如果範圍是網站或 Web，請啟動 SharePoint 專案的功能。 在伺服器陣列和 WebApplication 範圍中的功能並未啟用。

8. 工作流程，將關聯工作流程，與 SharePoint 文件庫、 清單中或您在選取的站台**SharePoint 自訂精靈**。

   > [!NOTE]
   >  只有當您選取，就會發生此關聯**自動關聯工作流程**精靈中。

9. 執行可自訂的部署後命令。

10. 附加[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]偵錯工具，[!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)]程序 (*w3wp.exe*)。 如果專案類型可讓您變更*沙箱化方案*屬性，且其值設定為 **，則為 true**，則偵錯工具會附加至不同的處理序 (*SPUCWorkerProcess.exe*). 如需詳細資訊，請參閱 <<c0> [ 沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)。

11. 如果 SharePoint 方案是伺服器陣列方案，請啟動 JavaScript 偵錯工具。

12. 在 Web 瀏覽器中顯示適當的程式庫、 清單或網站頁面。

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 每個工作完成後，請在 [輸出] 視窗中顯示狀態訊息。 如果無法完成工作，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]錯誤清單 視窗中顯示的錯誤訊息。

## <a name="sharepoint-project-features"></a>SharePoint 專案功能
 功能是功能的可修改站台的簡化使用網站定義的可攜性和模組化單位。 它也是一個封裝的[!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)](WSS) 項目，可以啟動的特定範圍，而且，可協助使用者完成特定目標或工作。 範本會部署為功能。

 當您在偵錯模式中執行專案時，部署程序，將會建立在資料夾*功能*目錄 *%COMMONPROGRAMFILES%\Microsoft Shared\web server extensions\14\TEMPLATE\FEATURES*。 功能名稱的格式*專案名稱*_Feature*x*，例如 TestProject_Feature1。

 方案資料夾內的功能目錄包含*功能定義*檔案並*工作流程定義*檔案。 功能定義檔案 (Feature.xml) 會描述專案的功能的專案定義檔中的檔案 (*Elements.xml*) 描述的專案範本。 *Elements.xml*篇**方案總管 中**，但在建立方案套件時，會產生 Feature.xml。 如需有關這些檔案的詳細資訊，請參閱 < [SharePoint 專案和專案項目範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。

## <a name="debug-workflows"></a>偵錯工作流程
 當您偵錯工作流程專案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]至程式庫或清單加入工作流程範本 （取決於其型別）。 您可以接著啟動工作流程範本，以手動方式或藉由新增或更新項目。 您可以接著使用[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]偵錯工作流程。

> [!NOTE]
>  如果您加入其他組件的參考，請確定這些組件會安裝在全域組件快取 ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)])。 否則，工作流程解決方案將會失敗。 如需有關如何安裝組件的資訊，請參閱 <<c0> [ 手動開始文件或項目上的 工作流程](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963)。

 不過，部署程序無法啟動工作流程。 您必須從 SharePoint 網站啟動工作流程。 使用 Microsoft Office Word 2010 中，用戶端應用程式，或使用不同的伺服器端程式碼，您也可以啟動工作流程。 使用其中一種方法中指定**SharePoint 自訂精靈**。

 例如，如果您指定工作流程都可以手動啟動，請直接從程式庫或清單中的項目啟動工作流程。 如需如何以手動方式啟動工作流程的詳細資訊，請參閱[手動開始文件項目上的 工作流程](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963)。

## <a name="debug-feature-event-receivers"></a>偵錯功能事件接收器
 根據預設，當您執行[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 應用程式，其功能會自動為您啟用 SharePoint 伺服器上。 不過，這會導致問題時您偵錯功能事件接收器，因為當啟動功能[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，它會在不同的程序比偵錯工具中執行。 這表示，某些偵錯的功能，例如中斷點，將無法正常運作。

 若要停用自動啟動 sharepoint 功能，並允許適當的功能事件接收器進行偵錯，來設定專案的值**現用部署組態**屬性設**無啟用**進行偵錯之前。 接著，您在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中開始對 SharePoint 應用程式進行偵錯之後，請手動啟用 SharePoint 中的功能。 若要啟用的功能，請開啟**站台動作**功能表，在 SharePoint 中，選擇**站台設定**，選擇**管理網站功能**連結，然後再選擇  **Activate**此功能，以繼續偵錯正常旁的按鈕。

## <a name="enable-enhanced-debug-information"></a>啟用增強型偵錯資訊
 由於之間可能很複雜的互動[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]程序 (devenv.exe)， [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 主機處理序 (*vssphost4.exe*)，SharePoint，與 WCF 層，診斷所發生的錯誤時建置、 部署及其他等等，可以是一項挑戰。 為了協助您解決這類錯誤，您可以啟用增強型偵錯資訊。 若要這樣做，請移至下列登錄機碼，在 Windows 登錄中：

 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools**

 如果"EnableDiagnostics" **REG_DWORD**值不存在，請以手動方式建立它。 將"EnableDiagnostics"值設為"1"。

 此索引鍵的值設定為 1 會導致堆疊追蹤資訊才會出現在**輸出**視窗執行時，專案系統錯誤發生時[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 若要停用增強型偵錯資訊，請將 EnableDiagnostics 設定回 0，或刪除該值。

 如需有關其他 SharePoint 登錄機碼的詳細資訊，請參閱 <<c0> [ 偵錯在 Visual Studio 中 SharePoint 工具擴充功能](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)。

## <a name="see-also"></a>另請參閱
- [SharePoint 方案進行疑難排解](../sharepoint/troubleshooting-sharepoint-solutions.md)
