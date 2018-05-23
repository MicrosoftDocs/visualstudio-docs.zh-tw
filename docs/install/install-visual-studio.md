---
title: 安裝 Visual Studio 2017 | Microsoft Docs
description: 了解如何逐步安裝 Visual Studio。
ms.custom: ''
ms.date: 05/07/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ee4a75ba456184ffe48cb59f77668625acf673d1
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
---
# <a name="install-visual-studio-2017"></a>安裝 Visual Studio 2017

歡迎使用安裝 Visual Studio 的新方式！ 在這個最新的版本之中，您將能更輕鬆地選取和安裝所需的功能。 我們也已經減少 Visual Studio 的最少使用量，使它能以更快的速度完成安裝，並對系統產生較少的影響。

是否想要深入了解此版本的其他新功能？ 請參閱[版本資訊](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes)。

準備要安裝了嗎？ 我們將逐步引導完成安裝。

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>步驟 1：請確定您的電腦已準備好安裝 Visual Studio

在您開始安裝 Visual Studio 之前：

1. 檢查[系統需求](https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs)。 這些需求可以協助確定您的電腦是否支援 Visual Studio 2017。
2. 套用最新的 Windows 更新。 這些更新可以確保您的電腦已具備最新的安全性更新，以及 Visual Studio 所需的系統元件。
3. 重新開機。 重新開機可以確保不會有任何擱置的安裝或更新會阻礙 Visual Studio 安裝。
4. 釋出空間。 透過執行 [磁碟清理] 應用程式之類的方式，將不必要的檔案及應用程式從 %SystemDrive% 移除。

