---
title: 移植、 移轉及升級 Visual Studio 中的 Visual Studio 專案&quot;15&quot; RC |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.assetid: 3457b3ad-f9d6-4cb2-a346-f37326a28ffb
caps.latest.revision: 6
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 5d750364ba5fd953a5a4aa18252961bbbf968ba5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768915"
---
# <a name="port-migrate-and-upgrade-visual-studio-projects-in-visual-studio-quot15quot-rc"></a>移植、 移轉及升級 Visual Studio 中的 Visual Studio 專案&quot;15&quot; RC
當您移至較新版本的 Visual Studio 時，您會想要知道是否您必須修改任何解決方案、 專案、 檔案和其他您在中建立的資產[!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]， [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]，或[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]中執行之前[!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]或[!INCLUDE[vs_dev15_md](../includes/vs-dev15-md.md)]. 此頁面可協助您使用的。 

> [!NOTE]
>  可能會到達此頁面設定如果當您嘗試開啟開啟它，Visual Studio 版本不支援的專案時，您會收到一則錯誤訊息，或者是否需要 SDK 或擴充功能，例如 Azure SDK for.NET。 如果是的話，此頁面可協助您，太。
  
 許多廣泛使用的資產的行為在相同[!INCLUDE[vs_dev15_md](../includes/vs-dev15-md.md)]， [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]，與兩個舊版本。 例如，在 [!INCLUDE[vs_dev15_md](../includes/vs-dev15-md.md)]中，您可以開啟 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] 或 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]中建立的專案，將它變更，然後在 [!INCLUDE[vs_dev15_md](../includes/vs-dev15-md.md)]中重新開啟專案；您的變更會保存，而專案行為和在舊版中的行為相同。 這也適用於許多中所建立的資產[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]。  
  
 如果您使用[!INCLUDE[vs_dev15_md](../includes/vs-dev15-md.md)]連同[!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]，並[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]，或[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]，您可以建立並修改專案及任一版本中的檔案。 只要不加入其中一個版本不支援的功能，就可以在版本之間傳輸專案和檔案。  
  
##  <a name="project"></a> 專案  
 下列清單說明中的支援[!INCLUDE[vs_dev15_md](../includes/vs-dev15-md.md)]並[!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]中所建立的專案[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]或[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]。 您可以使用這份清單協助判斷是否可以開啟專案做為處於[!INCLUDE[vs_dev15_md](../includes/vs-dev15-md.md)]， [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]，或[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]，還是您擁有進行修改以確保相容。  
  
