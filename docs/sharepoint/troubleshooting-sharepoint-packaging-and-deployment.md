---
title: SharePoint 封裝和部署疑難排解 |Microsoft 文件
ms.custom: ''
ms.date: 02/22/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.WorkflowDeployment.Troubleshooting
- VS.SharePointTools.Project.PackageRetraction
- VS.SharePointTools.Deployment.Troubleshooting
- VS.SharePointTools.Deploying.Troubleshooting
- VS.SharePointTools.Project.DeploymentTroubleshooting
- VS.SharePointTools.Project.SharePointNotInstalled
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
- SharePoint development in Visual Studio, troubleshooting
- SharePoint development in Visual Studio, deployment conflict resolution
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 22487077a355d51725258f37c03e5fd2bb58ab9b
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
---
# <a name="troubleshooting-sharepoint-packaging-and-deployment"></a>SharePoint 封裝和部署疑難排解
  這個主題涵蓋您在封裝和部署 SharePoint 方案時可能會遇到的各種問題。

## <a name="enabling-enhanced-debugging"></a>啟用增強型偵錯
 若要在 Visual Studio、SharePoint 和其他圖層之間進行診斷，您可以使用 EnableDiagnostics 登錄機碼來檢視堆疊追蹤。 如需詳細資訊，請參閱[偵錯 SharePoint 方案](../sharepoint/debugging-sharepoint-solutions.md)。

## <a name="adding-project-output-to-the-solution-package"></a>將專案輸出加入至方案套件
 您可以透過 [封裝設計工具] 將專案輸出加入至套件。 然而，當您加入專案輸出時，要確定專案的平台與 SharePoint 方案的平台相符。 我們建議您改用**任何 CPU**平台目標，您想要部署到 SharePoint 伺服器之組件。 如需詳細資訊，請參閱[專案設計工具、 編譯頁&#40;Visual Basic&#41; ](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)和[進階編譯器設定對話方塊&#40;Visual Basic&#41;](/visualstudio/ide/reference/advanced-compiler-settings-dialog-box-visual-basic)。

## <a name="validation-warnings-and-errors"></a>驗證警告和錯誤
 Visual Studio 中的 SharePoint 開發工具會執行驗證步驟，來驗證方案套件的格式是否正確。 您也可以為您的「功能」和套件建立自訂驗證步驟。 如需詳細資訊，請參閱[How to： 建立自訂功能和封裝驗證規則，SharePoint 方案的](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)。

## <a name="deployment-conflict-resolution"></a>部署衝突解決
 當您部署 SharePoint 方案時，可能會在伺服器上項目與方案套件中項目具有相同名稱、URL 或 ID 的情況中發現衝突。 您可以變更**部署衝突解決**屬性來解決、 報告或忽略模組、 Web 組件、 清單執行個體和內容類型的衝突。

 下表示範的設定**部署衝突解決**屬性。

|值|描述|
|-----------|-----------------|
|自動|偵測到衝突並自動解決衝突。|
|提示|偵測到衝突，並在解決衝突之前將其報告給開發人員。|
|無|未偵測到衝突。|

## <a name="differences-between-f5-deployment"></a>F5 部署之間的差異
 當您使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將 SharePoint 專案部署至本機 SharePoint 伺服器來進行測試和偵錯時，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 還會執行一些額外步驟。

1.  部署步驟期間重設「網際網路資訊服務」(IIS)。

2.  自動關聯工作流程。

3.  根據 [封裝設計工具] 中的階層，設定功能啟動順序。

 您可以加入自訂部署步驟，來進一步變更 F5 行為。 如需詳細資訊，請參閱[逐步解說： 建立 SharePoint 專案的自訂部署步驟](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)。

## <a name="delay-displaying-sharepoint-page-when-deploying-visual-web-part"></a>部署視覺 Web 組件時延遲顯示 SharePoint 頁面
 將視覺 Web 組件部署至 [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)]、[!INCLUDE[win7](../sharepoint/includes/win7-md.md)] 或 [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] 上的 Bin 資料夾時，會花費很長時間才會出現 SharePoint 頁面。 如果您變更最上層 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 目錄 (例如，Bin 目錄) 中的任何檔案，則會重新編譯整個 Web 應用程式。 這樣會導致 SharePoint 頁面的呈現存在長達 25 秒的延遲。

