---
title: 使用 NuGet 和擴充功能 SDK 兩種方式新增參考
description: 瞭解在 Visual Studio 專案中參考封裝軟體作為 NuGet 套件或軟體發展工具組之間的差異。
ms.custom: SEO-VS-2020
ms.date: 08/02/2019
ms.topic: conceptual
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ab2a99c2230c9fc150fe06c305741eedf14ded37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874031"
---
# <a name="nuget-versus-sdk-as-a-project-reference"></a>NuGet 與 SDK 做為專案參考

本文旨在協助開發人員選擇是否要將其軟體封裝為 NuGet 套件，或 (SDK) 的軟體發展工具組。 具體而言，它會討論 Visual Studio 專案中參考兩者之間的差異。

- [NuGet](/nuget) 是一種開放原始碼套件管理系統，可簡化將程式庫併入專案的流程。 針對 .NET (包括 .NET Core) ，NuGet 是 Microsoft 支援共用程式碼的機制。 NuGet 定義了如何建立、裝載和取用 .NET 的套件，並為每個角色提供工具。 在 Visual Studio 中，您可以使用 [封裝管理員](/nuget/consume-packages/install-use-packages-visual-studio) 使用者介面，將 NuGet 套件新增至專案。

- [SDK](../extensibility/creating-a-software-development-kit.md)是檔案的集合，Visual Studio 會將其視為單一參考專案。 當您選擇 [ **加入參考**] 時，Visual Studio 中的 [參考管理員] 對話方塊會列出所有與目前專案相關的 sdk。 當您將 SDK 新增至專案時，您可以透過 IntelliSense、工具箱視窗、設計工具、物件瀏覽器、MSBuild、部署、偵錯工具和封裝，來存取該 SDK 的所有內容。

## <a name="which-mechanism-should-i-use"></a>應該使用哪一種機制？

下表可協助您比較 SDK 的參考功能與 NuGet 的參考功能。