|專案類型|相容性|  
|---------------------|-------------------|  
|通用 Windows 平台應用程式|若要安裝通用 Windows 應用程式工具，請在 Visual Studio 安裝程式中，選取 [自訂]  或 [修改] ，然後選取 [通用 Windows 應用程式開發工具] 。<br /><br /> Windows 10 的通用 Windows 平台 (UWP) 應用程式只能在 Windows 10 或 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] 上的 [!INCLUDE[win81](../includes/win81-md.md)]受支援。|  
|Windows 市集應用程式|Windows 市集應用程式開發，包含以 Windows 8.1 和 Windows Phone 8.1 為目標的通用應用程式都受 [!INCLUDE[win81](../includes/win81-md.md)] 和 Windows 10 支援。 現有的 [!INCLUDE[win8](../includes/win8-md.md)] 專案可以繼續接收服務，但是無法建立新的 [!INCLUDE[win8](../includes/win8-md.md)] 專案。 [!INCLUDE[win81](../includes/win81-md.md)] 專案只能取決於特定的參考類型。 如需詳細資訊，請參閱[管理專案中的參考](../ide/managing-references-in-a-project.md)。 **注意：** [!INCLUDE[win81](../includes/win81-md.md)]使用您建立的專案[!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]或是[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]無法在開啟[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]。 這是因為使用 [!INCLUDE[win81](../includes/win81-md.md)] 和 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] 建立的 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 專案是以這些版本為目標，而且 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 僅支援目標設為 [!INCLUDE[win8](../includes/win8-md.md)] 的 [!INCLUDE[win8](../includes/win8-md.md)]專案。|  
|[!INCLUDE[net_v451](../includes/net-v451-md.md)]|安裝適當的多目標功能套件之後，您可以在 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] 和 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 中建立和使用這些專案。 Visual Studio 2010 SP1 不支援這些專案。|  
|[!INCLUDE[net_v45](../includes/net-v45-md.md)]|您可以在 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]、 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 和 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]中建立和開啟這些專案，但無法在 Visual Studio 2010 SP1 中這麼做。 如需詳細資訊，請參閱[移轉指南](http://msdn.microsoft.com/library/02d55147-9b3a-4557-a45f-fa936fadae3b)|  
|BizTalk|BizTalk 伺服器專案與 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] 或 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 不相容。|  
|C#/Visual Basic Silverlight 4 應用程式或類別庫|如果您允許 Visual Studio 自動更新專案，就可以在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 或 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 中開啟專案。|  
|C#/Visual Basic Webform 或 Windows Form|您可以在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 和 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 中開啟專案。|  
|Visual Basic 6 和 Visual C++ 6|Visual Studio 2012 和 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 不支援偵錯以 Visual Basic 6 或 Visual C++ 6 建置的應用程式；若要偵錯這些應用程式，請使用舊版 Visual Studio。|  
|自動程式碼 UI 測試|如果您允許 Visual Studio 自動更新專案，則可以在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 和 Visual Studio 2010 SP1 中開啟專案。|  
|F#|如果您允許 Visual Studio 升級 Visual Studio 2010 SP1 所建立的專案，則可以在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 和 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 中開啟專案。 不過，您無法將舊版 Visual Studio 建立的 Silverlight 專案升級至 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]。 相反地，您必須在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 中建立 Silverlight 專案，然後將程式碼複製到其中。 在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 中建立的 Silverlight 專案是以 Silverlight 5 為目標。|  
|LightSwitch|如果您允許 Visual Studio 自動升級專案，則只能在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 中開啟專案。|  
|本機資料庫快取|[本機資料庫快取] 範本和 [ **設定資料同步處理** ] 對話方塊不包含在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]中。 如果您已安裝 Microsoft Synchronization Services v1.0，就可以使用 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 來開啟和執行 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 所建立的專案。不過，如果您想要在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]中更新這些專案，則必須在程式碼中手動進行所有變更。 或者，您可以繼續使用 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 來維護和更新這些專案。  若要進行新開發，請以 Microsoft Sync Framework 提供的新同步處理模型為目標。 如需相關資訊，請參閱 [Microsoft Sync Framework Developer Center](http://msdn.microsoft.com/sync/default)(Microsoft Sync Framework 開發人員中心)|  
|模型檢視控制器 (MVC) 架構|Visual Studio 2010 SP1 只支援 MVC 2 和 MVC 3， [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 只支援 MVC 3 和 MVC 4，而 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 只支援 MVC 4。 如需關於如何從 MVC 2 自動升級到 MVC 3 的詳細資訊，請參閱 [ASP.NET MVC 3 Application Upgrader](http://go.microsoft.com/fwlink/?LinkID=238178) (ASP.NET MVC 3 應用程式升級程式)。 如需關於如何從 MVC 2 手動升級至 MVC 3 的詳細資訊，請參閱 [Upgrading an ASP.NET MVC 2 Project to ASP.NET MVC 3 Tools Update](http://go.microsoft.com/fwlink/?linkid=238178)(將 ASP.NET MVC 2 專案升級至 ASP.NET MVC 3 工具更新)。 如需關於如何從 MVC 3 手動升級至 MVC 4 的詳細資訊，請參閱 [Upgrading an ASP.NET MVC 3 Project to ASP.NET MVC 4](http://www.asp.net/whitepapers/mvc4-release-notes) (將 ASP.NET MVC 3 專案升級至 ASP.NET MVC 4)。 如果您的專案以 .NET Framework 3.5 SP1 為目標，專案必須重定目標為使用 .NET Framework 4。|  
|模型化|如果您允許 Visual Studio 自動更新專案，則可以在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 或 Visual Studio 2010 SP1 中開啟專案。<br /><br /> 當 Team Foundation 建置模型專案時，它會嘗試驗證專案中的各層。 在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 中，Team Foundation Build 無法驗證 Visual Studio 2010 SP1 中所建立模型專案的各層。 不過，在 Visual Studio 2010 SP1 中，Team Foundation Build 可以驗證在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 中建立的模型專案的各層。|  
|MPI/叢集偵錯|如果在執行 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 或 Visual Studio 2010 SP1 的電腦上有安裝相同版本的執行階段或工具，則在這三個版本的 Visual Studio 中都可以開啟這個專案。|  
|MSI 安裝程式 (.vdproj)|您無法在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 中開啟這個專案，因為它不支援該專案類型。 我們建議您使用 InstallShield Limited Edition for Visual Studio (ISLE)，它是直接支援大部分 Windows 平台和應用程式執行階段的免費部署方案。 您也可以使用 ISLE 從 Visual Studio Installer 專案匯入資料和設定。 中修改就能執行。|  
|Office 2007 VSTO|如果您升級專案，以 Office 2013 和 .NET Framework 4 為目標，則可以在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 或 Visual Studio 2010 SP1 中開啟這個專案。|  
|Office 2010 VSTO|如果專案是以 .NET Framework 4 為目標，您就可以在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 和 Visual Studio 2010 SP1 中開啟專案。 所有其他專案則需要單向升級。|  
|豐富網際網路應用程式|如果您升級專案，則可以在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 和 Visual Studio 2010 SP1 中開啟專案。|  
|SharePoint 2007|這個專案無法在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 中開啟。 不過，如果您手動升級專案至 SharePoint 2010，就可以在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]和 Visual Studio 2010 SP1 中開啟專案。 如需如何升級 SharePoint 2007 的詳細資訊，請參閱[從 SharePoint 2007 移轉至 SharePoint 2010 IT 專業人員](http://go.microsoft.com/fwlink/?LinkId=238224)，[將 2007年工作流程移轉到 Visual Studio 和 SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=238225)，及[SharePoint Server 2010 的 SharePoint Enterprise Search Migration Tool](http://go.microsoft.com/fwlink/?LinkId=238226)。|  
|SharePoint 2010|您可以在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 和 Visual Studio 2010 SP1 中開啟專案。|  
|SketchFlow|如果您允許 Visual Studio 升級專案至 WPF 4.5/Silverlight 5，則可以在 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 和 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 中開啟專案。|  
|[!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)] 資料庫|您可以在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 和 Visual Studio 2010 SP1 中開啟專案。 如果您有舊版 SQL Server 建立的資料庫檔案 (.mdf)，則必須將其升級至 [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)]，才能搭配 SQL Server Express LocalDB 使用該資料庫檔案，但是該資料庫不再與舊版 SQL Server 相容。 如果您不升級，則在同一台電腦上安裝和使用 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] ，就可以繼續在 [!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)] 中使用資料庫。 如需詳細資訊，請參閱 <<c0> [ 升級的.mdf 檔案](../data-tools/upgrade-dot-mdf-files.md)。|  
|[!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] Express|如果 [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] Express 是安裝在執行 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 和 Visual Studio 2010 SP1 的電腦上，則在這三個版本中都可以開啟專案。|  
|SQL Server 報表專案|您可以在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 和 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 中開啟專案。 對於本機模式 (也就是說，如果沒有連接至 SQL Server)，您將不會取得與 [!INCLUDE[vs2010](../includes/vs2010-md.md)]檢視器關聯之控制項的設計階段經驗，不過，但專案仍然可以正常運作於執行階段。 **注意：** 如果您加入功能特有[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]報表結構描述會自動升級，您無法再開啟中的專案[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]。|  
|單元測試|您可以在 [!INCLUDE[TCMext](../includes/tcmext-md.md)]、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 和 Visual Studio 2010 SP1 中使用 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]，來開啟任何這些版本所建立的測試。|  
|Visual C++|您可以使用 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 開啟在 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 或 Visual Studio 2010 SP1 中建立的 C++ 專案。 如果您想要使用 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 建置環境來建置 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]所建立的專案，則必須在同一台電腦上安裝這兩個版本的 Visual Studio。 如需詳細資訊，請參閱[如何：將 Visual C++ 專案升級為 Visual Studio 2015](../porting/how-to-upgrade-visual-cpp-projects-to-visual-studio-2015.md) 和 [Visual C++ 移植和升級指南](http://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb)。|  
|Visual Studio 2010 Web|如果您允許 Visual Studio 自動升級專案，則可以在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 和 Visual Studio 2010 SP1 中開啟專案。|  
|Visual Studio 2010 資料庫 (.dbproj)|如果您將專案轉換為 SQL Server Data Tools Database 專案，則可以在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 中開啟該專案。 不過， [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 不支援下列成品：<br /><br /> -單元測試<br />-資料產生計劃<br />-資料比較檔案<br />-靜態程式碼分析的自訂規則延伸模組<br />-server.sqlsettings<br />-.sqlcmd 檔案<br />-自訂部署擴充功能<br />-部分專案 (.files)<br /><br /> 如果您已經安裝 SQL Server Data Tools，可以在轉換後使用 Visual Studio 2010 SP1 開啟專案。 如需詳細資訊，請參閱 [Microsoft SQL Server Data Tools](http://msdn.microsoft.com/data/tools.aspx)。|  
|Visual Studio 2010 Visual Database Tools|您可以在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 和 Visual Studio 2010 SP1 中開啟這個專案。|  
|Visual Studio Lab Management|您可以使用 [!INCLUDE[TCMext](../includes/tcmext-md.md)]、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 和 Visual Studio 2010 SP1，來開啟任何這些版本所建立的環境。 不過，Microsoft Test Manager 的版本必須符合 Team Foundation Server 的版本才能建立環境。|  
|Visual Studio 巨集|您無法在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 中開啟這個專案，因為它不支援該專案類型。|  
|Visual Studio SDK/VSIX|將 Visual Studio SDK 專案升級至 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]之後，就無法在 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]中開啟該專案。 如需詳細資訊，請參閱 <<c0> [ 如何： 將擴充性專案移轉至 Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)。|  
|Microsoft Azure Tools for Visual Studio|如果您使用 Microsoft Azure Tools for Visual Studio 2.1 版，則可以在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 和 Visual Studio 2010 SP1 中開啟專案。 對於以舊版為目標的專案，如果您允許 Visual Studio 將專案升級到 2.1 版，您可以在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 和 Visual Studio 2010 SP1 開啟專案。|  
|Windows Communication Foundation、Windows Presentation Foundation|您可以在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 和 Visual Studio 2010 SP1 中開啟這個專案。|  
|Windows Mobile|您無法在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 中開啟這個專案，因為它不支援該專案類型。|  
|Windows Phone 7.1|如果您允許 Visual Studio 升級專案至 Windows Phone 8.0，則可以在 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 和 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 中開啟專案。|  
|其他|您可以在 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 和 Visual Studio 2010 SP1 中開啟大部分其他類型的專案。|  
|FrontPage 網站|您無法在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 中開啟這個專案，因為它不支援該專案類型。|  
|可攜式類別庫|如果您允許 Visual Studio 自動更新專案，則可以在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]、 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]或 Visual Studio 2010 SP1 中開啟專案。<br /><br /> -專案目標 Silverlight 4，將會以 Silverlight 5。<br />-Windows Phone 7.0 或 Windows Phone 7.5 為目標的專案會以 Windows Phone 8 為目標。<br />-專案，目標 Xbox 360 將不會再以 Xbox 360。|  
|Azure 專案 (例如雲端服務專案 (副檔名 .ccproj)) 以及副檔名為 .deployproj 的 Azure 資源管理員專案 (雲端部署專案)|若要開啟這些類型的專案，請先安裝 [Azure SDK for .NET](http://azure.microsoft.com/en-us/downloads/)，然後再開啟專案。|  
  
## <a name="troubleshooting-project-compatibility-issues"></a>疑難排解專案相容性問題  
 當專案在 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] 或 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]中不會開啟時，可執行的某些作業如下：  
  
