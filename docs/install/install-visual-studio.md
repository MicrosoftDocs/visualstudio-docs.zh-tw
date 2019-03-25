---
title: 安裝 Visual Studio
titleSuffix: ''
description: 了解如何逐步安裝 Visual Studio。
ms.date: 02/11/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf1497e79b6f41104664013efcf63adea5223f11
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "57983542"
---
# <a name="install-visual-studio"></a>安裝 Visual Studio

歡迎使用安裝 Visual Studio 的新方式！ 在此版本中，您能夠更輕鬆地選取和安裝所需的功能。 我們也已經減少 Visual Studio 的最少使用量，使它能以更快的速度完成安裝，並對系統產生較少的影響。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱[安裝 Visual Studio for Mac](/visualstudio/mac/installation)。

是否想要深入了解此版本的其他新功能？ 請參閱[版本資訊](/visualstudio/releasenotes/vs2017-relnotes)。

準備要安裝了嗎？ 我們將逐步引導完成安裝。

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>步驟 1：請確定您的電腦已準備好安裝 Visual Studio

在您開始安裝 Visual Studio 之前：

1. 檢查[系統需求](/visualstudio/productinfo/vs2017-system-requirements-vs)。 這些需求可以協助確定您的電腦是否支援 Visual Studio 2017。
2. 套用最新的 Windows 更新。 這些更新可以確保您的電腦已具備最新的安全性更新，以及 Visual Studio 所需的系統元件。
3. 重新開機。 重新開機可以確保不會有任何擱置的安裝或更新會阻礙 Visual Studio 安裝。
4. 釋出空間。 透過執行 [磁碟清理] 應用程式之類的方式，將不必要的檔案及應用程式從 %SystemDrive% 移除。

針對並存執行舊版 Visual Studio 及 Visual Studio 2017 的相關問題，請參閱 [Visual Studio 相容性詳細資料](/visualstudio/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases)。

## <a name="step-2---download-visual-studio"></a>步驟 2：下載 Visual Studio

