---
title: "尋找和使用 Visual Studio 延伸模組 | Microsoft Docs"
ms.custom: 
ms.date: 06/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6ed49a18c7497eefc21a7fe7bfe9d35003863a5e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="find-and-use-visual-studio-extensions"></a>尋找和使用 Visual Studio 延伸模組

Visual Studio 擴充功能是在 Visual Studio 內執行的程式碼封裝，並提供全新或改良的 Visual Studio 功能。 您可以在這裡找到有關 Visual Studio 擴充功能的詳細資訊： [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。

您可以使用 [ **擴充功能和更新** ] 對話方塊來安裝 Visual Studio 擴充功能和來自網站及其他位置的範例，然後啟用、停用、更新或將它們解除安裝。 ([工具/擴充功能和更新]，或在 [快速啟動]  視窗中輸入 **擴充功能** )。 對話方塊也會顯示已安裝的範例和擴充功能的更新。 您也可以從網站下載擴充功能，或從其他開發人員取得。

> [!NOTE]
> 從 Visual Studio 2015 開始，在 Visual Studio Marketplace 託管的延伸模組將自動更新。  您可以透過 [擴充功能和更新]  對話方塊變更此設定。  如需詳細資訊，請參閱下方〈自動更新擴充功能〉  的章節。

## <a name="finding-visual-studio-extensions"></a>尋找 Visual Studio 擴充功能

您可以從 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) 安裝延伸模組。 這些擴充功能可能是增強 Visual Studio 功能的控制項、範例、範本、工具或其他元件。 Visual Studio 支援 VSIX 套件格式的擴充功能，包括專案範本、項目範本、 **工具箱** 項目、Managed Extension Framework (MEF) 元件和 VSPackage。 您也可以下載和安裝 MSI 架構的擴充功能，不過 [擴充功能和更新]  對話方塊無法啟用或停用它們。 Visual Studio Marketplace 包含 VSIX 和 MSI 延伸模組。

## <a name="installing-or-uninstalling-visual-studio-extensions"></a>安裝或解除安裝 Visual Studio 擴充功能

在 [擴充功能和更新] 尋找您想要安裝的擴充功能。 (如果您知道延伸模組的名稱或部分名稱，則可以在 [搜尋] 視窗中搜尋)。按一下 [下載]。  延伸模組將會排程安裝。 您的延伸模組將會在所有 Visual Studio 執行個體都關閉之後進行安裝。

如果您嘗試安裝具有相依性的擴充功能，安裝程式會確認是否已經安裝相依性。 如果尚未安裝，[ **擴充功能和更新** ] 對話方塊會列出在安裝擴充功能之前必須安裝的相依性。

如果您要停止使用擴充功能，則可以停用或將它解除安裝。 停用擴充功能會保持它的安裝狀態，但是不載入。 您只能停用 VSIX 擴充功能；而使用 MSI 安裝的擴充功能則只能解除安裝。 尋找擴充功能，然後按一下 [解除安裝]  或 [停用] 。 您必須重新啟動 Visual Studio，以卸載停用的擴充功能。

## <a name="per-user-and-administrative-extensions"></a>個別使用者和管理擴充功能

大部分的延伸模組都是個別使用者延伸模組，並安裝於 **%LocalAppData%\Microsoft\VisualStudio\\<Visual Studio 版本\>\Extensions\\** 資料夾中。 一些延伸模組則是管理延伸模組，安裝於 **\<Visual Studio 安裝資料夾>\Common7\IDE\Extensions\\** 資料夾中。

若要保護您的系統以避免可能包含錯誤或惡意程式碼的擴充功能，您可以限制只在使用一般使用者權限執行 Visual Studio 時才能載入個別使用者擴充功能。 這表示當使用系統管理使用者權限執行 Visual Studio 時，個別使用者擴充功能會被停用。 若要這樣做，請移至 [擴充功能和更新]  選項頁面 ([工具/選項]、[環境] 、[擴充功能和更新] 或在 [快速啟動]  視窗中輸入 **擴充功能** )。 清除 [以系統管理員身分執行時載入個別使用者擴充功能]  核取方塊，然後重新啟動 Visual Studio。

## <a name="automatic-extension-updates"></a>自動擴充功能更新

Visual Studio Marketplace 有新版本可用時，就會自動更新個別使用者延伸模組。  會在背景中偵測並安裝擴充功能的新版本，而在下次重新啟動 Visual Studio 時，將會執行擴充功能的新版本。

只有個別使用者擴充功能可以自動更新。  將不會更新針對所有使用者安裝的系統管理延伸模組，但您還是可以透過 [延伸模組和更新] 對話方塊的 [更新] 節點手動安裝新版本。 您可以在 [延伸模組和更新] 對話方塊之延伸模組的詳細資料窗格中，查看將自動更新的延伸模組。

