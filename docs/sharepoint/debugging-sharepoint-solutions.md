---
title: "偵錯 SharePoint 方案 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.WebConfigModificationDialog
- VS.SharePointTools.Project.DebuggingNotEnabled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 85317332cd6b142bb8e0e916e3d7ac80e4aa836c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="debugging-sharepoint-solutions"></a>對 SharePoint 方案進行偵錯
  您可以使用偵錯 SharePoint 方案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]偵錯工具。 當您開始偵錯，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]將專案檔案部署到 SharePoint 伺服器，然後開啟網頁瀏覽器中的 SharePoint 網站的執行個體。 下列各節將說明如何偵錯 SharePoint 應用程式[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
-   [啟用偵錯](#EnableDebug)  
  
-   [F5 偵錯和部署程序](#Deployment)  
  
-   [SharePoint 專案功能](#Features)  
  
-   [偵錯工作流程](#Workflow)  
  
-   [偵錯功能事件接收器](#FeatureEvents)  
  
-   [啟用增強型偵錯資訊](#EnhancedDebug)  
  
##  <a name="EnableDebug"></a>啟用偵錯  
 當您第一次偵錯 SharePoint 方案中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，對話方塊會警示您的 web.config 檔案未設定以啟用偵錯。 （當您安裝 SharePoint server 時，會建立 web.config 檔案。 如需詳細資訊，請參閱[使用 Web.config 檔案](http://go.microsoft.com/fwlink/?LinkID=149266)。)對話方塊可讓您選擇任一個執行專案，偵錯，或修改的 web.config 檔案，以啟用偵錯。 如果您選擇第一個選項，專案將會正常執行。 如果您選擇第二個選項，則 web.config 檔案會設定為：  
  
-   開啟 呼叫堆疊 (`CallStack="true"`)  
  
-   停用中的自訂錯誤[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)](`<customErrors mode="Off" />`)  
  
-   啟用偵錯編譯 (`<compilation debug="true">`)  
  
 產生的 web.config 檔案如下：  
  
```  
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
  
 若要反轉所做的變更，並停用偵錯，變更下列[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]web.config 檔案中：  
  
-   關閉 呼叫堆疊 (`CallStack="false"`)  
  
-   啟用自訂錯誤[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)](`<customErrors mode="On" />`)  
  
-   停用編譯偵錯 (`<compilation debug="false">`)  
  
##  <a name="Deployment"></a>F5 偵錯和部署程序  
 當您在偵錯模式執行您的 SharePoint 專案時，SharePoint 部署程序會執行下列工作：  
  
1.  執行可自訂的預先部署命令。  
  
2.  建立 Web 方案套件 (.wsp) 檔案使用[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]命令。 .Wsp 檔案包含的所有必要的檔案和功能。 如需詳細資訊，請參閱[方案概觀](http://go.microsoft.com/fwlink/?LinkID=128154)。  
  
3.  如果伺服器陣列方案為 SharePoint 方案，回收[!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]指定的站台的應用程式集區[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]。 此步驟中釋放鎖定的檔案[!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]背景工作處理序。  
  
4.  如果先前的版本的套件已經存在，撤銷舊版本的.wsp 檔案中的功能。 此步驟會停用功能、 解除安裝方案的套件，然後再刪除 SharePoint 伺服器上的方案套件。  
  
5.  安裝.wsp 檔案中的目前版本的檔案的功能。 此步驟新增，並在 SharePoint 伺服器上安裝方案。  
  
6.  工作流程，會安裝工作流程組件。 您可以使用，以變更其位置*組件位置*屬性。  
  
7.  如果範圍是網站或網頁，請啟動 SharePoint 專案的功能。 未啟用的伺服器陣列和 WebApplication 範圍中的功能。  
  
8.  工作流程，將工作流程與 SharePoint 文件庫、 清單中或您在選取的站台**SharePoint 自訂精靈**。  
  
    > [!NOTE]  
    >  只有當您選取，就會發生此關聯**自動關聯工作流程**精靈中。  
  
9. 執行可自訂的部署後命令。  
  
10. 將 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 偵錯工具附加至 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 處理序 (w3wp.exe)。 如果專案類型可讓您變更*沙箱化方案*屬性和其值設定為**true**，偵錯工具會附加至不同的處理序 (SPUCWorkerProcess.exe)。 如需詳細資訊，請參閱[沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)。  
  
11. 如果 SharePoint 方案的伺服器陣列方案，請啟動 JavaScript 偵錯工具。  
  
12. 在 Web 瀏覽器中顯示適當的程式庫、 清單或網站頁面。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]每個工作完成後，請在 [輸出] 視窗中顯示狀態訊息。 如果無法完成工作， [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] [錯誤清單] 視窗中顯示的錯誤訊息。  
  
##  <a name="Features"></a>SharePoint 專案功能  
 功能是功能的可攜性和模組化單位，簡化修改站台使用站台定義。 它也是一個封裝的[!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)](WSS) 項目，可以啟用用於特定範圍，這樣可以協助您完成特定目標或工作的使用者。 範本會部署為功能。  
  
 當您在偵錯模式中執行專案時，部署程序會建立在資料夾*功能*在 %COMMONPROGRAMFILES%\Microsoft Shared\web server extensions\14\TEMPLATE\FEATURES 目錄。 功能名稱的格式*專案名稱*_Feature*x*，例如 TestProject_Feature1。  
  
 功能目錄中的方案的資料夾包含*功能定義*檔案和*工作流程定義*檔案。 功能的定義檔 （這個） 描述的檔案中的專案功能專案定義檔案 (Elements.xml) 描述的專案範本。 位於 Elements.xml**方案總管 中**，但是建立方案套件時，會產生這個。 如需有關這些檔案的詳細資訊，請參閱[SharePoint 專案與專案項目範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。  
  
##  <a name="Workflow"></a>偵錯工作流程  
 當您偵錯工作流程專案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]文件庫或清單加入工作流程範本 （取決於其類型）。 您可以開始將工作流程範本或藉由手動新增或更新項目。 然後您可以使用[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]偵錯工作流程。  
  
> [!NOTE]  
>  如果您加入其他組件的參考，請確定這些組件安裝在全域組件快取中 ([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)])。 否則，工作流程方案將會失敗。 如需如何安裝組件資訊，請參閱[手動啟動工作流程上的文件或項目](http://go.microsoft.com/fwlink/?LinkID=79938)。  
  
 不過，部署程序無法啟動工作流程。 您必須從 SharePoint 網站啟動工作流程。 使用 Microsoft Office Word 2010 中，用戶端應用程式，或使用不同的伺服器端程式碼，您也可以啟動工作流程。 使用其中一種方法中指定**SharePoint 自訂精靈**。  
  
 例如，如果您指定可以手動啟動工作流程，請直接從程式庫或清單中的項目啟動工作流程。 如需如何以手動方式啟動工作流程的詳細資訊，請參閱[手動啟動工作流程上的文件項目](http://go.microsoft.com/fwlink/?LinkID=79938)。  
  
##  <a name="FeatureEvents"></a>偵錯功能事件接收器  
 根據預設，當您執行[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 應用程式，其功能時會自動為您啟用 SharePoint 伺服器上。 不過，這會造成問題時進行偵錯功能事件接收器，因為當啟動功能[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，它會比偵錯工具在不同處理序中執行。 這表示，某些偵錯功能，例如中斷點，將無法正常運作。  
  
 若要停用自動啟用 SharePoint 中的功能，並允許適當偵錯功能事件接收器，將專案值**現用部署組態**屬性**無啟用**之前偵錯。 接著，您在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中開始對 SharePoint 應用程式進行偵錯之後，請手動啟用 SharePoint 中的功能。 若要啟用的功能，請開啟**網站動作**功能表在 SharePoint 中，選擇 **站台設定**，選擇**管理網站功能**連結，，然後選擇  **Activate**繼續偵錯正常功能旁的按鈕。  
  
##  <a name="EnhancedDebug"></a>啟用增強型偵錯資訊  
 由於之間有時複雜的互動[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]程序 (devenv.exe)， [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 主機處理序 (vssphost4.exe)、 SharePoint 和 WCF 層，可以是診斷建置、 部署和其他等等時，會發生的錯誤挑戰。 為了協助您解決這類錯誤，您可以啟用增強型偵錯資訊。 若要這樣做，請移至下列登錄機碼，在 Windows 登錄中：  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools]  
  
 如果"EnableDiagnostics" **REG_DWORD**值不存在，請以手動方式建立它。 將"EnableDiagnostics"值設為"1"。  
  
 此索引鍵的值設定為 1 的原因堆疊追蹤資訊會出現在**輸出**視窗執行時，專案系統錯誤發生時[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 若要停用增強型偵錯資訊，請將 EnableDiagnostics 設定回 0，或刪除該值。  
  
 如需有關其他 SharePoint 登錄機碼的詳細資訊，請參閱[偵錯 Visual Studio 中 SharePoint 工具的延伸模組](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>請參閱  
 [針對 SharePoint 方案進行疑難排解](../sharepoint/troubleshooting-sharepoint-solutions.md)  
  
  