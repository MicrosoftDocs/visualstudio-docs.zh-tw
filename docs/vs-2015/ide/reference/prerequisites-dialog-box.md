---
title: 必要條件對話方塊 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Prerequisites dialog box
ms.assetid: 53ac863c-77a0-409b-91e5-7a4bd8b8474e
caps.latest.revision: 79
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b8e5e004d2e337900d88f72d92bfd439103b87e0
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297841"
---
# <a name="prerequisites-dialog-box"></a>必要條件對話方塊
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

這個對話方塊可指定已安裝的必要條件元件、安裝方式，以及套件的安裝順序。

 若要存取這個對話方塊，請選取方案總管  中的專案節點，然後按一下 [專案]  功能表上的 [屬性]  。 當 [ **專案設計工具** ] 出現時，請按一下 [ **發行** ] 索引標籤。在 [發行]  頁面上，按一下 [必要條件]  。 針對安裝專案，按一下 [專案]  功能表上的 [屬性]  。 出現 [屬性頁]  對話方塊時，按一下 [必要條件]  。

## <a name="uielement-list"></a>UIElement 清單

|項目|說明|
|-------------|-----------------|
|**建立安裝程式以安裝必要條件元件**|將必要條件元件包含在應用程式的安裝程式 (Setup.exe) 中，才能在安裝應用程式之前，依照相依性的順序進行安裝。 根據預設，這個選項是選取的。 如果沒有選取這個選項，則不會建立 Setup.exe。|
|**選擇要安裝的必要條件**|指定是否要安裝元件，例如 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]、Crystal Reports 等。<br /><br /> 例如，選取 [SQL Server 2005 Express Edition SP2]  旁的核取方塊，即指定安裝程式確認這個元件是否已安裝在目標電腦上，如果尚未安裝就會進行安裝。<br /><br /> 如需各個必要條件套件的詳細資訊，請參閱本主題稍後的「必要條件資訊」表格。|
|**檢查 Microsoft Update 以取得更多可轉散發元件**|按一下這個連結會帶您前往[啟動載入器套件轉散發元件](https://go.microsoft.com/fwlink/?LinkId=208835)網站，以檢查更新。|
|**從元件廠商的網站下載必要條件**|指定從廠商的網站安裝必要條件元件。 這是預設選項。|
|**從應用程式的相同位置下載必要條件**|指定從應用程式的相同位置安裝必要條件元件。 這個選項會將所有的必要條件套件複製到發行位置。 必要條件套件必須放在開發電腦上，這個選項才能正常運作。|
|**從下列位置下載必要條件**|指定從您選取的位置安裝必要條件元件。 您可以使用 [瀏覽]  按鈕來選取位置。|

## <a name="prerequisites-information"></a>必要條件資訊
 [必要條件]  對話方塊中顯示的必要條件元件，可能和以下所列的不同。 第一次開啟該對話方塊時，會自動設定**必要條件對話方塊**中所列的必要條件套件。 如果您接著變更專案的目標架構，您就必須手動選取必要條件以符合新的目標架構。

|項目|說明|
|-------------|-----------------|
|**.NET Framework 3.5 SP1**|這個套件會安裝下列項目：<br /><br /> -   .NET Framework 2.0、3.0 和 3.5 版。<br />-   支援 32 位元 (x86) 及 64 位元 (x64) 作業系統上的所有 .NET Framework 版本。<br />-   隨著這個套件一併安裝之每個 .NET Framework 版本的語言套件。<br />-   .NET Framework 2.0 及 3.0 的 Service Pack。<br /><br /> .NET Framework 3.0 隨附於 Windows Vista，.NET Framework 3.5 則隨附於 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。 所有針對 32 位元作業系統編譯，而且目標架構設定為 [.NET Framework 3.5]  的 Visual Basic 和 Visual C# 專案，以及針對 64 位元作業系統編譯的 Visual Basic 和 Visual C# 專案，都需要 .NET Framework 3.5 (不支援 IA64)。請注意，根據預設，Visual Basic 和 Visual C# 專案是針對任何 CPU 架構編譯。 如需詳細資訊，請參閱 [Visual Studio 多目標概觀](../../ide/visual-studio-multi-targeting-overview.md)、[轉散發 .NET Framework](https://msdn.microsoft.com/a18d0456-fd89-493e-97f4-756505bfe287) 和 [64 位元應用程式的部署必要條件](../../deployment/deploying-prerequisites-for-64-bit-applications.md)。<br /><br /> 這個項目預設為選取。|
|**.NET Framework 3.5 SP1 Client Profile**|.NET Framework Client Profile 是完整 .NET Framework 3.5 SP1 的子集，以用戶端應用程式為目標。 它提供了 Windows Presentation Foundation (WPF)、Windows Forms、Windows Communication Foundation (WCF) 以及 ClickOnce 功能的精簡子集。 這樣可以快速部署以 .NET Framework Client Profile 為目標的 WPF、Windows Form、WCF 及主控台應用程式。 如需詳細資訊，請參閱 [.NET Framework Client Profile](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1)。|
|**Microsoft .NET Framework 4 (x86 和 x64)**|這個套件會在 x86 和 x64 平台安裝 .NET Framework 4。<br /><br /> 如需詳細資訊，請參閱 [Visual Studio 多目標概觀](../../ide/visual-studio-multi-targeting-overview.md)、[轉散發 .NET Framework](https://msdn.microsoft.com/a18d0456-fd89-493e-97f4-756505bfe287) 和 [64 位元應用程式的部署必要條件](../../deployment/deploying-prerequisites-for-64-bit-applications.md)。<br /><br /> 這個項目預設為選取。|
|**Microsoft .NET Framework 4 Client Profile (x86 和 x64)**|.NET Framework 4 Client Profile 是完整 .NET Framework 4 的子集，以用戶端應用程式為目標。 它提供了 Windows Presentation Foundation (WPF)、Windows Forms、Windows Communication Foundation (WCF) 以及 ClickOnce 功能的精簡子集。 這樣可以快速部署以 .NET Framework 4 Client Profile 為目標的 WPF、Windows Form 及主控台應用程式。 如需詳細資訊，請參閱 [.NET Framework Client Profile](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1)。|
|**Microsoft Office 2007 主要 Interop 組件**|這個套件會安裝 2007 Microsoft Office 產品的主要 Interop 組件。 主要 Interop 組件可讓 Managed 程式碼與 Microsoft Office 應用程式的 COM 物件模型互動。 如需詳細資訊，請參閱 [Office 主要 Interop 組件](https://msdn.microsoft.com/library/aa29d12c-185f-4558-a7cd-3d85f924203d)。|
|**Microsoft Visual Basic PowerPacks 10.0 版**|Power Pack 是可協助您開發 Visual Basic 應用程式的增益集 (Add-In)、控制項、元件及工具。 此版本包含[PrintForm](/previous-versions/bb882742(v=vs.140))元件，可讓您列印 Windows Form 的內容，以及印表機相容性程式庫，讓 Visual Basic 6.0 印表機程式碼以未修改的形式執行。|
|**Microsoft Visual F# Runtime for .NET 2.0**|這個套件會安裝 x86 和 x64 作業系統適用的 Visual F# 執行階段程式庫，此程式庫可支援函式程式設計，以及傳統物件導向程式設計與命令式 (程序式) 的程式設計。 如果應用程式或其元件是以 Visual F# 和 .NET Framework 2.0、.NET Framework 3.0 或 .NET Framework 3.5 撰寫的，必須先安裝這個套件。<br /><br /> 如需詳細資訊，請參閱 [F# 語言參考](https://msdn.microsoft.com/library/16b706f8-b5f2-4ff7-b2c1-64df33cd6adf)。|
|**Microsoft Visual F# Runtime for .NET 4.0**|這個套件會安裝 x86 和 x64 作業系統適用的 Visual F# 執行階段程式庫，此程式庫可支援函式程式設計，以及傳統物件導向程式設計與命令式 (程序式) 的程式設計。 如果應用程式或其元件是以 Visual F# 和 .NET Framework 4 撰寫的，必須安裝這個套件。<br /><br /> 如需詳細資訊，請參閱 [F# 語言參考](https://msdn.microsoft.com/library/16b706f8-b5f2-4ff7-b2c1-64df33cd6adf)。|
|**Microsoft Visual Studio 2010 Report Viewer**|本套件會安裝報表檢視器控制項，可以將大量的資料報表加入至 Windows Form 和 ASP.NET 應用程式。|
|**Microsoft Visual Studio 2010 for Office Runtime (x86 和 x64)**|Visual Studio 中的 Office Developer Tools 提供便於使用的整合式工具，可搭配 Microsoft Office 建立自訂商務方案。 您可以建立使用 Office 應用程式做為使用者介面的 Managed 智慧型用戶端解決方案。 這些工具讓開發人員能夠建立易於部署與維護的安全方案。<br /><br /> 如需詳細資訊，請參閱[如何：使用 ClickOnce 發行 Office 方案](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)。|
|**SQL Server 2005 Express Edition SP2 (x86)**|這個套件會安裝 Microsoft SQL Server 2005 Express Edition SP2，這是以 [!INCLUDE[sqprsqext](../../includes/sqprsqext-md.md)] 為基礎的資料庫應用程式。 SQL Server Express 是 Microsoft SQL Server Desktop Engine (MSDE) 的取代項目。 SQL Server Express 是免費的而且可轉散發 (依合約規定)，可以當做用戶端資料庫以及基本伺服器資料庫。 與 SQL Server 2005 相同，除了以下幾個不同處：<br /><br /> -   不支援企業功能。<br />-   只限於一個 CPU。<br />-   緩衝區集區的記憶體限制為 1 GB。<br />-   資料庫大小上限為 4 GB。|
|**SQL Server 2008 Express**|此套件會安裝 Microsoft SQL Server 2008 Express (Microsoft SQL Server 2008 的免費版本)，這是小型網路、伺服器或桌面應用程式的理想資料庫。 它可以免費用於開發和生產環境。 隨同應用程式散發 SQL Server 2008 Express 時，必須有免費的註冊。<br /><br /> 啟動載入器的行為如下：<br /><br /> -   如果電腦已有 SQL Server 2008 Express (含) 以後版本，則電腦會保持在 SQL Server 2008 Express (含) 以後版本。<br />-   如果電腦沒有任何 SQL Server 2008 Express (含) 以後版本，則套件會安裝最新版的 SQL Server 2008 Express SP1。<br /><br /> 若要深入了解 SQL Server 2008 Express，請瀏覽 [http://go.microsoft.com/fwlink/?LinkId=183586](https://go.microsoft.com/fwlink/?LinkId=183586)。|
|**Visual C++ 2010 執行階段程式庫 (IA64)**|這個套件會安裝適用於 Itanium 架構的 Visual C++ 執行階段程式庫，以提供 Microsoft Windows 作業系統程式設計所需的常式。 這些常式會自動執行 C 和 C++ 語言所未提供的許多常見的程式設計工作。<br /><br /> 如需詳細資訊，請參閱 [C 執行階段程式庫參考](https://msdn.microsoft.com/library/a503e11c-8dca-4846-84fb-025a826c32b8)。|
|**Visual C++ 2010 執行階段程式庫 (x64)**|這個套件會安裝適用於 x64 作業系統的 Visual C++ 執行階段程式庫，以提供 Microsoft Windows 作業系統程式設計所需的常式。 這些常式會自動執行 C 和 C++ 語言所未提供的許多常見的程式設計工作。<br /><br /> 如需詳細資訊，請參閱 [C 執行階段程式庫參考](https://msdn.microsoft.com/library/a503e11c-8dca-4846-84fb-025a826c32b8)。|
|**Visual C++ 2010 執行階段程式庫 (x86)**|這個套件會安裝適用於 x86 作業系統的 Visual C++ 執行階段程式庫，以提供 Microsoft Windows 作業系統程式設計所需的常式。 這些常式會自動執行 C 和 C++ 語言所未提供的許多常見的程式設計工作。<br /><br /> 如需詳細資訊，請參閱 [C 執行階段程式庫參考](https://msdn.microsoft.com/library/a503e11c-8dca-4846-84fb-025a826c32b8)。|
|**Windows Installer 3.1**|這個套件會安裝 Microsoft Windows Installer 可轉散發套件 3.1 版，以允許安裝 Windows Installer 安裝專案。 Windows Server 2003 SP1 (含) 以後版本都會預先安裝這個套件。<br /><br /> 這個項目預設為選取。|
|**Windows Installer 4.5**|這個套件會安裝 Microsoft Windows Installer 可轉散發套件 4.5 版，以允許安裝 Windows Installer 安裝專案。|

## <a name="see-also"></a>另請參閱
 [發行頁面、專案設計](../../ide/reference/publish-page-project-designer.md)工具[應用程式部署必要條件](../../deployment/application-deployment-prerequisites.md)轉散發 [.NET Framework](https://msdn.microsoft.com/a18d0456-fd89-493e-97f4-756505bfe287) [部署64位應用程式的必要條件](../../deployment/deploying-prerequisites-for-64-bit-applications.md) [Visual Studio 多目標總覽](../../ide/visual-studio-multi-targeting-overview.md)
