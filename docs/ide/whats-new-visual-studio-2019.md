---
title: Visual Studio 2019 Preview 的新功能
description: 深入了解 Visual Studio 2019 預覽版本中的新功能。
ms.custom: ''
ms.date: 12/04/2018
ms.prod: visual-studio-dev16
ms.technology: vs-acquisition
ms.topic: conceptual
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 838065d01e67f230d37ee318231371707117ec07
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2018
ms.locfileid: "52897182"
---
# <a name="what39s-new-in-visual-studio-2019-preview"></a>Visual Studio 2019 Preview 的新功能

**已針對 [16.0 Preview 1 版本](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)進行更新**

Visual Studio 2019 Preview 包含許多一般性改良，以及將開發人員生產力及小組共同作業最佳化的新功能。 無論您是第一次使用 Visual Studio 還是多年的使用者，皆能在開發週期的各種面向上利用其功能&mdash;從建立簡化的專案和程式碼健康狀態管理，到團隊與開放原始碼共同作業的工作流程。

以下是 Visual Studio 提供項目的概要回顧：

* **[個人和團隊生產力](#personal-and-team-productivity)**。 在每個人最需要時帶來生產力。
* **[新式開發支援](#modern-development-support)**。 支援您目前專案和未來的解決方案。
* **[持續創新](#continuous-innovation)**。 利用雲端等智慧支援項目，高效編寫程式碼。

> [!NOTE]
> 如需 Visual Studio 2019 Preview 中新功能的完整清單，請參閱[版本資訊](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)。

## <a name="personal-and-team-productivity"></a>個人和團隊生產力

改善效能是每個 Visual Studio 版本的首要考量，著重於提升您的生產力。 以下是我們可以提供協助的方法。

### <a name="new-start-window"></a>新的開始視窗

開啟 Visual Studio 2019 時，首先您會注意到新的開始視窗。

   ![Visual Studio 2019 中新的開始視窗](../ide/media/start-window.png)

這個新的開始視窗會顯示可供您複製或簽出程式碼、開啟專案或方案、開啟本機資料夾或建立新專案的選項。 在簡單的對話方塊中顯示這些選項，可協助初學者或熟悉 Visual Studio 的使用者快速編寫程式碼。

### <a name="better-search"></a>更佳的搜尋

先前稱為「快速啟動」，新的搜尋體驗將更快速且更有效。 現在，搜尋結果會隨著您的鍵入以動態方式顯示。 此外，搜尋結果會包含命令的鍵盤快速鍵，讓您輕鬆記憶，以便日後使用。

   ![Visual Studio 2019 中新的搜尋功能](../ide/media/search-feature.png)

不論您要尋找命令、設定、文件或其他使用項目，新搜尋功能可讓您更輕鬆找到您要尋找的內容。

### <a name="one-click-code-cleanup"></a>單擊程式碼清除

新的程式碼清除命令會與新文件健康狀態指標搭配。 您可以使用這個新的命令來找出警告與建議，並透過按一下按鈕進行修正。

   ![Visual Studio 2019 中新的程式碼清除功能](../ide/media/code-cleanup.png)

清除作業會將程式碼格式化，並套用由[目前的設定](../ide/code-styles-and-quick-actions.md)、[.editorconfig 檔案](../ide/create-portable-custom-editor-options.md)，或 [Roslyn 分析器](../code-quality/roslyn-analyzers-overview.md)所建議的任何程式碼修正。

### <a name="debugger-improvements"></a>改善偵錯工具

#### <a name="search-within-a-watch-window-and-format-watch-values"></a>在 [監看式] 視窗中搜尋，並將監看值格式化

在 [監看式] 視窗中查看一組值中的字串，您先前可能已進行過。 在 Visual Studio 2019 Preview 中，我們在 [監看式]、[區域變數] 和 [自動變數] 視窗中新增了搜尋功能，可協助您尋找物件和值。

在 [監看式]、[區域變數] 和 [自動變數] 視窗的顯示方式，您也能加以格式化。  在任一視窗中的其中一個項目上按兩下，並新增逗號 (",") 來存取可用格式規範的下拉式清單，其中每一項都包含其預期效果的描述。

   ![Visual Studio 2019 中的新 [監看式] 視窗和格式值功能](../ide/media/search-watch-window.png)

### <a name="visual-studio-live-share"></a>Visual Studio Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) 這項開發人員服務可讓您與組員共用程式碼庫和其中的內容，並直接從 Visual Stuido 中進行即時雙向共同作業。 組員可透過 Live Share 來閱讀、瀏覽、編輯和偵錯您與其共用的專案，過程相當自然且安全。

這項服務預設會安裝於 Visual Studio 2019 Preview。

## <a name="modern-development-support"></a>新式開發支援

### <a name="manage-pull-requests-prs-from-the-ide"></a>管理來自 IDE 的提取要求 (PR)

此次推出新的延伸模組，您可以下載來與 Visual Studio 2019 Preview 搭配使用。 使用這個新的延伸模組，您可以檢閱、執行偵錯要求，或是從您的團隊提取這些要求，而無需離開 Visual Studio IDE [(整合式開發環境)](../ide/visual-studio-ide.md)。 我們目前支援 Azure Repos 中的程式碼，但正在將支援擴大至 GitHub 並改善整體體驗。

若要立即開始，您可以從 Visual Studio Marketplace 下載[適用於 Visual Studio 的提取要求](https://aka.ms/pr4vs)延伸模組。

### <a name="develop-with-net-core-3-preview-1"></a>使用 .NET Core 3 Preview 1 進行開發

Visual Studio 2019 的預覽版本支援為任何平台建置 [.NET Core 3](http://aka.ms/netcore3preview1) 應用程式。 我們將持續支援並改善跨平台 C++ 程式開發，以及適用於 iOS 的 .NET 行動裝置開發、使用 Xamarin 的 Android 開發。

   ![使用 Visual Studio 2019 中的 .NET Core 3 Preview 1 開發應用程式](../ide/media/dot-net-core-three-dev.png)

## <a name="continuous-innovation"></a>持續創新

### <a name="per-monitor-aware-pma-rendering"></a>個別監視器感知 (PMA) 轉譯

如果您以不同顯示比例因素設定監視器，或從遠端連線到具有不同於您主要裝置顯示比例因素的機器，您可能會發現 Visual Studio 的顯示模糊，或以錯誤的比例轉譯。

對 Visual Studio 而言，Visual Studio 2019 Preview 1 版本使其往個別監視器感知 (PMA) 應用程式的方向邁進。 我們正在進行能讓 Visual Studio 正確轉譯的基礎工作，不論您使用的顯示比例因素為何。

   ![Visual Studio 2019 中的個別監視器感知 (PMA) 轉譯](../ide/media/per-monitor-aware-dpi-scaling.png)

### <a name="visual-studio-intellicode"></a>Visual Studio IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) 是使用人工智慧 (AI) 以改善軟體開發工作的延伸模組。 IntelliCode 在 GitHub 上的 2,000 個開放原始碼專案中訓練 (每個專案各有超過 100 顆星) 以產生建議。

以下是 Visual Studio IntelliCode 可協助提高生產力的幾種方式：

* 提供內容感知的程式碼完成
* 引導開發人員遵守所屬團隊的模式與風格
* 找出難以捕捉的程式碼問題
* 將注意力放在真正重要的區域，專注在程式碼檢閱上

當我們最初預覽適用於 Visual Studio 的 IntelliCode 延伸模組時，最早僅支援 C#。 現在，我們也在 Visual Studio 中新增了對 C++ 和 XAML 的支援。

如果您使用 C#，我們也新增了以您的程式碼訓練自訂模型的能力。

如需延伸模組及下載的詳細資訊，請參閱 Microsoft DevLabs 上的 [Visual Studio IntelliCode - 預覽](https://go.microsoft.com/fwlink/?linkid=872707)頁面。

## <a name="give-us-feedback"></a>提供意見反應

為什麼要傳送意見反應給 Visual Studio 小組？ 我們極為重視客戶的意見反應。 它們是我們進步的動力。

* 如果您想要提出改善 Visual Studio 的建議，可以使用[提供建議](../ide/talk-to-us.md#i-want-to-make-a-suggestion-about-visual-studio-features)工具。

* 如果您遇到停止回應、當機或其他效能問題，則可以使用[回報問題](../ide/talk-to-us.md#i-want-to-report-a-problem-with-visual-studio)工具，輕鬆地與我們分享重現步驟和支援檔案。

## <a name="see-also"></a>另請參閱

* [Visual Studio 2019 版本資訊](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)
* [Visual Studio 2017 的新功能](whats-new-in-visual-studio.md)
