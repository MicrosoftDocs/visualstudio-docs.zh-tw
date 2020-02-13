---
title: 移植、移轉和升級專案 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
caps.latest.revision: 108
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 3361b04900e549d037338abfba0911b232c9e1bd
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919095"
---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>移植、遷移及升級 Visual Studio 專案
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 的最新文件，請參閱 [Visual Studio 的專案移轉與升級參考](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)。

當您考慮是否應該移至較新版本的 Visual Studio 時，可以使用此文章來找出您在 Visual Studio 2013、Visual Studio 2012 或 Visual Studio 2010 SP1 所建立的哪些解決方案、專案、檔案與其他資產可不經修改而直接在 Visual Studio 2013 和 Visual Studio 2015 中執行。 或者，如果您嘗試開啟的專案不受開啟它的 Visual Studio 版本支援或是需要 SDK 或擴充功能 (例如 Azure SDK for .NET) 時發生錯誤訊息，則可能已到達此頁面。

許多廣泛使用的資產在 Visual Studio 2015、Visual Studio 2013 和兩個舊版中的行為都相同。 例如，在 Visual Studio 2015 中，您可以開啟在 Visual Studio 2013 或 Visual Studio 2012 中建立的專案、加以變更，然後在 Visual Studio 2015 中重新開啟。 您的變更會保存，而專案的行為與舊版相同。 這也適用於許多在 Visual Studio 2010 SP1 中建立的資產。

針對 Visual Basic，Visual Studio 2015 未引進任何會防止系統編譯在 Visual Studio 2013 中建立之 Visual Basic 應用程式的變更。 使用 Visual Studio 2015 重新編譯 Visual Basic 應用程式的執行階段行為將不會變更。

如果您將 Visual Studio 2015 與 Visual Studio 2013、Visual Studio 2012 或 Visual Studio 2010 SP1 一起使用，就可以使用這些版本其中任何一個建立和修改專案及檔案。 只要您未加入一或多個版本不支援的功能，您就可以在版本之間傳輸專案與檔案。

## <a name="project"></a> 專案

下列清單描述 Visual Studio 2015 與 Visual Studio 2013 中對在 Visual Studio 2012 或 Visual Studio 2010 SP1 中建立之專案的支援。 使用此清單可協助您判斷是否可以在 Visual Studio 2015、Visual Studio 2013、Visual Studio 2012 或 Visual Studio 2010 SP1 中以「原樣」開啟專案，或您是否必須加以修改以確保相容性。

