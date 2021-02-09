---
title: 必要條件對話方塊
description: '[必要條件] 對話方塊可指定已安裝的必要條件元件、安裝方式，以及套件的安裝順序。'
ms.custom: SEO-VS-2020
ms.date: 06/29/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
helpviewer_keywords:
- Prerequisites dialog box
author: Mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 78d5f4f00a81fccf573e69797b9d528ee61ffdc5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932055"
---
# <a name="prerequisites-dialog-box"></a>必要條件對話方塊

[必要條件] 對話方塊可指定已安裝的必要條件元件、安裝方式，以及套件的安裝順序。

![Visual Studio 中的必要條件對話方塊](media/prerequisites-dialog-box.png)

若要存取對話方塊，請選取 [方案總管] 中的專案節點，然後按一下 [專案] > [屬性]。 當 [專案設計工具] 出現時，請選取 [發佈] 索引標籤，然後選取 [必要條件]。 針對安裝專案，按一下 [專案] 功能表上的 [屬性]。 出現 [屬性頁] 對話方塊時，按一下 [必要條件]。

## <a name="uielement-list"></a>UIElement 清單

|元素|描述|
|-------------|-----------------|
|**建立安裝程式以安裝必要條件元件**|將必要條件元件包含在應用程式的安裝程式 (*Setup.exe*) 中，才能在安裝應用程式之前，依照相依性的順序進行安裝。 預設會選取這個選項。 如果沒有選取這個選項，則不會建立 *Setup.exe*。|
|**選擇要安裝的必要條件**|指定是否要安裝元件，例如 .NET Framework 和 C++ 執行階段程式庫。<br /><br />例如，選取 **SQL Server 2012 Express** 旁的核取方塊，即指定安裝程式必須確認這個元件是否已安裝在目標電腦上，如果尚未安裝就會進行安裝。<br /><br />如需各個必要條件套件的詳細資訊，請參閱[必要條件資訊](#prerequisites-information)。|
|**從元件廠商的網站下載必要條件**|指定從廠商的網站安裝必要條件元件。 這是預設選項。|
|**從應用程式的相同位置下載必要條件**|指定從應用程式的相同位置安裝必要條件元件。 這個選項會將所有的必要條件套件複製到發行位置。 必要條件套件必須放在開發電腦上，這個選項才能正常運作。|
|**從下列位置下載必要條件**|指定從您輸入的位置安裝必要條件元件。 您可以使用 [瀏覽] 按鈕來選取位置。|

> [!NOTE]
> 如需有關如何放置必要條件的詳細資訊，請參閱[建立啟動載入器套件](../../deployment/creating-bootstrapper-packages.md#create-custom-bootstrapper-packages)。

## <a name="prerequisites-information"></a>必要條件資訊

[必要條件] 對話方塊中顯示的必要條件元件，可能和以下所列的不同。 第一次開啟該對話方塊時，會自動設定 **必要條件對話方塊** 中所列的必要條件套件。 如果您接著變更專案的目標架構，您就必須手動選取必要條件以符合新的目標架構。

|元素|描述|
|-------------|-----------------|
|**.NET Framework 3.5 SP1**|這個套件會安裝下列項目：<br /><br /> -   .NET Framework 2.0、3.0 和 3.5 版。<br />-   支援 32 位元 (x86) 及 64 位元 (x64) 作業系統上的所有 .NET Framework 版本。<br />-   隨著這個套件一併安裝之每個 .NET Framework 版本的語言套件。<br />-   .NET Framework 2.0 及 3.0 的 Service Pack。<br /><br /> .NET Framework 3.0 隨附於 Windows Vista，.NET Framework 3.5 則隨附於 Visual Studio。 所有針對 32 位元作業系統編譯，而且目標架構設定為 [.NET Framework 3.5] 的 Visual Basic 和 C# 專案，以及針對 64 位元作業系統編譯的 Visual Basic 和 C# 專案，都需要 .NET Framework 3.5。 不支援 (IA64。 ) 請注意，根據預設，會針對任何 CPU 架構編譯 Visual Basic 和 c # 專案。 如需詳細資訊，請參閱 [Framework 目標概觀](../../ide/visual-studio-multi-targeting-overview.md)和 [64 位元應用程式的部署必要條件](../../deployment/deploying-prerequisites-for-64-bit-applications.md)。|
|**Microsoft .NET Framework 4.x**|這個套件會在 x86 和 x64 平台安裝 .NET Framework 4.x。|
|**Microsoft System CLR Types for SQL Server 2014 (x64 和 x86)**|此套件會安裝適用於 x64 或 x86 SQL Server 2014 的 Microsoft System CLR Types。|
|**SQL Server 2008 R2 Express**|此套件會安裝 Microsoft SQL Server 2008 R2 Express (Microsoft SQL Server 2008 R2 的免費版本)，這是適用於小型網路、伺服器或傳統型應用程式的理想資料庫。 它可以免費用於開發和生產環境。|
|**SQL Server 2012 Express**|此套件會安裝 Microsoft SQL Server 2012 Express。|
|**SQL Server 2012 Express LocalDB**|此套件會安裝 Microsoft SQL Server 2012 Express LocalDB。|
|**Visual C++ "14" 執行階段程式庫 (ARM)**|這個套件會安裝適用於 Itanium 架構的 Visual C++ 執行階段程式庫，以提供 Microsoft Windows 作業系統程式設計所需的常式。 這些常式將許多常見但 C 和 C++ 語言未提供的程式設計工作自動化。<br /><br /> 如需詳細資訊，請參閱 [C 執行階段程式庫參考](/cpp/c-runtime-library/c-run-time-library-reference)。|
|**Visual C++ "14" 執行階段程式庫 (x64)**|這個套件會安裝適用於 x64 作業系統的 Visual C++ 執行階段程式庫，以提供 Microsoft Windows 作業系統程式設計所需的常式。 這些常式將許多常見但 C 和 C++ 語言未提供的程式設計工作自動化。<br /><br /> 如需詳細資訊，請參閱 [C 執行階段程式庫參考](/cpp/c-runtime-library/c-run-time-library-reference)。|
|**Visual C++ "14" 執行階段程式庫 (x86)**|這個套件會安裝適用於 x86 作業系統的 Visual C++ 執行階段程式庫，以提供 Microsoft Windows 作業系統程式設計所需的常式。 這些常式將許多常見但 C 和 C++ 語言未提供的程式設計工作自動化。<br /><br /> 如需詳細資訊，請參閱 [C 執行階段程式庫參考](/cpp/c-runtime-library/c-run-time-library-reference)。|

## <a name="see-also"></a>另請參閱

- [專案設計工具、發行頁](../../ide/reference/publish-page-project-designer.md)
- [應用程式部署必要條件](../../deployment/application-deployment-prerequisites.md)
- [64 位元應用程式的部署必要條件](../../deployment/deploying-prerequisites-for-64-bit-applications.md)
- [Framework 目標概觀](../../ide/visual-studio-multi-targeting-overview.md)
