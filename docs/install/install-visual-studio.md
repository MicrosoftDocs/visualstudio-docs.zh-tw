---
title: 安裝 Visual Studio
titleSuffix: ''
description: 了解如何逐步安裝 Visual Studio。
ms.date: 12/13/2019
ms.custom: contperf-fy21q1
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 97e354dfb1208ec7306cb797049cd8ca82d0d8db
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852113"
---
# <a name="install-visual-studio"></a>安裝 Visual Studio

::: moniker range="vs-2019"

歡迎使用 Visual Studio 2019！ 在此版本中，您可以輕鬆選擇並安裝需要的功能。 因為降低了磁碟使用量下限，所以安裝快速，且對系統影響更小。

::: moniker-end

::: moniker range="vs-2017"

歡迎使用安裝 Visual Studio 的新方式！ 在此版本中，我們讓您能更輕鬆選取及安裝需要的功能。 我們也已經減少 Visual Studio 的最少使用量，使它能以更快的速度完成安裝，並對系統產生較少的影響。

::: moniker-end

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱[安裝 Visual Studio for Mac](/visualstudio/mac/installation/)。

::: moniker range="vs-2019"

是否想要深入了解此版本的其他新功能？ 請參閱[版本資訊](/visualstudio/releases/2019/release-notes/)。

::: moniker-end

::: moniker range="vs-2017"

是否想要深入了解此版本的其他新功能？ 請參閱[版本資訊](/visualstudio/releasenotes/vs2017-relnotes)。

::: moniker-end

準備要安裝了嗎？ 我們將逐步引導完成安裝。

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>步驟 1：請確定您的電腦已準備好安裝 Visual Studio

在您開始安裝 Visual Studio 之前：

::: moniker range="vs-2017"

1. 檢查[系統需求](/visualstudio/productinfo/vs2017-system-requirements-vs)。 這些需求可以協助確定您的電腦是否支援 Visual Studio 2017。

1. 套用最新的 Windows 更新。 這些更新可以確保您的電腦已具備最新的安全性更新，以及 Visual Studio 所需的系統元件。

1. 重新開機。 重新開機可以確保不會有任何擱置的安裝或更新會阻礙 Visual Studio 安裝。

1. 釋出空間。 透過執行 [磁碟清理] 應用程式之類的方式，將不必要的檔案及應用程式從 %SystemDrive% 移除。

::: moniker-end

::: moniker range="vs-2019"

1. 檢查[系統需求](/visualstudio/releases/2019/system-requirements)。 這些需求可以幫助您了解電腦是否支援 Visual Studio 2019。

1. 套用最新的 Windows 更新。 這些更新可以確保您的電腦已具備最新的安全性更新，以及 Visual Studio 所需的系統元件。

1. 重新開機。 重新開機可以確保不會有任何擱置的安裝或更新會阻礙 Visual Studio 安裝。

1. 釋出空間。 透過執行 [磁碟清理] 應用程式之類的方式，將不必要的檔案及應用程式從 %SystemDrive% 移除。

::: moniker-end

::: moniker range="vs-2017"

針對並存執行舊版 Visual Studio 及 Visual Studio 2017 的相關問題，請參閱 [Visual Studio 相容性詳細資料](/visualstudio/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases)。

::: moniker-end

::: moniker range="vs-2019"

如有並存執行舊版 Visual Studio 及 Visual Studio 2019 的相關問題，請參閱 [Visual Studio 2019 平台目標及相容性](/visualstudio/releases/2019/compatibility/)頁面。

::: moniker-end

## <a name="step-2---download-visual-studio"></a>步驟 2：下載 Visual Studio

接下來，請下載 Visual Studio 啟動載入器檔案。

::: moniker range="vs-2017"