接下來，請下載 Visual Studio 啟動載入器檔案。 若要這麼做，請按一下下方的按鈕，選取想要的 Visual Studio 2017 版本，按一下 [儲存]，然後按一下 [開啟資料夾]。

 > [!div class="button"]
 > [下載 Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
<br/>

## <a name="step-3---install-the-visual-studio-installer"></a>步驟 3：安裝 Visual Studio 安裝程式

接著，請執行啟動載入器檔案以安裝 Visual Studio 安裝程式。 這個全新的輕量化安裝程式包含了安裝及自訂 Visual Studio 2017 所需的所有內容。

1. 從您的 [下載] 資料夾中，按兩下符合或類似於下列其中一項檔案的啟動載入器：

   * **vs_enterprise.exe** (適用於 Visual Studio Enterprise)
   * **vs_professional.exe** (適用於 Visual Studio Professional)
   * **vs_community.exe** (適用於 Visual Studiofor Community)  <br><br>

   如果您收到 [使用者帳戶控制] 通知，請按一下 [是]。

2. 我們將會要求您認可 Microsoft [授權條款](https://visualstudio.microsoft.com/license-terms/)和 Microsoft [隱私權聲明](https://privacy.microsoft.com/privacystatement)。 按一下 [ **繼續**]。

   ![授權條款和隱私權聲明](media/vs2017-privacy-and-license-terms.PNG "Microsoft 授權條款和隱私權聲明")

## <a name="step-4---select-workloads"></a>步驟 4：選取工作負載

在安裝程式安裝完畢之後，您可以利用它來選取所需的功能集 (或工作負載) 以自訂您的安裝。 方式如下：

1. 在 [安裝 Visual Studio] 畫面中找到您想要的工作負載。

   ![從 Visual Studio 2017 設定對話方塊中選取工作負載](../install/media/install-visual-studio-community.png)

     例如，選擇「.NET 桌面開發」工作負載。 它隨附預設核心編輯器，其中包括超過 20 種語言的基本程式碼編輯支援、能夠從任何資料夾開啟及編輯程式碼而不需要專案，以及整合的原始程式碼控制。

2. 選取您想要的工作負載之後，按一下 [安裝]。

    接著會出現狀態畫面，顯示 Visual Studio 的安裝進度。

3. 安裝新的工作負載和元件之後，按一下 [啟動]。

> [!TIP]
> 您可以在安裝後，隨時安裝一開始未安裝的工作負載或元件。 如果您已開啟 Visual Studio，請移至 [工具] > [Get Tools and Features] (取得工具和功能)，以開啟 Visual Studio 安裝程式。 或者，從 [開始] 功能表開啟 [Microsoft Visual Studio 安裝程式]。 您可以從該處選取想要安裝的工作負載或元件，然後按一下 [修改]。

## <a name="step-5---select-individual-components-optional"></a>步驟 5：選取個別元件 (選擇性)

如果您不想要使用 [工作負載] 功能來自訂 Visual Studio 安裝，則可以改為安裝個別的元件。 若要選取個別元件，請按一下 Visual Studio 安裝程式中的 [個別元件] 選項，選取所需的項目，然後遵循提示執行。

  ![Visual Studio 2017 - 安裝個別元件](media/vs2017-components.PNG "安裝 Visual Studio 的個別元件")

## <a name="step-6---install-language-packs-optional"></a>步驟 6：安裝語言套件 (選擇性)

根據預設，安裝程式會在第一次執行時，嘗試比對作業系統的語言。 若要以您選擇的語言安裝 Visual Studio 2017，請從「Visual Studio 安裝程式」按一下 [語言套件] 選項，然後依照提示進行操作。

  ![Visual Studio 2017 - 安裝語言套件](media/vs2017-languages.PNG "安裝 Visual Studio 語言套件")

### <a name="change-the-installer-language-from-the-command-line"></a>從命令列變更安裝程式語言

另一個變更預設語言的方法，便是從命令列執行安裝程式。 例如，您可以使用下列命令來強制安裝程式以英文執行：`vs_installer.exe --locale en-US`。 下次執行安裝程式時，它會記住這項設定。 安裝程式支援下列語言權杖：zh-cn、zh-tw、cs-cz、en-us、es-es、fr-fr、de-de、it-it、ja-jp、ko-kr、pl-pl、pt-br、ru-ru 和 tr-tr。

## <a name="step-7---change-the-installation-location-optional"></a>步驟 7 - 變更安裝位置 (選擇性)

**15.7 版中的新功能**：現在您可以減少 Visual Studio 在系統磁碟機上的安裝磁碟使用量。 您可以選擇將快取、共用元件、SDK 和工具下載至不同的磁碟機，並將 Visual Studio 保留在以最快速度執行它的磁碟機上。

  ![Visual Studio 2017 - 變更安裝位置](media/installation-options-by-location.png "變更安裝位置")

如需詳細資訊，請參閱[變更 Visual Studio 中的安裝位置](change-installation-locations.md)頁面。

## <a name="step-8---start-developing"></a>步驟 8 - 開始開發

1. 當 Visual Studio 安裝完成之後，請按一下 [啟動] 按鈕來開始使用 Visual Studio 進行開發。

2. 按一下 [檔案]，然後按一下 [新增專案]。

3. 選取專案類型。

   例如，若要[建置 C++ 應用程式](../ide/getting-started-with-cpp-in-visual-studio.md)，請按一下 [已安裝]，展開 [Visual C++]，然後選取您要建置的 C++ 專案類型。

   若要[建置 C# 應用程式](../get-started/csharp/tutorial-wpf.md)，請按一下 [已安裝]，展開 [Visual C#]，然後選取您要建置的 C# 專案類型。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [更新 Visual Studio](update-visual-studio.md)
* [修改 Visual Studio](modify-visual-studio.md)
* [解除安裝 Visual Studio](uninstall-visual-studio.md)
* [建立 Visual Studio 的離線安裝](create-an-offline-installation-of-visual-studio.md)
* [使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [安裝 Visual Studio for Mac](/visualstudio/mac/installation)