如果您想要停用自動更新，您可以停用所有擴充功能或僅停用特定擴充功能。

- 若要停用所有延伸模組的自動更新，請選擇 [延伸模組和更新] 對話方塊中的 [變更您的 [延伸模組和更新] 設定] 連結，然後取消核取 [自動更新延伸模組]。

- 若要停用特定延伸模組的自動更新，請取消核取 [自動更新此延伸模組] 選項，該選項位於 [延伸模組和更新] 對話方塊右側之延伸模組的詳細資料窗格中。

> [!NOTE]
> 從 Visual Studio 2015 Update 2 開始，您可以指定 (在 [工具] / [選項] / [環境] / [延伸模組和更新] 中) 是否要自動更新每個使用者延伸模組、所有使用者延伸模組，或兩者皆自動更新 (預設值)。

## <a name="extension-crash-notifications"></a>延伸模組當機通知

在 Visual Studio 2017 (15.3 版 - Preview) 中，如果 Visual Studio 懷疑延伸模組與前一個工作階段期間的當機有關，則會通知您。 Visual Studio 當機時，會儲存例外狀況堆疊。 下次 Visual Studio 啟動時會檢查堆疊，而且是從分葉節點和工作節點開始往基礎節點方向開始檢查。 如果 Visual Studio 判斷框架屬於已安裝並啟用之延伸模組的模組，則會使用下列這類訊息通知您：

「上一個工作階段意外終止。 停用延伸模組 'extension_name' 可有助於避免發生類似問題。」

您可以略過此通知，或採取下列其中一個動作：

- 選擇 [停用此延伸模組]。 Visual Studio 會停用延伸模組，並可讓您知道是否需要重新啟動系統，以讓停用生效。 想要的話，您可以在 [延伸模組和更新] 對話方塊中重新啟用延伸模組。

- 選擇 [不要再針對此延伸模組顯示]。 IDE 將不再顯示這個延伸模組相關當機的通知，但會顯示其他延伸模組相關當機的通知。

- 選擇 [深入了解]，以在預設瀏覽器中檢視此說明主題。

- 選擇通知結尾的 [X] 按鈕，以關閉通知。 如果同一個延伸模組與未來工作階段中的當機有關，則會再次出現此通知。

> [!NOTE]
> 當機通知只表示其中一個延伸模組的模組位在當機的堆疊上。 不一定表示延伸模組本身造成當機。 延伸模組可能呼叫為 Visual Studio 一部分的程式碼，而且該程式碼造成當機。 不過，如果導致當機的案例對您而言不重要，則此通知可能仍然十分有用。 在此情況下，停用延伸模組可避免未來發生相同的當機，而且不會影響產能。

## <a name="sample-master-copies-and-working-copies"></a>範例主複本與工作複本

當您安裝線上範例時，方案會儲存在兩個位置中：

- 工作複本會儲存在您於 [ **新增專案** ] 對話方塊中所指定的位置。

- 個別的主複本則會儲存在您的電腦中。

您可以使用 [ **擴充功能和更新** ] 對話方塊來執行這些範例相關工作：

- 列出您安裝的範例的主複本。

- 停用或解除安裝範例的主複本。

- 安裝範例套件 (是與某個技術或功能相關的範例集合)。

- 安裝個別的線上範例 (您也可以在 [ **新增專案** ] 對話方塊中執行這項作業)。

- 當安裝的範例原始程式碼變更發行時，檢視更新通知。

- 當有更新通知時，更新已安裝範例的主複本。

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>不使用擴充功能和更新對話方塊安裝擴充功能

在 Visual Studio Marketplace 以外的位置中，可能也會提供已封裝在 .vsix 檔案中的延伸模組。 雖然 [擴充功能和更新]  對話方塊無法偵測這些檔案，但您可以按兩下該檔案來安裝 .vsix 檔，或選取檔案並按下 Enter 鍵。 接下來只需遵循指示進行。 當擴充功能安裝完成時，您可以使用 [ **擴充功能和更新** ] 對話方塊來啟用、停用或將它解除安裝。

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>擴充功能和更新對話方塊不支援擴充功能類型

Visual Studio 會繼續支援 Microsoft Installer (MSI) 所安裝的擴充功能，但無法不經修改即使用 [擴充功能和更新]  對話方塊。

> [!TIP]
> 若以 MSI 為基礎的擴充功能包含 extension.vsixmanifest 檔案，則此擴充功能會出現在 [擴充功能和更新]  對話方塊中。
