---
title: 移植、移轉及升級專案
description: 支援在目前版本和舊版 Visual Studio 中建立之專案的參考。
ms.date: 11/26/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload: multiple
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
ms.openlocfilehash: 8182f8982734bd0089d483c9acefc230c9baaa91
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901325"
---
# <a name="project-migration-and-upgrade-reference-for-visual-studio"></a>Visual Studio 的專案移轉與升級參考

::: moniker range="vs-2017"

Visual Studio 的每個版本一般都支援大部分先前的專案、檔案及其他資產類型。 您可以 [像往常一樣](../ide/solutions-and-projects-in-visual-studio.md)地使用它們，而且如果您不依賴較新的功能，Visual Studio 會嘗試保留與舊版的回溯相容性，例如 Visual Studio 2015、Visual Studio 2013 和 Visual Studio 2012。 (請參閱[版本資訊](/visualstudio/releasenotes/vs2017-relnotes/)，以了解哪些功能專屬於哪一個版本)。

有些專案類型的支援也會隨時間而改變。 新版的 Visual Studio 可能完全不再支援某些專案，或者需要更新專案，使它們不再具有回溯相容性。 如需移轉問題的目前狀態，請參閱 [Visual Studio Developer Community 網站](https://aka.ms/feedback/suggest?space=8)。

本文僅提供 Visual Studio 2017 能移轉之專案類型的詳細資料。 文中不包含 Visual Studio 2017 中不再支援，因此無法移轉的專案類型。 文中也不包含沒有移轉問題的已支援專案類型；該清單位於 [Visual Studio 2017 平台目標及相容性](/visualstudio/productinfo/vs2017-compatibility-vs)中。

> [!IMPORTANT]
> 特定專案類型需要透過 Visual Studio 安裝程式安裝適當的工作負載。 如果您未安裝工作負載，Visual Studio 會回報未知或不相容的專案類型。 在該情況下，請檢查您的安裝選項，然後再試一次。 同樣地，如需 Visual Studio 2017 中專案支援的詳細資料，請參閱 [Visual Studio 2017 平台目標及相容性](/visualstudio/productinfo/vs2017-compatibility-vs)一文。

## <a name="project-types"></a>專案類型

下列清單描述 Visual Studio 2017 對使用舊版建立之專案的支援。

如果您看不到應於此處列出的專案或檔案類型，請參閱[本文的 Visual Studio 2015 版本](/previous-versions/visualstudio/visual-studio-2015/porting/porting-migrating-and-upgrading-visual-studio-projects?preserve-view=true&view=vs-2015)，使用本頁底部的 [Send feedback about > This page] \(傳送關於本頁的意見反應\) 選項，提供您專案的詳細資料。 (如果您使用匿名的「本頁對您有幫助嗎？」 控制項，我們將無法回應您的意見反應。)

| 專案類型 | 支援 |
| --- | --- |
| .NET Core 專案 (xproj) | 以 Visual Studio 2015 建立的專案所使用的預覽工具，包含 xproj 專案檔。 在 Visual Studio 2017 中，除了遷移至 .csproj 格式以外，不支援 xproj 格式。 當您開啟 xproj 檔案時，系統會提示您將檔案遷移至 SDK 樣式的 .csproj 格式。  (建立 xproj 檔案的備份。 Visual Studio 2015 及更早版本不支援 ) SDK 樣式的 .csproj 專案。 如需詳細資訊，請參閱將 [.Net Core 專案遷移至 .csproj 格式](/dotnet/core/migration/#visual-studio)。|
| 已啟用 Application Insights 的 ASP.NET Web 應用程式和 ASP.NET Core Web 應用程式 | 對每位 Visual Studio 使用者來說，資源資訊會儲存在每個使用者執行個體的登錄中。 當使用者未開啟任何專案，而要搜尋 Azure Application Insights 資料時，就會使用此資訊。 Visual Studio 2015 使用的登錄位置和 Visual Studio 2017 不同，因此不會產生衝突。<br/><br/>在使用者建立 ASP.NET Web 應用程式或 ASP.NET Core Web 應用程式之後，資源就會存放在 .suo 檔案中。 只要 Visual Studio 支援在 Visual Studio 2015 和 Visual Studio 2017 中使用專案和解決方案，使用者即可在這兩個版本中開啟專案，資源資訊亦可用於這兩個版本。 使用者必須在每個產品上進行一次驗證。 例如，如果專案是以 Visual Studio 2015 建立並在 Visual Studio 2017 中開啟，則使用者也需要在 Visual Studio 2017 上進行驗證。 |
| C#/Visual Basic Webform 或 Windows Form | 您可以在 Visual Studio 2017 和 Visual Studio 2015 中開啟專案。 |
| 資料庫單元測試專案 (csproj、vbproj) | Visual Studio 2017 可以載入舊版的資料單元測試專案，但會使用 GAC 版本的相依性。 若要升級單元測試專案以使用最新的相依性，請以滑鼠右鍵按一下方案總管，並選取 [轉換成 SQL Server 單元測試專案...]。 |
| F# | Visual Studio 2017 可以開啟在 Visual Studio 2013 和 Visual Studio 2015 中建立的專案。 不過，若要在這些專案中啟用 Visual Studio 2017 的功能，請開啟專案屬性，並將目標 fsharp.core 變更為 F# 4.1。 另請注意，如果是 .NET 工作負載，則預設不會選取 Visual Studio 安裝程式中的 [F# 語言支援] 選項；您必須包括它，方法是針對工作負載選取該選項，或從 [開發活動] 的 [個別元件] 索引標籤中選取它。 |
| InstallShield<br/>MSI 安裝程式 | 在 Visual Studio 2010 中建立的安裝程式專案，可以透過 [Visual Studio Installer Projects extension](https://marketplace.visualstudio.com/items?itemName=UnniRavindranathan-MSFT.MicrosoftVisualStudio2013InstallerProjects) (Visual Studio 安裝程式專案延伸模組) 的協助在較新版本中開啟。 另請參閱 [WiX Toolset Visual Studio 2017 Extension](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension) (WiX 工具組 Visual Studio 2017 延伸模組)。 Visual Studio 不再隨附 InstallShield 限量版。 如需 Visual Studio 2017 的可用性，請參閱 [Flexera Software](https://info.flexerasoftware.com/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio)。 |
| LightSwitch | Visual Studio 2017 不再支援 LightSwitch。 在 Visual Studio 2013 或 Visual Studio 2015 中，如果開啟使用 Visual Studio 2012 和更早版本所建立的專案，系統會將該專案升級，並僅可在 Visual Studio 2013 或 Visual Studio 2015 之後的版本中開啟。 |
| Microsoft Azure Tools for Visual Studio | 若要開啟這些類型的專案，請先安裝 [Azure SDK for .NET](https://azure.microsoft.com/downloads/)，然後再開啟專案。 如有必要，系統會更新您的專案。 |
| 模型檢視控制器架構 (ASP.NET MVC) | 針對 MVC 版本和 Visual Studio 的支援：<ul><li>Visual Studio 2010 SP1 支援 MVC 2 和 MVC 3；您可透過 [ASP.NET 4 MVC 4 for Visual Studio 2010 SP1 下載](https://www.microsoft.com/download/details.aspx?id=30683)來新增 MVC 4 的支援</li><li>Visual Studio 2012 只支援 MVC 3 和 MVC 4</li><li>Visual Studio 2013 只支援 MVC 4 和 MVC 5</li><li>Visual Studio 2017 和 Visual Studio 2015 支援 MVC 4 (您可以開啟現有專案，但不能建立新的專案) 和 MVC 5</li></ul><br/>升級 MVC 版本：<ul><li>如需如何從 MVC 2 自動升級到 MVC 3 的資訊，請參閱 [ASP.NET MVC 3 應用程式升級程式](https://archive.codeplex.com/?p=aspnet)。</li><li>如需關於如何從 MVC 2 手動升級至 MVC 3 的詳細資訊，請參閱 [Upgrading an ASP.NET MVC 2 Project to ASP.NET MVC 3 Tools Update](https://archive.codeplex.com/?p=aspnet)(將 ASP.NET MVC 2 專案升級至 ASP.NET MVC 3 工具更新)。</li><li>如需關於如何從 MVC 3 手動升級至 MVC 4 的詳細資訊，請參閱 [Upgrading an ASP.NET MVC 3 Project to ASP.NET MVC 4](/aspnet/whitepapers/mvc4-release-notes)(將 ASP.NET MVC 3 專案升級至 ASP.NET MVC 4)。 如果您的專案是以 .NET Framework 3.5 SP1 為目標，則必須將目標重定為使用 .NET Framework 4。</li><li>如需如何將 MVC 4 手動升級為 MVC 5 的資訊，請參閱 [How to Upgrade an ASP.NET MVC 4 and Web API Project to ASP.NET MVC 5 and Web API 2](https://www.asp.net/mvc/overview/releases/how-to-upgrade-an-aspnet-mvc-4-and-web-api-project-to-aspnet-mvc-5-and-web-api-2) (如何將 ASP.NET MVC 4 和 Web API 專案升級至 ASP.NET MVC 5 和 Web API 2)。</li></ul> |
| 模型化 | 如果您允許 Visual Studio 自動更新專案，則可以在 Visual Studio 2015、Visual Studio 2013 或 Visual Studio 2012 中開啟專案。<br/><br/>Visual Studio 2015 和 Visual Studio 2017 之間的模型專案格式沒有變更，因此在任一版本都可以開啟和修改專案。 不過，Visual Studio 2017 的行為有下列差異：<ul><li>在功能表和範本中，模型專案現在稱為「相依性驗證」專案。</li><li>Visual Studio 2017 不再支援 UML 圖表。 UML 檔案在方案總管中的列出方式與之前相同，但會以 XML 檔案的形式開啟。 您可以使用 Visual Studio 2015 來檢視、建立或編輯 UML 圖表。</li><li>在 Visual Studio 2017 中建置專案模型時，系統將不再執行架構相依性的驗證。 相反地，系統會在每個程式碼專案建置時執行驗證。 此變更不會影響專案模型建立，但卻必須對要驗證的程式碼專案進行變更。 Visual Studio 2017 可以自動對程式碼專案進行必要的變更 ([詳細資訊](../modeling/validate-code-with-layer-diagrams.md?view=vs-2017&preserve-view=true#live-dependency-validation))。</li></ul> |
| MSI 安裝程式 (vdproj) | 請參閱＜InstallShield 專案＞。 |
| Office 2007 VSTO | 需要針對 Visual Studio 2017 進行單向升級。 |
| Office 2010 VSTO | 如果專案是以 .NET Framework 4 為目標，您可以在 Visual Studio 2010 SP1 及更新版本中開啟該專案。 所有其他專案則需要單向升級。 |
| Service Fabric (sfproj) | Service Fabric 應用程式專案可以在 Visual Studio 2015 或 Visual Studio 2017 中開啟，除非該 Service Fabric 應用程式專案參考 ASP.NET Core 服務專案。 在 Visual Studio 2017 中開啟的 Visual Studio 2015 Service Fabric 專案是從 xproj 格式單向移轉至 csproj 的。 請參閱此表格中稍早提到的「.NET Core 專案 (xproj)」。 |
| SharePoint 2010 | 當使用 Visual Studio 2017 開啟 SharePoint 方案專案時，便會將該專案升級至 SharePoint 2013 或 SharePoint 2016。 必須在 Visual Studio 2017 中安裝「.NET 桌面開發」工作負載以進行升級。<br/><br/>如需如何升級 SharePoint 專案的詳細資訊，請參閱[升級到 SharePoint 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)、[在 SharePoint Server 2013 中更新工作流程 (英文)](/SharePoint/governance/update-workflow-in-sharepoint-server)，以及[針對資料庫附加升級建立 SharePoint Server 2016 伺服器陣列 (英文)](/SharePoint/upgrade-and-update/create-the-sharepoint-server-2016-farm-for-a-database-attach-upgrade)。 |
| SharePoint 2016 | 在 Office Developer Tools Preview 2 中建立的 SharePoint 增益集專案，無法在 Visual Studio 2017 中開啟。 若要規避此限制，請將 csproj vbproj 檔案中的 `MinimumVisualStudioVersion` 更新為 12.0，並將 `MinimumOfficeToolsVersion` 更新為 12.2。 |
| Silverlight | Visual Studio 2017 不支援 Silverlight 專案。 若要維護 Silverlight 應用程式，請繼續使用 Visual Studio 2015。 |
| SQL Server Reporting Services 和 SQL Server Analysis Services (SSRS、SSDT、SSAS、MSAS) | 這些專案類型的支援是透過 Visual Studio 組件庫中的兩個延伸模組來提供：[Microsoft Analysis Services 模型專案](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects)和 [Microsoft Reporting Services 專案](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio)。 SSDT 支援也隨附於 Visual Studio 2017 中的資料儲存和處理工作負載。 如需詳細資訊，請參閱[下載並安裝 SQL Server Data Tools (SSDT) for Visual Studio](/sql/ssdt/download-sql-server-data-tools-ssdt) 頁面。|
| SQL Server Integration Services (SSIS) | 透過 SQL Server Data Tools (SSDT) 可取得 Visual Studio 2017 的支援。 如需詳細資訊，請參閱[下載並安裝 SQL Server Data Tools (SSDT) for Visual Studio](/sql/ssdt/download-sql-server-data-tools-ssdt) 頁面，以及 [SQL Server Integration Services (SSIS) ](https://techcommunity.microsoft.com/t5/SQL-Server-Integration-Services/bg-p/SSIS) \(英文\) 小組部落格。 |
| Visual C++ | 您可以使用 Visual Studio 2017 來處理在較早之前 Visual Studio 版本 (自 Visual Studio 2010 起) 中建立的專案。 當您第一次開啟專案時，可以選擇要升級到最新的編譯器和工具組，或是繼續使用原本的編譯器和工具組。 如果您選擇繼續使用原本的編譯器和工具組，Visual Studio 2017 不會修改專案檔，並且會使用較早 Visual Studio 安裝的工具組來建置您的專案。 保留原本的選項表示您仍然可以視需要在原始的 Visual Studio 版本中開啟該專案。 如需詳細資訊，請參閱[在 Visual Studio 中使用原生多目標來建置舊專案](/cpp/porting/use-native-multi-targeting)。 |
| Visual Studio 擴充性/VSIX | 系統會更新含 MinimumVersion 14.0 或以下版本的專案，以宣告 MinimumVersion 15.0；如此一來，即無法在舊版的 Visual Studio 中開啟專案。 若要允許在舊版本中開啟專案，請將 MinimumVersion 設定為 `$(VisualStudioVersion)`。 另請參閱[如何︰將擴充性專案移轉至 Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)。 |
| Visual Studio Lab Management | 您可以使用 Microsoft Test Manager 或 Visual Studio 2010 SP1 和更新版本，開啟在這些版本中建立的環境。 不過，若是 Visual Studio 2010 SP1，Microsoft Test Manager 的版本必須符合 Team Foundation Server 的版本才能建立環境。 |
| Visual Studio Tools for Apache Cordova | 專案可以在 Visual Studio 2017 中開啟，但不具備回溯相容性。 從 Visual Studio 2015 中開啟專案時，系統會提示您允許對專案進行修改。 此修改會將專案升級為使用工具組 (而不是 `taco.json` 檔案) 來管理 Cordova 程式庫、其平台、其外掛程式，以及其節點/npm 相依性的版本設定。 如需詳細資訊，請參閱[移轉指南](/visualstudio/cross-platform/tools-for-cordova/first-steps/migrate-from-visual-studio-2015)。 |
| Web 部署 (wdproj) | 對 Web 部署專案的支援已在 Visual Studio 2012 中移除，但加入發行設定檔支援。 因為在 Visual Studio 2017 中沒有對等項目，所以沒有適用於此類專案的自動移轉路徑。 請改為在文字編輯器中開啟該 wdproj 檔案，然後將任何自訂項目複製並貼上到 pubxml (發行設定檔) 檔案中，如 [StackOverflow](https://stackoverflow.com/a/12061065/1203388) \(英文\) 上所述。 |
| Windows Communication Foundation 與 Windows Workflow Foundation | 您可以在 Visual Studio 2017、Visual Studio 2015、Visual Studio 2013 和 Visual Studio 2012 中開啟這類專案。 |
| Windows Presentation Foundation | 您可以在 Visual Studio 2017、Visual Studio 2013、Visual Studio 2012 和 Visual Studio 2010 SP1 中開啟這類專案。 |
| Windows 市集/Windows Phone 應用程式 | Visual Studio 2017 不支援 Windows 市集 8.1 和 8.0 以及 Windows Phone 8.1 和 8.0 專案。 若要維護這些應用程式，請繼續使用 Visual Studio 2015。 若要維護 Windows Phone 7.x 專案，請使用 Visual Studio 2012。 |

## <a name="how-visual-studio-decides-when-to-migrate-a-project"></a>Visual Studio 如何決定移轉專案的時間

Visual Studio 的每個新版本通常都會嘗試維持與舊版的相容性，使得相同的專案可以在不同的版本中開啟、修改和建置。 不過，隨著時間變化出現無可避免的變更，而導致某些專案類型可能不再受支援。  (請參閱 Visual Studio 2017 中支援的專案類型的 [平臺目標和相容性](/visualstudio/productinfo/vs2017-compatibility-vs) 。 ) 在這些情況下，較新版本的 Visual Studio 將不會載入專案，也不會提供遷移路徑;您必須在支援此專案的舊版 Visual Studio 中維護該專案。

在其他情況下，較新版本的 Visual Studio 可以開啟專案，但必須以可能會使其與舊版不相容的方式更新或移轉專案。 Visual Studio 會使用幾個準則，來判斷是否必須進行這類移轉：

- 與目標版本平台的相容性，回溯到 Visual Studio 2013 RTM。

- 設計階段資產與舊版 Visual Studio 的相容性。  (Visual Studio 2017 的不同通道;Visual Studio 2015 RTM & Update 3;Visual Studio 2013 RTM & Update 5;Visual Studio 2012 Update 4;Visual Studio 2010 SP 1. ) Visual Studio 2017 的目標是要讓已淘汰的設計階段資產正常失敗，而不會損毀，使得舊版仍然可以開啟專案。

- 新的設計階段資產是否會中斷與回溯到 Visual Studio 2013 RTM 和 Update 5 的舊版相容性。

有問題之專案類型的工程擁有者會查看這些準則，並在涉及支援、相容性和移轉處進行呼叫。 同樣地，可能的話，Visual Studio 會嘗試維持 Visual Studio 版本之間的透明相容性，這表示某人可以在某個版本的 Visual Studio 中建立和修改專案，而該專案只會在其他版本中使用。

不過，如同本文中描述的某些專案類型，若這類相容性不可行，則 Visual Studio 會開啟升級精靈來進行必要的單向變更。

這類單向變更可能包含變更專案檔中的 `ToolsVersion` 屬性，此屬性確切表示哪個版本的 MSBuild 可以將專案的原始程式碼變成您最終需要的可執行且可部署成品。 也就是說，使專案與舊版 Visual Studio 不相容的項目不是 *Visual Studio* 版本，而是 `ToolsVersion` 所決定的 *MSBuild* 版本。 只要您的 Visual Studio 版本包含的 MSBuild 工具鏈符合專案中的 `ToolsVersion`，Visual Studio 就可以叫用該工具鏈來建置專案。

為了保持與較舊版本所建立專案的最大相容性，Visual Studio 2017 包含了必要的 MSBuild 工具鏈來支援 `ToolsVersion` 15、14、12 和 4。 使用其中任一 `ToolsVersion` 值的專案應該都能成功建置。 (同樣地，取決於 Visual Studio 2017 是否完全支援該專案類型，如[平台目標及相容性](/visualstudio/productinfo/vs2017-compatibility-vs)所述。)

在此情況下，自然會產生下列問題：您是否應該嘗試以手動方式更新，或將專案移轉至較新的 `ToolsVersion` 值。 進行這類變更是不必要的作業，而且可能會產生許多錯誤和警告，您必須修正這些問題才能重新建置專案。 此外，如果 Visual Studio 日後移除對特定 `ToolsVersion` 的支援，則開啟專案將會明確地觸發專案移轉處理序，因為 `ToolsVersion` 值必須進行變更。 在這種情況下，該特定專案類型的子系統會確切知道需要變更哪些項目，而且會遵循本文稍早所述自動進行這些變更。

## <a name="next-steps"></a>下一步

請參閱下列文章以了解進一步的討論內容：

- [ToolsVersion 指導方針](../msbuild/msbuild-toolset-toolsversion.md)
- [Framework 目標指導方針](../ide/visual-studio-multi-targeting-overview.md)

## <a name="see-also"></a>另請參閱

- [Visual Studio 2019 的專案移轉與升級參考](port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2019&preserve-view=true)
- [Visual Studio 產品生命週期和服務](/visualstudio/releases/2019/servicing/)

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 的每個新版本都支援大部分的專案、檔案及其他資產類型。 您可以 [如往常一樣](../ide/solutions-and-projects-in-visual-studio.md)使用它們，但前提是您不需依賴較新的功能。

我們會嘗試保留與舊版的回溯相容性，例如 Visual Studio 2017、Visual Studio 2015、Visual Studio 2013 和 Visual Studio 2012。 不過，對某些專案類型的支援會隨著時間而改變。 較新版本的 Visual Studio 可能完全不支援某些專案，或者，您可能需要更新專案，使其不再回溯相容。

> [!NOTE]
> 如需移轉問題的目前狀態，請參閱 [Visual Studio Developer Community](https://aka.ms/feedback/suggest?space=8)。 若要深入瞭解 Visual Studio 版本的特定功能，請參閱 [版本](/visualstudio/releases/2019/release-notes/)資訊。

> [!IMPORTANT]
> 某些專案類型需要特定的工作負載。 如果您未安裝工作負載，Visual Studio 會回報未知或不相容的專案類型。 在此情況下，請檢查 [Visual Studio 安裝程式中的安裝選項](../install/modify-visual-studio.md) ，然後再試一次。 如需 Visual Studio 2019 中專案支援的詳細資訊，請參閱 [平臺目標與相容性](/visualstudio/releases/2019/compatibility) 頁面。

## <a name="project-types"></a>專案類型

下列清單描述 Visual Studio 2019 對使用舊版建立之專案的支援。

如果您在這裡看不到此處所列的專案或檔案類型，請參閱 [這篇文章的 Visual Studio 2017 版本](?view=vs-2017&preserve-view=true)。 您也可以使用此頁面底部的 [**傳送關於**  >  **此頁面** 的意見反應] 按鈕，以提供專案的詳細資料。 (如果您使用匿名的「本頁對您有幫助嗎？」 控制項，我們將無法回應您的意見反應。)

| 專案類型 | 支援 |
| --- | --- |
| .NET Core 專案 (xproj) | 以 Visual Studio 2015 建立的專案所使用的預覽工具，包含 xproj 專案檔。<br/><br/>Visual Studio 2017：不支援用來遷移至 .csproj 格式的 xproj 格式。 當您開啟 xproj 檔案時，系統會提示您將檔案遷移至 SDK 樣式的 .csproj 格式。  (建立 xproj 檔案的備份。 Visual Studio 2015 及更早版本不支援 ) SDK 樣式的 .csproj 專案。 <br/><br/>Visual Studio 2019：在16.3 版和更新版本中，您無法載入或遷移 xproj 專案。 如需詳細資訊，請參閱將 [.Net Core 專案遷移至 .csproj 格式](/dotnet/core/migration/#visual-studio)。|
| 已啟用 Application Insights 的 ASP.NET Web 應用程式和 ASP.NET Core Web 應用程式 | 對每位 Visual Studio 使用者來說，資源資訊會儲存在每個使用者執行個體的登錄中。 當使用者未開啟任何專案，而要搜尋 Azure Application Insights 資料時，就會使用此資訊。 Visual Studio 2015 使用的登錄位置不同於 Visual Studio 2017 和 Visual Studio 2019，因此不會產生衝突。<br/><br/>在使用者建立 ASP.NET Web 應用程式或 ASP.NET Core Web 應用程式之後，資源就會存放在 .suo 檔案中。 只要 Visual Studio 支援在 Visual Studio 2015、Visual Studio 2017 和 Visual Studio 2019 中使用專案和方案，使用者即可在這些版本中開啟專案，資源資訊亦可用於每個版本。 使用者必須在每個產品上進行一次驗證。 例如，如果專案是以 Visual Studio 2017 建立並在 Visual Studio 2019 中開啟，則使用者也需要在 Visual Studio 2019 上進行驗證。 |
| C#/Visual Basic Webform 或 Windows Form | 您可以在 Visual Studio 2019、Visual Studio 2017 和 Visual Studio 2015 中開啟專案。 |
| 自動程式化 UI 測試 | 自動化 UI 驅動功能測試的自動程式化 UI 測試在 Visual Studio 2019 中已淘汰。 <br/><br/>Visual Studio 2019 將會是最後一個提供自動程式化 UI 測試的版本。 建議您使用 Selenium 測試 Web 應用程式，而使用 Appium 與 WinAppDriver 測試傳統型和 UWP 應用程式。 |
| 資料庫單元測試專案 (csproj、vbproj) | Visual Studio 2019 可以載入舊版的資料單元測試專案，但會使用 GAC 版本的相依性。 若要升級單元測試專案以使用最新的相依性，請以滑鼠右鍵按一下方案總管，並選取 [轉換成 SQL Server 單元測試專案...]。 |
| F# | Visual Studio 2019 可以開啟在 Visual Studio 2013、Visual Studio 2015 和 Visual Studio 2017 中建立的專案。 與舊版 Visual Studio 範本的一個主要差異，就是在新專案中，FSharp.Core 版本現在一律是 NuGet 套件。 F# 預設會隨任何 .NET 工作負載安裝。|
| InstallShield<br/>MSI 安裝程式 | 在 Visual Studio 2010 中建立的安裝程式專案，可以透過 [Visual Studio Installer Projects extension](https://marketplace.visualstudio.com/items?itemName=UnniRavindranathan-MSFT.MicrosoftVisualStudio2013InstallerProjects) (Visual Studio 安裝程式專案延伸模組) 的協助在較新版本中開啟。 另請參閱 [WiX Toolset Visual Studio 2017 Extension](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension) (WiX 工具組 Visual Studio 2017 延伸模組)。 Visual Studio 不再隨附 InstallShield 限量版。 如需 Visual Studio 2019 的可用性，請參閱 [Flexera Software](https://info.flexerasoftware.com/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio)。 |
| LightSwitch | Visual Studio 2019 或 Visual Studio 2017 不再支援 LightSwitch。 在 Visual Studio 2013 或 Visual Studio 2015 中，如果開啟使用 Visual Studio 2012 和更早版本所建立的專案，系統會將該專案升級，並僅可在 Visual Studio 2013 或 Visual Studio 2015 之後的版本中開啟。 |
| 負載測試 | Web 效能和負載測試功能在 Visual Studio 2019 中已淘汰。 <br/><br/>Visual Studio 2019 將會是最後一個提供負載測試的版本。 請使用替代的負載測試工具，例如 Apache JMeter、Akamai CloudTest、Blazemeter。  |
| Microsoft Azure Tools for Visual Studio | 若要開啟這些類型的專案，請先安裝 [Azure SDK for .NET](https://azure.microsoft.com/downloads/)，然後再開啟專案。 如有必要，系統會更新您的專案。 |
| Microsoft Test Manager | 從 Visual Studio 2019 開始，Visual Studio 不再隨附 Microsoft Test Manager 和 Feedback Client。 <br/><br/>如有手動和探勘測試需求，請利用 Azure Test Plans (Azure DevOps 的一部分)。 如需詳細資訊，請參閱 Azure DevOps 文件中的 [Microsoft Test Manager 使用指導方針](/azure/devops/test/mtm/guidance-mtm-usage?view=azure-devops&preserve-view=true)頁面。 |
| 模型檢視控制器架構 (ASP.NET MVC) | 針對 MVC 版本和 Visual Studio 的支援：<ul><li>Visual Studio 2010 SP1 支援 MVC 2 和 MVC 3；您可透過 [ASP.NET 4 MVC 4 for Visual Studio 2010 SP1 下載](https://www.microsoft.com/download/details.aspx?id=30683)來新增 MVC 4 的支援</li><li>Visual Studio 2012 只支援 MVC 3 和 MVC 4</li><li>Visual Studio 2013 只支援 MVC 4 和 MVC 5</li><li>Visual Studio 2019、Visual Studio 2017 和 Visual Studio 2015 支援 MVC 4 (您可以開啟現有專案，但不能建立新的專案) 和 MVC 5</li></ul><br/>升級 MVC 版本：<ul><li>如需如何從 MVC 2 自動升級到 MVC 3 的資訊，請參閱 [ASP.NET MVC 3 應用程式升級程式](https://archive.codeplex.com/?p=aspnet)。</li><li>如需關於如何從 MVC 2 手動升級至 MVC 3 的詳細資訊，請參閱 [Upgrading an ASP.NET MVC 2 Project to ASP.NET MVC 3 Tools Update](https://archive.codeplex.com/?p=aspnet)(將 ASP.NET MVC 2 專案升級至 ASP.NET MVC 3 工具更新)。</li><li>如需關於如何從 MVC 3 手動升級至 MVC 4 的詳細資訊，請參閱 [Upgrading an ASP.NET MVC 3 Project to ASP.NET MVC 4](/aspnet/whitepapers/mvc4-release-notes)(將 ASP.NET MVC 3 專案升級至 ASP.NET MVC 4)。 如果您的專案是以 .NET Framework 3.5 SP1 為目標，則必須將目標重定為使用 .NET Framework 4。</li><li>如需如何將 MVC 4 手動升級為 MVC 5 的資訊，請參閱 [How to Upgrade an ASP.NET MVC 4 and Web API Project to ASP.NET MVC 5 and Web API 2](https://www.asp.net/mvc/overview/releases/how-to-upgrade-an-aspnet-mvc-4-and-web-api-project-to-aspnet-mvc-5-and-web-api-2) (如何將 ASP.NET MVC 4 和 Web API 專案升級至 ASP.NET MVC 5 和 Web API 2)。</li></ul> |
| 模型化 | 如果您允許 Visual Studio 自動更新專案，則可以在 Visual Studio 2015、Visual Studio 2013 或 Visual Studio 2012 中開啟專案。<br/><br/>模型專案的格式自 Visual Studio 2015 以後並未變更，因此您可以在這些版本中開啟及修改專案。 不過，Visual Studio 2017 和 Visual Studio 2019 的行為有下列差異：<ul><li>在功能表和範本中，模型專案現在稱為「相依性驗證」專案。</li><li>Visual Studio 2017 和 Visual Studio 2019 不再支援 UML 圖表。 UML 檔案在方案總管中的列出方式與之前相同，但會以 XML 檔案的形式開啟。 您可以使用 Visual Studio 2015 來檢視、建立或編輯 UML 圖表。</li><li>在 Visual Studio 2019 中建置專案模型時，系統將不再執行架構相依性的驗證。 相反地，系統會在每個程式碼專案建置時執行驗證。 此變更不會影響專案模型建立，但卻必須對要驗證的程式碼專案進行變更。 Visual Studio 2019 可以自動對程式碼專案進行必要的變更。</li></ul> |
| MSI 安裝程式 (vdproj) | 請參閱＜InstallShield 專案＞。 |
| Office 2007 VSTO | 需要針對 Visual Studio 2019 進行單向升級。 |
| Office 2010 VSTO | 如果專案是以 .NET Framework 4 為目標，您可以在 Visual Studio 2010 SP1 及更新版本中開啟該專案。 所有其他專案則需要單向升級。 |
| 可攜式類別庫 (PCL) | 可攜式類別庫 (或 PCL) 現在不受支援。 Visual Studio 2019 仍然可以開啟和建置它們，但無法建立新的 PCL 專案。 建議將 PCL 專案中的程式碼移轉至 .NET Standard 專案。<br/><br/>預設不再隨附 PCL 支援，但可透過 Visual Studio 的 [個別元件] 索引標籤取得。 |
| Python 工作負載 | 對 Python Windows IoT Core 應用程式的支援已在 Visual Studio 2019 中移除。 因為在 Visual Studio 2019 Preview 中沒有對等項目，所以沒有適用於此類專案的自動移轉路徑。<br/><br/>您可以繼續使用 Visual Studio 2017。 |
| 適用於 Visual Studio 的 R 工具 | 適用於 Visual Studio 的 R 工具已從 Visual Studio 2019 資料科學工作負載中移除。<br/><br/>您可以繼續使用 Visual Studio 2017 或 RStudio 等替代產品。 |
| Service Fabric (sfproj) | Service Fabric 應用程式專案可以在 Visual Studio 2015、Visual Studio 2017 和 Visual Studio 2019 Preview 中開啟，除非該 Service Fabric 應用程式專案參考 ASP.NET Core 服務專案。 在 Visual Studio 2017 或 Visual Studio 2019 Preview 中開啟的 Visual Studio 2015 Service Fabric 專案是從 xproj 格式單向移轉至 csproj 格式。 請參閱此表格中稍早提到的「.NET Core 專案 (xproj)」。 |
| SharePoint 2010 | 當使用 Visual Studio 2019 開啟 SharePoint 方案專案時，便會將該專案升級至 SharePoint 2013 或 SharePoint 2016。 必須在 Visual Studio 2019 中安裝「.NET 桌面開發」工作負載以進行升級。<br/><br/>如需如何升級 SharePoint 專案的詳細資訊，請參閱[升級到 SharePoint 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)、[在 SharePoint Server 2013 中更新工作流程 (英文)](/SharePoint/governance/update-workflow-in-sharepoint-server)，以及[針對資料庫附加升級建立 SharePoint Server 2016 伺服器陣列 (英文)](/SharePoint/upgrade-and-update/create-the-sharepoint-server-2016-farm-for-a-database-attach-upgrade)。 |
| SharePoint 2016 | 在 Office Developer Tools Preview 2 中建立的 SharePoint 增益集專案無法在 Visual Studio 2019 中開啟。 若要規避此限制，請將 csproj vbproj 檔案中的 `MinimumVisualStudioVersion` 更新為 12.0，並將 `MinimumOfficeToolsVersion` 更新為 12.2。 |
| Silverlight | Visual Studio 2019 不支援 Silverlight 專案。 若要維護 Silverlight 應用程式，請繼續使用 Visual Studio 2015。 |
| SQL - Redgate | Visual Studio 安裝程式不再隨附 Redgate 的 SQL Change Automation Core (之前稱為 ReadyRoll Core)、SQL Prompt Core 和 SQL Search。<br/><br/>您可以繼續使用 Visual Studio 2017 來取得這些功能。 在 Visual Studio 2019 中，您可以升級為 Redgate SQL Toolbelt 中所提供的付費 SQL Change Automation 和 SQL Prompt 產品。|
| SQL Server Reporting Services 和 SQL Server Analysis Services (SSRS、SSDT、SSAS、MSAS) | 這些專案類型的支援是透過 Visual Studio 組件庫中的兩個延伸模組來提供：[Microsoft Analysis Services 模型專案](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects)和 [Microsoft Reporting Services 專案](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio)。 SSDT 支援也隨附於 Visual Studio 2019 中的資料儲存和處理工作負載。 如需詳細資訊，請參閱[下載並安裝 SQL Server Data Tools (SSDT) for Visual Studio](/sql/ssdt/download-sql-server-data-tools-ssdt) 頁面。 |
| SQL Server Integration Services (SSIS) | 可取得 Visual Studio 2019 的支援。 如需詳細資訊，請參閱[下載並安裝 SQL Server Data Tools (SSDT) for Visual Studio](/sql/ssdt/download-sql-server-data-tools-ssdt) 頁面、[SQL Server Integration Services (SSIS) ](https://techcommunity.microsoft.com/t5/SQL-Server-Integration-Services/bg-p/SSIS) \(英文\) 小組部落格，以及 Marketplace 上的 [SQL Server 整合服務專案](https://marketplace.visualstudio.com/items?itemName=SSIS.SqlServerIntegrationServicesProjects&ssr=false#overview) \(英文\) 頁面。 |
| 測試視窗延伸模組 | 在 Visual Studio 2019 中，會移除一些先前標記為公用，但從未正式記載的測試視窗 API。 許多 API 已在 Visual Studio 2017 中標示為已淘汰，可為延伸模組維護人員提供初期警告。 據我們所知，很少有延伸模組相依於這些 API。 如需詳細資訊和更新，請檢視[已淘汰之測試相關 API 的完整清單](https://github.com/Microsoft/vstest/issues/1830)。 如果這會影響您的案例，請在[開發人員社群](https://aka.ms/feedback/suggest?space=8)中讓我們知道。 |
| Visual C++ | 您可以使用 Visual Studio 2019 來處理在 Visual Studio 更早版本 (自 Visual Studio 2010 起) 中建立的專案。 當您第一次開啟專案時，可以選擇要升級到最新的編譯器和工具組，或是繼續使用原本的編譯器和工具組。 如果您選擇繼續使用原本的編譯器和工具組，Visual Studio 2019 不會修改專案檔，且會使用 Visual Studio 更早所安裝工具組來建置您的專案。 保留原本的選項表示您仍然可以視需要在原始的 Visual Studio 版本中開啟該專案。 如需詳細資訊，請參閱[在 Visual Studio 中使用原生多目標來建置舊專案](/cpp/porting/use-native-multi-targeting)。 |
| Visual Studio 擴充性/VSIX | 系統會更新含 MinimumVersion 14.0 或以下版本的專案，以宣告 MinimumVersion 15.0；如此一來，即無法在舊版的 Visual Studio 中開啟專案。 若要允許在舊版本中開啟專案，請將 MinimumVersion 設定為 `$(VisualStudioVersion)`。 另請參閱[如何︰將擴充性專案移轉至 Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)。 |
| Visual Studio Lab Management | 您可以使用 Microsoft Test Manager 或 Visual Studio 2010 SP1 和更新版本，開啟在這些版本中建立的環境。 不過，若是 Visual Studio 2010 SP1，Microsoft Test Manager 的版本必須符合 Team Foundation Server 的版本才能建立環境。 |
| Visual Studio Tools for Apache Cordova | 對 Apache Cordova 的支援已在 Visual Studio 2019 中移除。 因為在 Visual Studio 2019 中沒有對等項目，所以沒有適用於此類專案的自動移轉路徑。<br/><br/>您可以使用適用於 Visual Studio 的 Cordova 工具延伸模組 (提供最新版 Cordova 的支援)，或繼續使用 Visual Studio 2017。 |
| Web 部署 (wdproj) | 對 Web 部署專案的支援已在 Visual Studio 2012 中移除，但加入發行設定檔支援。 因為在 Visual Studio 2019 中沒有對等項目，所以沒有適用於此類專案的自動移轉路徑。 請改為在文字編輯器中開啟該 wdproj 檔案，然後將任何自訂項目複製並貼上到 pubxml (發行設定檔) 檔案中，如 [StackOverflow](https://stackoverflow.com/a/12061065/1203388) \(英文\) 上所述。 |
| Windows Communication Foundation 與 Windows Workflow Foundation | 您可以在 Visual Studio 2019、Visual Studio 2017、Visual Studio 2015、Visual Studio 2013 和 Visual Studio 2012 中開啟這類專案。 |
| Windows Presentation Foundation | 您可以在 Visual Studio 2019、Visual Studio 2017、Visual Studio 2013、Visual Studio 2012 和 Visual Studio 2010 SP1 中開啟此專案。 |
| Windows Phone 應用程式 | Visual Studio 2019 不支援 Windows Phone 專案。 <br/><br/>若要保留 Windows Phone 8.x 應用程式，請使用 Visual Studio 2015。 若要維護 Windows Phone 7.x 專案，請使用 Visual Studio 2012。 |
| Windows 市集應用程式 | Visual Studio 2019 不支援 JavaScript 通用 Windows 專案。 若要保留這些專案，請使用 Visual Studio 2017。 <br/><br/>Windows 10 Fall Creators Update (組建 16299) 之前的 Windows 10 SDK 已從 Visual Studio 2019 安裝工具中移除。 您可以手動下載舊版 SDK，或將專案目標重定為使用新版 SDK。<br/><br/>不支援使用 project.json 的通用 Windows 專案。 建議升級這些專案以使用套件參考。 或者，在 project.json 檔案中新增 Microsoft.NET.Test.Sdk 16.0.0.0 版的參考。<br/><br/>Visual Studio 2019 不支援 Windows Store 8.1 和 8.0 專案。 若要維護這些應用程式，請繼續使用 Visual Studio 2015。 |
| Xamarin | 已移除適用於 Visual Studio 和 Visual Studio for Mac 的 Xamarin Live Player 延伸模組。 這會移除成對的畫面和任何整合。 請改用內建 Xamarin.Forms Previewer。<br/><br/>Visual Studio 的 Android 模擬器已從 Visual Studio 安裝程式中移除。 請改用 Google Android 模擬器中新增的 Hyper-V 支援。 |

## <a name="migrate-a-project"></a>移轉專案

當我們嘗試維持與舊版的相容性時，可能會有與舊版不相容的變更。  (請參閱 Visual Studio 2019 中支援的專案類型的 [平臺目標和相容性](/visualstudio/releases/2019/compatibility) 。 ) 發生這種情況時，較新版本的 Visual Studio 將不會載入專案或提供遷移路徑。 您可能必須在舊版 Visual Studio 中維護該專案。

有時候，較新版本的 Visual Studio 可以開啟專案，但它必須以可能會使其與舊版不相容的方式來更新或遷移專案。 Visual Studio 會使用幾個準則，來判斷是否必須進行這類移轉：

- 與目標版本平台的相容性，回溯到 Visual Studio 2013 RTM。

- 設計階段資產與舊版 Visual Studio 的相容性。  (Visual Studio 2019，Visual Studio 2017;）的不同通道Visual Studio 2015 RTM & Update 3;Visual Studio 2013 RTM & Update 5;Visual Studio 2012 Update 4;Visual Studio 2010 SP 1. ) Visual Studio 2019 的目標是要讓已淘汰的設計階段資產正常失敗，而不會損毀，使得舊版仍然可以開啟專案。

- 新的設計階段資產是否會中斷與回溯到 Visual Studio 2013 RTM 和 Update 5 的舊版相容性。

擁有專案類型的工程小組會查看這些準則，並進行支援、相容性和遷移的相關呼叫。 同樣地，我們會嘗試維持 Visual Studio 版本之間的相容性，如此一來，當您在某個版本的 Visual Studio 中建立和修改專案時，它就會在其他版本中運作。

有時無法進行相容性。 然後，Visual Studio 會開啟升級嚮導，以進行必要的單向變更。 這些單向變更可能牽涉到變更專案檔 `ToolsVersion` 中的屬性，這代表哪個版本的 MSBuild 可以將專案的原始程式碼轉換成您想要的可執行和可部署的構件。

專案呈現與舊版 Visual Studio 不相容的專案不是 *Visual Studio* 版本，而是由所決定的 *MSBuild* 版本 `ToolsVersion` 。 如果您的 Visual Studio 版本包含的 MSBuild 工具鏈符合 `ToolsVersion` 專案中的，則 Visual Studio 可以叫用該工具鏈以建立專案。

為了維持與您在舊版中建立之專案的相容性，Visual Studio 2019 包含必要的 MSBuild 工具鏈來支援 `ToolsVersion` 15、14、12和4。 使用其中任一 `ToolsVersion` 值的專案應該都能成功建置。 同樣地， (主旨，Visual Studio 2019 是否支援專案類型，如 [平臺目標和相容性](/visualstudio/releases/2019/compatibility)所述。 ) 

您可能會想要以手動方式將專案更新或遷移至較新的 `ToolsVersion` 值。 不需要進行這項變更，而且可能會產生許多錯誤和警告，您必須修正這些錯誤和警告，才能讓專案再次建立。 此外，如果 Visual Studio 不支援未來的特定 `ToolsVersion` ，則當您開啟專案時，專案就會觸發專案遷移程式，因為它的 `ToolsVersion` 值必須變更。

## <a name="next-steps"></a>下一步

請參閱下列文章以了解進一步的討論內容：

- [ToolsVersion 指導方針](../msbuild/msbuild-toolset-toolsversion.md)
- [Framework 目標指導方針](../ide/visual-studio-multi-targeting-overview.md)

## <a name="see-also"></a>另請參閱

- [Visual Studio 2017 的專案移轉與升級參考](?view=vs-2017&preserve-view=true)
- [Visual Studio 產品生命週期和服務](/visualstudio/releases/2019/servicing/)

::: moniker-end