針對並存執行舊版 Visual Studio 及 Visual Studio 2017 的相關問題，請參閱 [Visual Studio 相容性詳細資料](https://www.visualstudio.com/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases)。

## <a name="step-2---download-visual-studio"></a>步驟 2：下載 Visual Studio

接下來，請下載 Visual Studio 啟動載入器檔案。 若要這麼做，請按一下下方的按鈕，選取想要的 Visual Studio 2017 版本，按一下 [儲存]，然後按一下 [開啟資料夾]。

 > [!div class="button"]
 > [下載 Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
<br/>

|         |         |
|---------|---------|
|  ![影片的電影攝影機圖示](media/video-icon.png "觀看影片")  |    [觀看影片](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Download-the-Visual-Studio-Installer-GgrESHD6D_3311787171) \(英文\) 以了解如何下載 Visual Studio 啟動載入器檔案，並選取適合您的 Visual Studio 版本。 |

## <a name="step-3---install-the-visual-studio-installer"></a>步驟 3：安裝 Visual Studio 安裝程式

接著，請執行啟動載入器檔案以安裝 Visual Studio 安裝程式。 這個全新的輕量化安裝程式包含了安裝及自訂 Visual Studio 2017 所需的所有內容。

1. 從您的 [下載] 資料夾中，按兩下符合或類似於下列其中一項檔案的啟動載入器：

  * **vs_enterprise.exe** (適用於 Visual Studio Enterprise)
  * **vs_professional.exe** (適用於 Visual Studio Professional)
  * **vs_community.exe** (適用於 Visual Studiofor Community)  <br><br>

  如果您收到 [使用者帳戶控制] 通知，請按一下 [是]。

2. 我們將會要求您認可 Microsoft [授權條款](https://www.visualstudio.com/license-terms/)和 Microsoft [隱私權聲明](https://go.microsoft.com/fwlink/?LinkID=824704)。 按一下 [ **繼續**]。  

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

|         |         |
|---------|---------|
|  ![影片的電影攝影機圖示](media/video-icon.png "觀看影片")  |    [觀看影片](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Workloads-in-Visual-Studio-2017-jHE19HD6D_1611787171) \(英文\) 以了解如何安裝 Visual Studio 安裝程式並安裝工作負載。 |

## <a name="step-5---select-individual-components-optional"></a>步驟 5：選取個別元件 (選擇性)

如果您不想要使用 [工作負載] 功能來自訂 Visual Studio 安裝，則可以改為安裝個別的元件。 若要選取個別元件，請按一下 Visual Studio 安裝程式中的 [個別元件] 選項，選取所需的項目，然後遵循提示執行。

  ![Visual Studio 2017 - 安裝個別元件](media/vs2017-components.PNG "安裝 Visual Studio 的個別元件")

  |         |         |
  |---------|---------|
  |  ![影片的電影攝影機圖示](media/video-icon.png "觀看影片")  |   [觀看影片](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Components-in-Visual-Studio-2017-ZMfaVID6D_7411787171) \(英文\) 以了解如何使用 Visual Studio 安裝程式安裝個別元件。 |

## <a name="step-6---install-language-packs-optional"></a>步驟 6：安裝語言套件 (選擇性)

根據預設，安裝程式會在第一次執行時，嘗試比對作業系統的語言。 若要以您選擇的語言安裝 Visual Studio 2017，請從「Visual Studio 安裝程式」按一下 [語言套件] 選項，然後依照提示進行操作。

  ![Visual Studio 2017 - 安裝語言套件](media/vs2017-languages.PNG "安裝 Visual Studio 語言套件")

  |         |         |
  |---------|---------|
  |  ![影片的電影攝影機圖示](media/video-icon.png "觀看影片")  |   [觀看影片](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Language-Packs-in-Visual-Studio-2017-ByT7yID6D_9011787171) \(英文\) 以了解如何使用 Visual Studio 安裝程式安裝語言套件。 |

### <a name="change-the-installer-language-from-the-command-line"></a>從命令列變更安裝程式語言

另一個變更預設語言的方法，便是從命令列執行安裝程式。 例如，您可以使用下列命令來強制安裝程式以英文執行：`vs_installer.exe --locale en-US`。 下次執行安裝程式時，它會記住這項設定。 安裝程式支援下列語言權杖：zh-cn、zh-tw、cs-cz、en-us、es-es、fr-fr、de-de、it-it、ja-jp、ko-kr、pl-pl、pt-br、ru-ru 和 tr-tr。

## <a name="step-7---change-the-installation-location-optional"></a>步驟 7 - 變更安裝位置 (選擇性)

**15.7 的新功能**：現在您可以減少 Visual Studio 在系統磁碟機上的安裝使用量。 您可以選擇將快取、共用元件、SDK 和工具下載至不同的磁碟機，並將 Visual Studio 保留在以最快速度執行它的磁碟機上。

  ![Visual Studio 2017 - 變更安裝位置](media/installation-options-by-location.png "變更安裝位置")

如需詳細資訊，請參閱[變更 Visual Studio 中的安裝位置](change-installation-locations.md)頁面。

## <a name="step-8---start-developing"></a>步驟 8 - 開始開發

1. 當 Visual Studio 安裝完成之後，請按一下 [啟動] 按鈕來[開始使用 Visual Studio 進行開發](../ide/get-started-developing-with-visual-studio.md)。

2. 按一下 [檔案]，然後按一下 [新增專案]。

3. 選取專案類型。 <br><br>
   例如，若要[建置 C++ 應用程式](../ide/getting-started-with-cpp-in-visual-studio.md)，請按一下 [已安裝]，展開 [Visual C++]，然後選取您要建置的 C++ 專案類型。 <br><br>
   若要[建置 C# 應用程式](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)，請按一下 [已安裝]，展開 [Visual C#]，然後選取您要建置的 C# 專案類型。

## <a name="get-support"></a>取得支援

有時可能會發生一些問題。 如果您的 Visual Studio 安裝失敗，請參閱[針對 Visual Studio 2017 安裝和升級問題進行疑難排解](troubleshooting-installation-issues.md)頁面。 如果所有疑難排解步驟都沒有幫助，您可以透過即時聊天與我們連絡，以取得安裝協助 (僅限英文)。 如需詳細資訊，請參閱 [Visual Studio 支援頁面](https://www.visualstudio.com/vs/support/#talktous) \(英文\)。

以下是一些支援選項：

* 您可以透過 Visual Studio 安裝程式和 Visual Studio IDE 中的[回報問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)工具來向我們報告產品問題。
* 您可以在 [UserVoice](https://visualstudio.uservoice.com/forums/121579) 上與我們分享產品建議。
* 您可以追蹤產品問題並在 [Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/) \(英文\) 中尋找解答。
* 您也可以透過[在 Gitter 社群中的 Visual Studio 交談](https://gitter.im/Microsoft/VisualStudio)，與我們以及其他 Visual Studio 開發人員進行互動。 (這個選項需要 [GitHub](https://github.com/) 帳戶)。

## <a name="see-also"></a>另請參閱

* [更新 Visual Studio 2017](update-visual-studio.md)
* [修改 Visual Studio 2017](modify-visual-studio.md)
* [解除安裝 Visual Studio 2017](uninstall-visual-studio.md)
* [建立 Visual Studio 2017 的離線安裝](create-an-offline-installation-of-visual-studio.md)
* [Visual Studio 2017 系統管理員指南](visual-studio-administrator-guide.md)
  * [使用命令列參數安裝 Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
* [將建置工具安裝至容器](build-tools-container.md)