若要取得 Visual Studio 2017 的啟動載入器，請參閱 [Visual Studio 舊版](https://visualstudio.microsoft.com/vs/older-downloads/) 下載頁面，以取得如何進行這項操作的詳細資訊。

::: moniker-end

::: moniker range="vs-2019"

若要這麼做，請依序選擇下列按鈕、您想要的 Visual Studio 版本、[儲存] 和 [開啟資料夾]。

 > [!div class="button"]
 > [下載 Visual Studio](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="step-3---install-the-visual-studio-installer"></a>步驟 3：安裝 Visual Studio 安裝程式

執行啟動載入器檔案以安裝 Visual Studio 安裝程式。 這個新輕量型安裝程式包含安裝及自訂 Visual Studio 所需的全部內容。

1. 從您的 [下載] 資料夾中，按兩下符合或類似於下列其中一項檔案的啟動載入器：

   * **vs_community.exe** (適用於 Visual Studiofor Community)
   * **vs_professional.exe** (適用於 Visual Studio Professional)
   * **vs_enterprise.exe** (適用於 Visual Studio Enterprise)

   如果您收到使用者帳戶控制通知，請選擇 [是]。

2. 我們將會要求您認可 Microsoft [授權條款](https://visualstudio.microsoft.com/license-terms/)和 Microsoft [隱私權聲明](https://privacy.microsoft.com/privacystatement)。 選擇 [繼續]。

   ![授權條款和隱私權聲明](media/privacy-and-license-terms.png "Microsoft 授權條款和隱私權聲明")

## <a name="step-4---choose-workloads"></a>步驟 4 - 選擇工作負載

在安裝程式安裝完畢之後，您可以利用它來選取所需的功能集 (或工作負載) 以自訂您的安裝。 方法如下。

 ::: moniker range="vs-2017"

1. 在 **Visual Studio 安裝程式** 中尋找您想要的工作負載。

   ![Visual Studio 2017：安裝工作負載](../install/media/vs-installer-installing-workloads.png)

     例如，選擇「.NET 桌面開發」工作負載。 它隨附預設核心編輯器，其中包括超過 20 種語言的基本程式碼編輯支援、能夠從任何資料夾開啟及編輯程式碼而不需要專案，以及整合的原始程式碼控制。

1. 選擇您想要的工作負載之後，再選擇 [安裝]。

    接著會出現狀態畫面，顯示 Visual Studio 的安裝進度。

 ::: moniker-end

::: moniker range="vs-2019"

1. 在 **Visual Studio 安裝程式** 中尋找您想要的工作負載。

   ![Visual Studio 2019：安裝工作負載](../install/media/vs-2019/vs-installer-workloads.png)

     例如，選擇 [ASP.NET 與網頁程式開發] 工作負載。 它隨附預設核心編輯器，其中包括超過 20 種語言的基本程式碼編輯支援、能夠從任何資料夾開啟及編輯程式碼而不需要專案，以及整合的原始程式碼控制。

1. 選擇您想要的工作負載之後，再選擇 [安裝]。

    接著會出現狀態畫面，顯示 Visual Studio 的安裝進度。

 ::: moniker-end

> [!TIP]
> 您可以在安裝後，隨時安裝一開始未安裝的工作負載或元件。 如果您已 Visual Studio 開啟，請移至 [**工具**  >  **取得工具和功能**]，這會開啟 Visual Studio 安裝程式。 或者，從 [開始] 功能表開啟 [Microsoft Visual Studio 安裝程式]。 您可以在此選擇想要安裝的工作負載或元件。 然後，選擇 [修改]。

## <a name="step-5---choose-individual-components-optional"></a>步驟 5：選取個別元件 (選擇性)

如果您不想要使用 [工作負載] 功能來自訂 Visual Studio 安裝，或想要新增超過工作負載安裝的元件，您可以從 [ **個別元件** ] 索引標籤安裝或新增個別元件來執行此作業。選擇您想要的內容，然後遵循提示進行。

::: moniker range="vs-2017"

  ![Visual Studio 2017-安裝個別元件](media/vs-installer-installing-components.png "安裝 Visual Studio 的個別元件")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual Studio 2019-安裝個別元件](media/vs-2019/vs-installer-individual-components.png "安裝 Visual Studio 的個別元件")

::: moniker-end

## <a name="step-6---install-language-packs-optional"></a>步驟 6：安裝語言套件 (選擇性)

根據預設，安裝程式會在第一次執行時，嘗試比對作業系統的語言。 若要以您選擇的語言安裝 Visual Studio，請選擇 Visual Studio 安裝程式的 [語言套件] 索引標籤，然後遵循提示作業。

::: moniker range="vs-2017"

  ![Visual Studio 2017-安裝語言套件](media/vs-installer-installing-language-packs.png "安裝 Visual Studio 語言套件")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual Studio 2019-安裝語言套件](media/vs-2019/vs-installer-language-packs.png "安裝 Visual Studio 語言套件")

::: moniker-end

### <a name="change-the-installer-language-from-the-command-line"></a>從命令列變更安裝程式語言

另一個變更預設語言的方法，便是從命令列執行安裝程式。 例如，您可以使用下列命令來強制安裝程式以英文執行：`vs_installer.exe --locale en-US`。 下次執行安裝程式時，它會記住這項設定。 安裝程式支援下列語言權杖：zh-cn、zh-tw、cs-cz、en-us、es-es、fr-fr、de-de、it-it、ja-jp、ko-kr、pl-pl、pt-br、ru-ru 和 tr-tr。

## <a name="step-7---select-the-installation-location-optional"></a>步驟 7 - 選取安裝位置 (選擇性)

::: moniker range="vs-2017"

**15.7 的新功能**：現在您可以減少 Visual Studio 在系統磁碟機上的安裝使用量。 您可以選擇將快取、共用元件、SDK 和工具下載至不同的磁碟機，並將 Visual Studio 保留在以最快速度執行它的磁碟機上。

  ![Visual Studio 2017-變更安裝位置](media/installation-options-by-location.png "變更安裝位置")

::: moniker-end

::: moniker range="vs-2019"

您可以減少系統磁碟機上的 Visual Studio 安裝磁碟使用量。 您可以選擇將快取、共用元件、SDK 和工具下載至不同的磁碟機，並將 Visual Studio 保留在以最快速度執行它的磁碟機上。

  ![Visual Studio 2019-選取安裝位置](media/vs-2019/vs-installer-installation-locations.png "選取安裝位置")

::: moniker-end

> [!IMPORTANT]
> 您只有在第一次安裝 Visual Studio 時才可以選取不同的磁碟機。 如已安裝 Visual Studio 並想要變更磁碟機，您必須解除安裝它，再重新安裝。

如需詳細資訊，請參閱[選取安裝位置](change-installation-locations.md)頁面。

## <a name="step-8---start-developing"></a>步驟 8 - 開始開發

::: moniker range="vs-2017"

1. 在完成 Visual Studio 安裝後，請選擇 [啟動] 按鈕以開始使用 Visual Studio 來進行開發。

2. 選取 [檔案]，然後選擇 [新增專案]。

3. 選取專案類型。

   例如，若要[建置 C++ 應用程式](/cpp/get-started/tutorial-console-cpp)，請選擇 [已安裝]，展開 [Visual C++]，然後選擇您要建置的 C++ 專案類型。

   若要[建置 C# 應用程式](../get-started/csharp/tutorial-console.md)，請選擇 [已安裝]，展開 [Visual C#]，然後選擇您要建置的 C# 專案類型。

::: moniker-end

::: moniker range="vs-2019"

1. 在完成 Visual Studio 安裝後，請選擇 [啟動] 按鈕以開始使用 Visual Studio 來進行開發。

1. 在 [開始] 視窗中，選擇 [ **建立新專案**]。

1. 在搜尋方塊中，輸入您想要建立的應用程式類型，以查看可用的範本清單。 範本清單取決於您在安裝期間所選擇的工作負載。 若要查看不同的範本，請選擇不同的工作負載。

   您也可以使用 [語言] 下拉式清單來篩選搜尋特定的程式設計語言。 您也可以使用 [平台] 清單和 [專案類型] 清單來篩選。

1. Visual Studio 會開啟您的新專案，而您已準備好撰寫程式碼！

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [更新 Visual Studio 2017](update-visual-studio.md)
* [修改 Visual Studio 2017](modify-visual-studio.md)
* [解除安裝 Visual Studio](uninstall-visual-studio.md)
* [建立 Visual Studio 的離線安裝](create-an-offline-installation-of-visual-studio.md)
* [使用命令列參數來安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [安裝 Visual Studio for Mac](/visualstudio/mac/installation)
 