### <a name="error-message"></a>錯誤訊息
 無。

### <a name="resolution"></a>解決方式
 若要解決這個問題，請執行下列步驟：

1.  Microsoft 支援文章中所述，安裝更新 KB967535[修正： hotfix 可修正的兩個問題 ASP.NET 在 IIS 7.0 上的 Windows Vista 和 Windows Server 2008](http://go.microsoft.com/fwlink/?LinkId=179055)。

2.  將下列行加入至 Web.config 檔案：

    ```xml
    <compilation batch="false" optimizeCompilations="true">
    ```

## <a name="sharepoint-project-deployment-fails-with-error-failed-to-extract-the-cab-file-in-the-solution"></a>SharePoint 專案部署因「無法擷取方案中的封包檔」錯誤而失敗
 如果有任何 SharePoint 專案項目的名稱中包含括號，其方案的部署即會因錯誤而失敗。

### <a name="error-message"></a>錯誤訊息
 部署步驟「加入方案」中發生錯誤：無法擷取方案中的封包檔。

### <a name="resolution"></a>解決方式
 若要解決這個問題，請移除 SharePoint 專案項目名稱中的括號。

## <a name="error-appears-when-deploying-a-visual-web-part-to-a-site-on-a-different-web-application"></a>在不同 Web 應用程式上將視覺 Web 組件部署至網站時，出現錯誤
 當您第一次在非目前用來進行部署的 Web 應用程式上將視覺 Web 組件部署至網站時 (藉由變更視覺 Web 組件的 SiteUrl 屬性)，會出現錯誤。

### <a name="error-message"></a>錯誤訊息
 部署步驟「加入方案」中發生錯誤：識別碼為 [#] 的功能已經安裝在此伺服器陣列中。 請使用強制屬性明確重新安裝功能。

### <a name="resolution"></a>解決方式
 這個錯誤是由於在 SharePoint 中撤銷視覺 Web 組件功能的方式不當所致。 若要成功部署視覺 Web 組件，請選擇 F5 鍵重新部署方案。

## <a name="warning-appears-when-deploying-nested-user-controls"></a>當部署巢狀使用者控制項時出現警告
 當您部署具有巢狀使用者控制項 (例如包含使用者控制項的視覺 Web 組件或是包含視覺 Web 組件或另一個使用者控制項的使用者控制項) 的 SharePoint 方案時，將會發生這個警告。 會發生這個警告是否您將控制項加入設計工具將它從 [工具箱] 拖曳或使用@Register來源檢視中的指示詞。

### <a name="error-message"></a>錯誤訊息
 警告 1 元素 ' [*控制項名稱*]' 不是已知的項目。 當網站中發生編譯錯誤或 web.config 檔案遺失時，就會發生這個狀況。

### <a name="resolution"></a>解決方式
 如果[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]專案系統並不知道巢狀的使用者控制項，它無法提供 IntelliSense 而且會發出警告。 專案系統不會感知巢狀的使用者控制項的如果無法建置專案而且設計工具並未關閉及重新開啟，或者自動撤銷選項已啟用，讓使用者控制偵錯後，從 SharePoint 登錄區撤銷。

 若要移除這項警告，請建置專案，然後關閉設計工具再重新開啟，或者停用專案的自動撤銷選項。 若要這樣做，請清除**偵錯後自動撤銷** 核取方塊**SharePoint**  索引標籤的 專案屬性 對話方塊。

## <a name="see-also"></a>另請參閱
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)