|專案類型|相容性|
|---------------------|-------------------|
|通用 Windows 平台應用程式|若要安裝通用 Windows 應用程式工具，請在 Visual Studio 安裝程式中，選取 [自訂]  或 [修改]  ，然後選取 [通用 Windows 應用程式開發工具]  。<br /><br /> 只有在 Windows 10 或 [!INCLUDE[win81](../includes/win81-md.md)] 上的 Visual Studio 2015 中，才支援適用於 Windows 10 的通用 Windows 平台 (UWP) 應用程式開發。|
|Windows 市集應用程式|Windows 市集應用程式開發，包含以 Windows 8.1 和 Windows Phone 8.1 為目標的通用應用程式都受 [!INCLUDE[win81](../includes/win81-md.md)] 和 Windows 10 支援。 現有的 [!INCLUDE[win8](../includes/win8-md.md)] 專案可以繼續接收服務，但是無法建立新的 [!INCLUDE[win8](../includes/win8-md.md)] 專案。 [!INCLUDE[win81](../includes/win81-md.md)] 專案只能取決於特定的參考類型。 如需詳細資訊，請參閱[管理專案中的參考](../ide/managing-references-in-a-project.md)。 **注意：** 您使用 Visual Studio 2015 或 Visual Studio 2013 建立的 [!INCLUDE[win81](../includes/win81-md.md)] 專案無法在 Visual Studio 2012 中開啟。 這是因為使用 Visual Studio 2015 與 Visual Studio 2013 以那些版本與 Visual Studio 2012 為目標所建立的 [!INCLUDE[win81](../includes/win81-md.md)] 專案只支援以 [!INCLUDE[win8](../includes/win8-md.md)] 為目標的 [!INCLUDE[win8](../includes/win8-md.md)] 專案。|
|[!INCLUDE[net_v451](../includes/net-v451-md.md)]|在安裝適當的多目標套件之後，您可以在 Visual Studio 2015 和 Visual Studio 2013 中建立及使用這些專案。 Visual Studio 2010 SP1 不支援這些專案。|
|[!INCLUDE[net_v45](../includes/net-v45-md.md)]|您可以在 Visual Studio 2015、Visual Studio 2013 與 Visual Studio 2012 中建立及開啟這些專案，但無法在 Visual Studio 2010 SP1 中進行。|
|BizTalk|BizTalk Server 專案與 Visual Studio 2015 或 Visual Studio 2013 不相容。|
|C#/Visual Basic Silverlight 4 應用程式或類別庫|若您允許 Visual Studio 自動更新專案，您可以在 Visual Studio 2013 或 Visual Studio 2012 中開啟它。|
|C#/Visual Basic Webform 或 Windows Form|您可以在 Visual Studio 2013 和 Visual Studio 2012 中開啟專案。|
|Visual Basic 6 和 Visual C++ 6|Visual Studio 2012 和 Visual Studio 2013 不支援針對以 Visual Basic 6 或 Visual C++ 6 建立的應用程式進行偵錯；若要針對這些應用程式進行偵錯，請使用舊版的 Visual Studio。|
|自動程式碼 UI 測試|若您允許 Visual Studio 自動更新專案，您可以在 Visual Studio 2013、Visual Studio 2012 與 Visual Studio 2010 SP1 中開啟它。|
|F#|若您允許 Visual Studio 升級在 Visual Studio 2010 SP1 中建立的專案，您可以在 Visual Studio 2013 與 Visual Studio 2012 中加以開啟。 不過，您無法將以舊版 Visual Studio 建立的 Silverlight 專案升級到 Visual Studio 2013。 相反地，您必須在 Visual Studio 2013 中建立 Silverlight 專案，然後將您的程式碼複製到其中。 在 Visual Studio 2013 中建立的 Silverlight 專案會以 Silverlight 5 為目標。|
|LightSwitch|若您允許 Visual Studio 自動升級專案，您只能在 Visual Studio 2013 中加以開啟。|
|本機資料庫快取|[本機資料庫快取] 範本與 [設定資料同步處理]  對話方塊不包含在 Visual Studio 2013 中。 若已安裝 Microsoft 同步處理服務 v1.0，您可以使用 Visual Studio 2013 來開啟並執行在 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 中建立的專案，但若您想要在 Visual Studio 2013 中更新它們，您必須在程式碼中手動進行所有變更。 或者，您可以繼續使用 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 來維護和更新這些專案。  若要進行新開發，請以 Microsoft Sync Framework 提供的新同步處理模型為目標。 如需相關資訊，請參閱 [Microsoft Sync Framework Developer Center](https://msdn.microsoft.com/sync/default)(Microsoft Sync Framework 開發人員中心)|
|模型檢視控制器 (MVC) 架構|Visual Studio 2010 SP1 只支援 MVC 2 與 MVC 3、Visual Studio 2012 只支援 MVC 3 與 MVC 4，而 Visual Studio 2013 只支援 MVC 4。 如需關於如何從 MVC 2 自動升級到 MVC 3 的詳細資訊，請參閱 [ASP.NET MVC 3 Application Upgrader](https://aspnet.codeplex.com/releases/view/59008) (ASP.NET MVC 3 應用程式升級程式)。 如需關於如何從 MVC 2 手動升級至 MVC 3 的詳細資訊，請參閱 [Upgrading an ASP.NET MVC 2 Project to ASP.NET MVC 3 Tools Update](https://aspnet.codeplex.com/releases/view/59008)(將 ASP.NET MVC 2 專案升級至 ASP.NET MVC 3 工具更新)。 如需關於如何從 MVC 3 手動升級至 MVC 4 的詳細資訊，請參閱 [Upgrading an ASP.NET MVC 3 Project to ASP.NET MVC 4](/aspnet/whitepapers/mvc4-release-notes) (將 ASP.NET MVC 3 專案升級至 ASP.NET MVC 4)。 如果您的專案以 .NET Framework 3.5 SP1 為目標，專案必須重定目標為使用 .NET Framework 4。|
|模型化|如果您允許 Visual Studio 自動更新專案，則可以在 Visual Studio 2013、Visual Studio 2012 或 Visual Studio 2010 SP1 中開啟專案。<br /><br /> 當 Team Foundation 建置模型專案時，它會嘗試驗證專案中的各層。 在 Visual Studio 2013 中，Team Foundation Build 無法驗證在 Visual Studio 2010 SP1 中建立之模型專案的層級。 不過，在 Visual Studio 2010 SP1 中，Team Foundation Build 可以驗證在 Visual Studio 2013 中建立之模型專案的層級。|
|MPI/叢集偵錯|若執行 Visual Studio 2013、Visual Studio 2012 或 Visual Studio 2010 SP1 的電腦上已安裝相同版本的執行階段或工具，您可以在這三個版本中開啟此專案。|
|MSI 安裝程式 (.vdproj)|無法在 Visual Studio 2013 中開啟此專案，因為它不支援該專案類型。 我們建議您使用 InstallShield Limited Edition for Visual Studio (ISLE)，它是直接支援大部分 Windows 平台和應用程式執行階段的免費部署方案。 您也可以使用 ISLE 從 Visual Studio Installer 專案匯入資料和設定。 中修改就能執行。|
|Office 2007 VSTO|若您將專案升級為以 Office 2013 與 .NET Framework 4 為目標，您可以在 Visual Studio 2013、Visual Studio 2012 或 Visual Studio 2010 SP1 中開啟此專案。|
|Office 2010 VSTO|若專案以 .NET Framework 4 為目標，您可以在 Visual Studio 2013、Visual Studio 2012 與 Visual Studio 2010 SP1 中加以開啟。 所有其他專案則需要單向升級。|
|豐富網際網路應用程式|若您升級專案，您可以在 Visual Studio 2013、Visual Studio 2012 與 Visual Studio 2010 SP1 中加以開啟。|
|SharePoint 2007|無法在 Visual Studio 2013 中開啟此專案。 不過，若您手動將專案升級為 SharePoint 2010，您可以在 Visual Studio 2013、Visual Studio 2012 與 Visual Studio 2010 SP1 中加以開啟。 如需如何升級 SharePoint 2007 的詳細資訊，請參閱[從 SharePoint 2007 移轉到 SharePoint 2010 (IT 專業人士適用)](https://channel9.msdn.com/Blogs/matthijs/Migrating-from-SharePoint-2007-to-SharePoint-2010-for-the-IT-Pro) 和[適用於 SharePoint Server 2010 的 SharePoint 企業版搜尋移轉工具](/previous-versions/office/developer/sharepoint-2010/ee556856(v%3Doffice.14)) \(英文\)。|
|SharePoint 2010|您可以在 Visual Studio 2013、Visual Studio 2012 與 Visual Studio 2010 SP1 中開啟專案。|
|SketchFlow|若您允許 Visual Studio 將專案升級至 WPF 4.5/Silverlight 5，您可以在 Visual Studio 2012 與 Visual Studio 2013 中加以開啟。|
|[!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)] 資料庫|您可以在 Visual Studio 2013、Visual Studio 2012 與 Visual Studio 2010 SP1 中開啟專案。 如果您有舊版 SQL Server 建立的資料庫檔案 (.mdf)，則必須將其升級至 [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] ，才能搭配 SQL Server Express LocalDB 使用該資料庫檔案，但是該資料庫不再與舊版 SQL Server 相容。 若您不升級，您可以在同一部電腦上安裝並使用 [!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)]，以繼續在 Visual Studio 2013 中使用資料庫。 如需詳細資訊，請參閱[升級 .mdf 檔案](../data-tools/upgrade-dot-mdf-files.md)。|
|[!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] Express|若 [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] Express 安裝在執行 Visual Studio 2013、Visual Studio 2012 與 Visual Studio 2010 SP1 的電腦上，您可以在這三個版本中開啟專案。|
|SQL Server 報表專案|您可以在 Visual Studio 2013 和 Visual Studio 2012 中開啟專案。 對於本機模式 (也就是說，如果沒有連接至 SQL Server)，您將不會取得與 [!INCLUDE[vs2010](../includes/vs2010-md.md)]檢視器關聯之控制項的設計階段經驗，不過，但專案仍然可以正常運作於執行階段。 **注意：** 若您加入 Visual Studio 2013 特有的功能，報表架構會自動升級，而且您無法再於 Visual Studio 2012 中開啟專案。|
|單元測試|您可以使用 Visual Studio 2013、Visual Studio 2012 與 Visual Studio 2010 SP1 中的 [!INCLUDE[TCMext](../includes/tcmext-md.md)]，開啟在這些版本中所建立的測試。|
|Visual C++|您可以使用 Visual Studio 2013 開啟在 Visual Studio C++ 2012 或 Visual Studio 2010 SP1 中建立的專案。 若要使用 Visual Studio 2013 建置環境來建置在 Visual Studio 2012 中建立的專案，您必須在同一部電腦上安裝這兩個版本的 Visual Studio。 如需詳細資訊，請參閱[如何：將 Visual C++ 專案升級為 Visual Studio 2015](../porting/how-to-upgrade-visual-cpp-projects-to-visual-studio-2015.md) 和 [Visual C++ 移植和升級指南](https://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb)。|
|Visual Studio 2010 Web|若您允許 Visual Studio 自動升級專案，您可以在 Visual Studio 2013、Visual Studio 2012 與 Visual Studio 2010 SP1 中加以開啟。|
|Visual Studio 2010 資料庫 (.dbproj)|若您將專案轉換為 SQL Server Data Tools 資料庫專案，您可以在 Visual Studio 2013 中加以開啟。 不過，Visual Studio 2013 不支援下列成品：<br /><br /> -   單元測試<br />-   資料產生計劃<br />-   資料比較檔案<br />-   靜態程式碼分析的自訂規則延伸模組<br />-   server.sqlsettings<br />-   .sqlcmd 檔案<br />-   自訂部署延伸模組<br />-   部分專案 (.files)<br /><br /> 如果您已經安裝 SQL Server Data Tools，可以在轉換後使用 Visual Studio 2010 SP1 開啟專案。 如需詳細資訊，請參閱 [Microsoft SQL Server Data Tools](https://msdn.microsoft.com/data/tools.aspx)。|
|Visual Studio 2010 Visual Database Tools|您可以在 Visual Studio 2013、Visual Studio 2012 和 Visual Studio 2010 SP1 中開啟這類專案。|
|Visual Studio Lab Management|您可以使用 [!INCLUDE[TCMext](../includes/tcmext-md.md)]、Visual Studio 2013、Visual Studio 2012 與 Visual Studio 2010 SP1 來開啟在這些版本中建立的環境。 不過，Microsoft Test Manager 的版本必須符合 Team Foundation Server 的版本才能建立環境。|
|Visual Studio 巨集|無法在 Visual Studio 2013 中開啟此專案，因為它不支援此專案類型。|
|Visual Studio SDK/VSIX|將 Visual Studio SDK 專案升級為 Visual Studio 2013 之後，就無法在 Visual Studio 2012 中加以開啟。 如需詳細資訊，請參閱[如何：將擴充性專案移轉至 Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)。|
|Microsoft Azure Tools for Visual Studio|若您使用的是 Microsoft Azure Tools for Visual Studio 2.1 版，您可以在 Visual Studio 2013、Visual Studio 2012 與 Visual Studio 2010 SP1 中開啟專案。 針對以較早版本為目標的專案，若您允許 Visual Studio 將專案升級到 2.1 版，您可以在 Visual Studio 2013、Visual Studio 2012 與 Visual Studio 2010 SP1 中加以開啟。|
|Windows Communication Foundation、Windows Presentation Foundation|您可以在 Visual Studio 2013、Visual Studio 2012 和 Visual Studio 2010 SP1 中開啟這類專案。|
|Windows Mobile|無法在 Visual Studio 2013 中開啟此專案，因為它不支援此專案類型。|
|Windows Phone 7.1|若您允許 Visual Studio 將專案升級到 Windows Phone 8.0，您可以在 Visual Studio 2012 與 Visual Studio 2013 中加以開啟。|
|其他|您可以在 Visual Studio 2012、Visual Studio 2013 與 Visual Studio 2010 SP1 中開啟大部分其他類型的專案。|
|FrontPage 網站|無法在 Visual Studio 2013 中開啟此專案，因為它不支援此專案類型。|
|可攜式類別庫|如果您允許 Visual Studio 自動更新專案，則可以在 Visual Studio 2013、Visual Studio 2012 或 Visual Studio 2010 SP1 中開啟專案。<br /><br /> -   原先以 Silverlight 4 為目標的專案，將會以 Silverlight 5 為目標。<br />-   原先以 Windows Phone 7.0 或 Windows Phone 7.5 為目標的專案，將會以 Windows Phone 8 為目標。<br />-   以 Xbox 360 為目標的專案，不會再以 Xbox 360 為目標。|
|Azure 專案 (例如雲端服務專案 (副檔名 .ccproj)) 以及副檔名為 .deployproj 的 Azure 資源管理員專案 (雲端部署專案)|若要開啟這些類型的專案，請先安裝 [Azure SDK for .NET](https://azure.microsoft.com/downloads/)，然後再開啟專案。|

## <a name="troubleshooting-project-compatibility-issues"></a>疑難排解專案相容性問題
 以下是當專案無法在 Visual Studio 2015 或 Visual Studio 2013 中開啟時，您可以執行的一些動作：

- 若您嘗試開啟 Visual Studio 2015 或 Visual Studio 2013 不支援的專案，而且未安裝相關聯的 Visual Studio 版本，則可能會出現專案類型不受支援的訊息，而且專案類型可能會列在 [檢閱專案和方案變更]  對話方塊中的 [不支援的專案]  下。 若要解決這個問題，請開啟 Windows [ **控制台**] 的 [程式和功能] 頁面，選取 [ **Visual Studio**]，然後選擇 [ **變更**]、[ **修復**]。 然後您就可以安裝遺漏的版本。

- 若您嘗試在 [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] 中開啟傳統型應用程式的專案，會發生錯誤並顯示下列其中一個訊息：「此 Visual Studio 版本僅支援 [!INCLUDE[win81](../includes/win81-md.md)] 應用程式」或「此專案與目前的 Visual Studio 不相容。」 [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] 只能用於開發、測試和部署針對 Windows 8.1 所設計的 Windows 市集應用程式。 若要開啟桌面應用程式專案，您必須使用支援該專案類型的 Visual Studio 版本。

   如需 Visual Studio 版本的詳細資訊，請參閱 [Microsoft Visual Studio 產品](https://visualstudio.microsoft.com/products/)

- 如果您嘗試在 [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Desktop 中開啟 Windows 市集應用程式專案，會發生錯誤。 [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Desktop 不可用來建置 Windows 市集應用程式。 如果您想要建置 Windows 市集應用程式，您也可以安裝 [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)]。 或者，若要開發適用於所有 Microsoft 平台和 Web 的應用程式，請嘗試 Visual Studio Professional 2013。

- 若專案需要 Visual Studio 2013 特有的功能，就無法在舊版中加以開啟。

- 若您使用 Visual Studio 2012，而且想要開啟在 Visual Studio 2013 中建立的專案，您可能可以自訂專案系統以併入 Visual Studio 2013 的功能。 如需此作法的詳細資訊，請參閱[讓自訂專案成為版本感知](../misc/making-custom-projects-version-aware.md)。

  如需其他疑難排解資訊，請參閱 [Visual Studio 2013 相容性](https://support.microsoft.com/help/2863286/roundtrip-issues-for-visual-studio-2012-and-visual-studio-2013-preview) 知識庫文章。

## <a name="file"></a> 檔案

下列清單會識別 Visual Studio 2013 是否支援每種類型的檔案、是否可以在 Visual Studio 2012 與 Visual Studio 2010 SP1 中開啟檔案，以及是否必須加以修改以確保相容性。

|檔案類型|相容性|
|------------------|-------------------|
|AppManifest、Inbrowsersettings、OutOfBrowserSettings (.xml 檔案)|您可以在 Visual Studio 2012、Visual Studio 2013 與 Visual Studio 2010 SP1 中開啟這些檔案。|
|BizTalk 一般檔案結構描述|您可以在 Visual Studio 2013 中，將這些結構描述新增至 BizTalk 2013 專案。 若要搭配具有一般檔案結構描述的 BizTalk 2010 專案使用 Visual Studio 2013，請在已安裝 Visual Studio 2013 的電腦上安裝 BizTalk 2013。 當您第一次開啟 BizTalk 2010 專案時，它會自動升級為 BizTalk 2013 或 Visual Studio 2013 專案系統。|
|用戶端報表定義檔案 (.rdlc)|您可以在 Visual Studio 2013 中開啟這些檔案，若您加入 Visual Studio 2013 功能與控制項，則會自動升級結構描述。|
|程式碼分析規則集|您可以在 Visual Studio 2012、Visual Studio 2013 與 Visual Studio 2010 SP1 中開啟這些檔案。|
|資料層應用程式套件檔案|若這些檔案是 2.0 版或 2.5 版，您可以在 Visual Studio 2013 中開啟這些檔案。|
|偵錯工具傾印檔案|您可以在 Visual Studio 2012、Visual Studio 2013 與 Visual Studio 2010 SP1 中開啟這些檔案。|
|有向圖形標記語言 (DGML) 圖表檔案|您可以在 Visual Studio 2012、Visual Studio 2013 與 Visual Studio 2010 SP1 中開啟這些檔案，而不需要變更檔案。|
|實體資料模型 (EDMX) 檔案|在 Visual Studio 2013 中，您可以開啟以 .NET Framework 4.5 或 .NET Framework 4 為目標的 EDMX 檔案，而不需要變更檔案。|
|分析工具報告檔|您可以在 Visual Studio 2012 與 Visual Studio 2013 中開啟分析工具報告檔案 (.vsp、.vsps、.psess 與 .vspf)。 .vspx 檔案無法在 Visual Studio 2010 SP1 中開啟。|
|方案 (.suo) 檔案|您可以使用 Visual Studio 2013 開啟在 Visual Studio 2012 或 Visual Studio 2010 SP1 中建立的方案檔|
|SQL Server Compact Edition|Visual Studio 2013 不支援 SQL Server Compact Edition。|
|SQLX 檔案|若要在 Visual Studio 2013 中開啟這些檔案，您必須執行單向升級，在目標版本的 Visual Studio 上部署 .sqlx 檔案，然後以 .dacpac 格式重建檔案。|
|[!INCLUDE[vs2010](../includes/vs2010-md.md)] 的 IntelliTrace 記錄檔|您可以在 Visual Studio 2012、Visual Studio 2013 與 Visual Studio 2010 SP1 中開啟這些檔案。|
|JavaScript 記憶體分析器 (.diagsession) 檔案|您可以在 Visual Studio 2013 中檢視舊版 Visual Studio 所建立的檔案。 不過，視收集的資訊而定，在 Visual Studio 2013 中建立的檔案可能無法在 Visual Studio 2012 或 Visual Studio 2010 SP1 中開啟。|

## <a name="integration"></a> 整合資產

如果您的用戶端與伺服器使用不同版本的 Visual Studio Team Foundation Server，可能會遇到相容性問題。

|整合的類型|相容性|
|-------------------------|-------------------|
|程式碼檢閱和我的工作|如果您將 [!INCLUDE[esprfound](../includes/esprfound-md.md)] 的用戶端連接至 [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)]，將無法使用 [程式碼檢閱] 和 [我的工作] 功能。|
|[!INCLUDE[vs_dev11_expwin_long](../includes/vs-dev11-expwin-long-md.md)]|您無法使用 64 位元環境 (例如 MSBuild 或 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] ) 來建置您在 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 中建立的 [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)]應用程式。|

## <a name="see-also"></a>另請參閱

- [讓自訂專案成為版本感知](../misc/making-custom-projects-version-aware.md)