- 如果您嘗試開啟 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] 或 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 不支援的專案，而且相關聯的 Visual Studio 版本也未安裝，則可能會出現專案類型不支援的訊息，並且 [不支援的專案]  底下的 [檢閱專案和方案變更] 對話方塊可能會顯示專案類型。 若要解決這個問題，請開啟 Windows [ **控制台**] 的 [程式和功能] 頁面，選取 [ **Visual Studio**]，然後選擇 [ **變更**]、[ **修復**]。 然後您就可以安裝遺漏的版本。  
  
- 如果您嘗試在 [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] 中開啟桌面應用程式的專案，將會發生錯誤並顯示下列其中一個訊息：「這個版本的 Visual Studio 僅支援 [!INCLUDE[win81](../includes/win81-md.md)] 應用程式」或「這個專案與目前的 Visual Studio 版本不相容」。 [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] 只能用於開發、測試和部署針對 Windows 8.1 所設計的 Windows 市集應用程式。 若要開啟桌面應用程式專案，您必須使用支援該專案類型的 Visual Studio 版本。  
  
   如需 Visual Studio 版本的詳細資訊，請參閱 [Microsoft Visual Studio 產品](http://go.microsoft.com/fwlink/?LinkId=254332)  
  
- 如果您嘗試在 [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Desktop 中開啟 Windows 市集應用程式專案，會發生錯誤。 [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Desktop 不可用來建置 Windows 市集應用程式。 如果您想要建置 Windows 市集應用程式，您也可以安裝 [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)]。 或者，若要開發適用於所有 Microsoft 平台和 Web 的應用程式，請嘗試 Visual Studio Professional 2013。  
  
- 如果專案需要 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 的專用功能，則專案無法在較舊版本中開啟。  
  
- 如果您使用的是 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] ，而您想要開啟 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]所建立的專案時，您或許可以自訂專案系統，將 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]的功能併入。 如需如何執行這項操作的資訊，請參閱[讓自訂專案版本感知](../misc/making-custom-projects-version-aware.md)。  
  
  如需其他疑難排解資訊，請參閱 [Visual Studio 2013 相容性](http://support.microsoft.com/kb/2863286) 知識庫文章。  
  
##  <a name="file"></a> 檔案  
 下列清單列出 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 是否支援每個檔案類型，是否可以同時在 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 和 Visual Studio 2010 SP1 中開啟檔案，以及是否必須進行修改以確保相容性。  
  
|檔案類型|相容性|  
|------------------|-------------------|  
|AppManifest、Inbrowsersettings、OutOfBrowserSettings (.xml 檔案)|您可以在 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 和 Visual Studio 2010 SP1 中開啟這些檔案。|  
|BizTalk 一般檔案結構描述|您可以在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 中將這些結構描述加入至 BizTalk 2013 專案。 若要搭配有一般檔案結構描述的 BizTalk 2010 專案使用 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]，請在具有 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 的電腦上安裝 BizTalk 2013。 第一次開啟 BizTalk 2010 專案時，會自動升級為 BizTalk 2013 或 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 專案系統。|  
|用戶端報表定義檔案 (.rdlc)|您可以在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 中開啟這些檔案，而結構描述會在您加入 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 功能和控制項時自動升級。|  
|程式碼分析規則集|您可以在 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 和 Visual Studio 2010 SP1 中開啟這些檔案。|  
|資料層應用程式套件檔案|如果是 2.0 版或 2.5 版，您可以在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 中開啟這些檔案。|  
|偵錯工具傾印檔案|您可以在 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 和 Visual Studio 2010 SP1 中開啟這些檔案。|  
|有向圖形標記語言 (DGML) 圖表檔案|您可以在不變更檔案的情況下，在 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 和 Visual Studio 2010 SP1 開啟檔案。|  
|實體資料模型 (EDMX) 檔案|在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 中，您可以開啟目標設定為 .NET Framework 4.5 或 .NET Framework 4 的 EDMX 檔案，而不需要變更檔案。|  
|分析工具報告檔|您可以在 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 和 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 中開啟分析工具報告檔 (.vsp、.vsps、.psess 和 .vspf)。 .vspx 檔案無法在 Visual Studio 2010 SP1 中開啟。|  
|方案 (.suo) 檔案|您可以使用 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 開啟在 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 或 Visual Studio 2010 SP1 中建立的方案檔。|  
|SQL Server Compact Edition|[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 不支援 SQL Server Compact Edition。|  
|SQLX 檔案|若要在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 中開啟這些檔案，您必須執行單向升級，將 .sqlx 檔案部署在 Visual Studio 目標版本上，然後以 .dacpac 格式重新建置檔案。|  
|[!INCLUDE[vs2010](../includes/vs2010-md.md)] 的 IntelliTrace 記錄檔|您可以在 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]、[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 和 Visual Studio 2010 SP1 中開啟這些檔案。|  
|JavaScript 記憶體分析器 (.diagsession) 檔案|Visual Studio 舊版建立的檔案可以在 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 中檢視。 不過，根據收集的資訊，用 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 建立的檔案可能不會在 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 或 Visual Studio 2010 SP1 中開啟。|  
  
##  <a name="integration"></a> 整合資產  
 如果您的用戶端與伺服器使用不同版本的 Visual Studio Team Foundation Server，可能會遇到相容性問題。  
  
|整合的類型|相容性|  
|-------------------------|-------------------|  
|程式碼檢閱和我的工作|如果您將 [!INCLUDE[esprfound](../includes/esprfound-md.md)] 的用戶端連接至 [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)]，將無法使用 [程式碼檢閱] 和 [我的工作] 功能。|  
|[!INCLUDE[vs_dev11_expwin_long](../includes/vs-dev11-expwin-long-md.md)]|您無法使用 64 位元環境 (例如 MSBuild 或 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] ) 來建置您在 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 中建立的 [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)]應用程式。|  
  
## <a name="see-also"></a>另請參閱  
 [讓自訂專案成為版本感知](../misc/making-custom-projects-version-aware.md)


  