| 功能 | SDK 支援 | SDK 資訊 | NuGet 支援 | NuGet 資訊 |
| - | - | - |---------------| - |
| 機制會參考一個實體，然後即可使用所有檔案和功能。 | Y | 使用 [參考管理員] 對話方塊新增 SDK，即可在開發工作流程期間使用所有檔案和功能。 | Y | |
| MSBuild 會自動使用元件和 Windows 中繼資料 (*winmd*) 檔。 | Y | SDK 中的參考會自動傳遞給編譯器。 | Y | |
| MSBuild 會自動使用 .h 或 .lib 檔案。 | Y | *SDKName.props* 檔案會指示 Visual Studio 如何設定 Visual C++ 目錄等等，以自動使用 *.h* 或 *.lib* 檔案。 | N | |
| MSBuild 會自動使用  *.js* 或 *.css* 檔案。 | Y | 在 [方案總管] 中，您可以展開 JavaScript SDK 參考節點以顯示個別的 *.js* 或 *.css* 檔案，然後將這些檔案拖曳至來源檔案以產生 `<source include/>` 標記。 SDK 支援 F5 及自動套件設定。 | Y | |
| MSBuild 會自動在 [工具箱] 中新增控制項。 | Y | [工具箱] 可以使用 SDK，並在您指定的索引標籤中顯示控制項。 | N | |
| 機制會支援 Visual Studio 延伸模組安裝程式 (VSIX)。 | Y | VSIX 有用以建立 SDK 套件的特殊資訊清單和邏輯 | Y | VSIX 可以內嵌在另一個安裝程式中。 |
| [物件瀏覽器] 會列舉參考。 | Y | [物件瀏覽器] 會自動取得 SDK 中的參考清單，並列舉它們。 | N | |
| 檔案和連結會自動新增至 [參考管理員] 對話方塊 (說明連結等會自動填入) | Y | [參考管理員] 對話方塊會自動列舉 SDK、說明連結和 SDK 相依性的清單。 | N | NuGet 提供它自己的 [管理 NuGet 套件] 對話方塊。 |
| 機制支援多個架構。 | Y | SDK 可以運送多個組態。 MSBuild 會針對每個專案組態使用適當的檔案。 | N | |
| 機制支援多個組態。 | Y | SDK 可以運送多個組態。 根據專案的架構，MSBuild 會針對每個專案架構使用適當的檔案。 | N | |
| 機制可以指定「不複製」。 | Y | 根據檔案放在 *\redist* 或 *\designtime* 資料夾而定，您可以控制要將哪些檔案複製到取用應用程式的套件中。 | N | 您在套件資訊清單中宣告要複製的檔案。 |
| 內容會出現在已當地語系化的檔案中。 | Y | SDK 中的當地語系化 XML 文件會自動包含以獲得更佳的設計階段體驗。 | N | |
| MSBuild 支援同時使用多個版本的 SDK。 | Y | SDK 支援同時使用多個版本。 | N | 這不參考。 同一時間內，您不能在專案中有多個版本的 NuGet 檔案。 |
| 機制支援指定適用的目標 Framework、Visual Studio 版本和專案類型。 | Y | [參考管理員] 對話方塊和 [工具箱] 只會顯示適用於專案的 SDK，讓使用者可以更輕鬆地選擇適當的 SDK。 | Y (部分) | 樞紐分析是目標 Framework。 使用者介面上沒有任何篩選。 在安裝時，它可能會傳回錯誤。 |
| 機制支援指定原生 WinMD 的註冊資訊。 | Y | 您可以在 *SDKManifest.xml* 中指定 .winmd 檔案和 .dll 檔案之間的關聯性。 | N | |
| 機制支援指定對其他 SDK 的相依性。 | Y | SDK 只會通知使用者。使用者仍必須手動安裝它們並加以參考。 | Y | NuGet 會自動提取它們，且不會通知使用者。 |
| 機制與應用程式資訊清單和 Framework 識別碼等 [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] 概念整合。 | Y | SDK 必須傳遞 [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] 的特定概念，以便封裝和 F5 能正確地搭配 [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] 中可用的 SDK 使用。 | N | |
| 機制與 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 應用程式的應用程式偵錯管線整合。 | Y | SDK 必須傳遞 [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] 的特定概念，以使封裝和 F5 能正確地搭配 [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] 中可用的 SDK 使用。 | Y | NuGet 內容會成為專案的一部分。 不需要任何特殊的 F5 考量。 |
| 機制與應用程式資訊清單整合。 | Y | SDK 必須傳遞 [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] 的特定概念，以使封裝和 F5 能正確地搭配 [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] 中可用的 SDK 使用。 | Y | NuGet 內容會成為專案的一部分。 不需要任何特殊的 F5 考量。 |
| 機制會部署非參考檔案 (例如，部署在其上執行 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 應用程式測試的測試架構)。 | Y | 如果您將檔案放在 *\redist* 資料夾中，則系統會自動部署檔案。 | Y | |
| 機制會自動在 Visual Studio IDE 中新增平台 SDK。 | Y | 如果您將 [!INCLUDE[win8](../debugger/includes/win8_md.md)] SDK 或 Windows Phone SDK 放在具有特定配置的特定位置，SDK 會自動與所有 Visual Studio 功能整合。 | N | |
| 機制支援全新的開發人員機器。 (也就是，不需安裝作業，簡單地從原始程式碼控制擷取即可運作。) | N | 由於您參考 SDK，因此您必須個別簽入您的方案和 SDK。 您可以從兩個 MSBuild 逐一查看 SDK 的非登錄預設位置簽入 SDK (如需詳細資訊，請參閱[建立軟體開發套件](../extensibility/creating-a-software-development-kit.md))。 或者，如果自訂位置包含 SDK，您可以在專案檔中指定下列程式碼︰<br /><br />`<PropertyGroup>`<br />&nbsp;&nbsp;`<SDKReferenceDirectoryRoot>`<br />&nbsp;&nbsp;`C:\MySDKs`<br />&nbsp;&nbsp;`</SDKReferenceDirectoryRoot>`<br />`</PropertyGroup>`<br /><br /> 然後將 SDK 簽入到該位置。 | Y | 您可以簽出方案，Visual Studio 可立即辨識並處理檔案。 |
| 您可以加入龐大的現有套件作者社群。 | N/A | 此為新社群。 | Y | |
| 您可以加入龐大的現有套件取用者社群。 | N/A | 此為新社群。 | Y | |
| 您可以加入合作夥伴的生態系統 (自訂組件庫、儲存機制等等)。 | N/A | 可用的存放庫包含 Visual Studio Marketplace、Microsoft 下載中心與 [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]。 | Y | |
| 機制與連續整合建置伺服器整合，以建立和使用套件。 | Y | SDK 必須在命令列上將簽入位置 (SDKReferenceDirectoryRoot 屬性) 傳遞給 MSBuild。 | Y | |
| 機制支援穩定和發行前版本的套件版本。 | Y | SDK 支援將參考新增至多個版本。 | Y | |
| 機制支援自動更新已安裝的套件。 | Y | 如果作為 VSIX 或部分 Visual Studio 自動更新寄送，SDK 會提供自動通知。 | Y | |
| 機制中包含獨立的 *.exe* 檔案，可用來建立及使用套件。 | Y | SDK 包含 *MSBuild.exe*。 | Y | |
| 套件可以簽入至版本控制。 | Y | 您不能在 [文件] 節點之外簽入任何內容，因此可能不會簽入延伸模組 SDK。 延伸模組 SDK 的大小可能很大。 | Y | |
| 您可以使用 PowerShell 介面來建立和使用套件。 | Y (使用)、N (建立) | 沒有工具可建立 SDK。 使用是在命令列上執行 MSBuild。 | Y | |
| 您可以使用符號套件進行偵錯支援。 | Y | 如果您將 *.pdb* 檔案放在 SDK 中，就會自動挑選這些檔案。 | Y | |
| 機制支援套件管理員自動更新。 | N/A | SDK 因 MSBuild 而修改。 | Y | |
| 機制支援輕量的資訊清單格式。 | Y | *SDKManifest.xml* 支援許多屬性，但通常只有一小部分為必要。 | Y | |
| 機制可供所有 Visual Studio 版本使用。 | Y | SDK 支援所有 Visual Studio 版本。 | Y | NuGet 支援所有 Visual Studio 版本。 |

## <a name="see-also"></a>另請參閱

- [管理專案中的參考](../ide/managing-references-in-a-project.md)
- [管理專案中的參考 (Visual Studio for Mac)](/visualstudio/mac/managing-references-in-a-project)
