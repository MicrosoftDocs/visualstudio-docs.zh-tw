---
title: 尋找及使用延伸模組
ms.date: 01/30/2019
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e282cdfda27579fd83871153a19897652d55865
ms.sourcegitcommit: d4bea2867a4f0c3b044fd334a54407c0fe87f9e8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58790754"
---
# <a name="find-and-use-visual-studio-extensions"></a>尋找和使用 Visual Studio 延伸模組

Visual Studio 擴充功能是在 Visual Studio 內執行的程式碼封裝，並提供全新或改良的 Visual Studio 功能。 您可以在這裡找到有關 Visual Studio 延伸模組的詳細資訊：[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。

::: moniker range="vs-2017"

使用 [延伸模組和更新] 對話方塊，即可安裝和管理 Visual Studio 延伸模組。 若要開啟 [擴充功能和更新] 對話方塊，請選擇 [工具]  > [擴充功能和更新]，或是在 [快速啟動] 搜尋方塊中輸入**擴充功能**。

::: moniker-end

::: moniker range=">=vs-2019"

使用 [管理擴充功能] 對話方塊來安裝和管理 Visual Studio 擴充功能。 若要開啟 [管理擴充功能] 對話方塊，請選擇 [擴充功能] > [管理擴充功能]。 或者，在搜尋方塊中輸入**延伸模組**，然後選擇 [管理延伸模組]。

::: moniker-end

![Visual Studio 中的 [擴充功能] 視窗](media/finding-using-visual-studio-extensions/extensions-and-updates.png)

左側窗格會依據已安裝、可在 Visual Studio Marketplace (**Online**) 取得以及有更新可用的延伸模組進行分類。 **漫遊擴充管理員**會保留您已在任何電腦或 Visual Studio 執行個體上安裝的所有 Visual Studio 延伸模組清單。 它設計成可讓您更輕鬆地找到您最愛的延伸模組。

## <a name="find-visual-studio-extensions"></a>尋找 Visual Studio 延伸模組

您可以從 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) 安裝延伸模組。 這些擴充功能可能是增強 Visual Studio 功能的控制項、範例、範本、工具或其他元件。 Visual Studio 支援 VSIX 套件格式的擴充功能，包括專案範本、項目範本、 **工具箱** 項目、Managed Extension Framework (MEF) 元件和 VSPackage。

::: moniker range="vs-2017"

您也可以下載和安裝 MSI 架構的擴充功能，不過 [擴充功能和更新]  對話方塊無法啟用或停用它們。 Visual Studio Marketplace 包含 VSIX 和 MSI 擴充功能。

::: moniker-end

::: moniker range=">=vs-2019"

您也可以下載並安裝 MSI 架構的擴充功能，但是，[管理擴充功能] 對話方塊無法啟用或停用它們。 Visual Studio Marketplace 包含 VSIX 和 MSI 擴充功能。

::: moniker-end

## <a name="install-or-uninstall-visual-studio-extensions"></a>安裝或解除安裝 Visual Studio 延伸模組

::: moniker range="vs-2017"

在 [擴充功能和更新] 中，尋找您想要安裝的擴充功能。 (如果您知道延伸模組的名稱或部分名稱，則可以在 [搜尋] 視窗中搜尋)。按一下 [下載]。 延伸模組將會排程安裝。 您的延伸模組將會在所有 Visual Studio 執行個體都關閉之後進行安裝。

如果您嘗試安裝具有相依性的擴充功能，安裝程式會確認是否已經安裝相依性。 如果尚未安裝，[ **擴充功能和更新** ] 對話方塊會列出在安裝擴充功能之前必須安裝的相依性。

::: moniker-end

::: moniker range=">=vs-2019"

在 [管理擴充功能] 中，尋找您想要安裝的擴充功能。 (如果您知道延伸模組的名稱或部分名稱，則可以在 [搜尋] 視窗中搜尋)。按一下 [下載]。 延伸模組將會排程安裝。 您的延伸模組將會在所有 Visual Studio 執行個體都關閉之後進行安裝。

如果您嘗試安裝具有相依性的擴充功能，安裝程式會確認是否已經安裝相依性。 如果尚未安裝，[管理擴充功能] 對話方塊就會列出必須在安裝擴充功能之前安裝的相依性。

::: moniker-end

如果您要停止使用擴充功能，則可以停用或將它解除安裝。 停用擴充功能會保持它的安裝狀態，但是不載入。 您只能停用 VSIX 擴充功能；而使用 MSI 安裝的擴充功能則只能解除安裝。 尋找擴充功能，然後按一下 [解除安裝]  或 [停用] 。 重新啟動 Visual Studio 以卸載某個已停用的延伸模組。

## <a name="per-user-and-administrative-extensions"></a>個別使用者和管理延伸模組

大部分的延伸模組都是個別使用者延伸模組，並安裝於 *%LocalAppData%\Microsoft\VisualStudio\\<Visual Studio 版本\>\Extensions\\* 資料夾中。 一些延伸模組則是管理延伸模組，安裝於 *\<Visual Studio 安裝資料夾>\Common7\IDE\Extensions\\* 資料夾中。

若要保護您的系統以避免可能包含錯誤或惡意程式碼的擴充功能，您可以限制只在使用一般使用者權限執行 Visual Studio 時才能載入個別使用者擴充功能。 這表示當使用系統管理使用者權限執行 Visual Studio 時，個別使用者擴充功能會被停用。 若要這樣做，請移至擴充功能選項頁面 ([工具] > [選項] > [環境] > [擴充功能])。 清除 [以系統管理員身分執行時載入個別使用者擴充功能]  核取方塊，然後重新啟動 Visual Studio。

## <a name="automatic-extension-updates"></a>自動延伸模組更新

Visual Studio Marketplace 有新版本可用時，就會自動更新延伸模組。 偵測到新版本的延伸模組，並且會在背景安裝。 當您下一次開啟 Visual Studio 時，將執行新版的擴充功能。

如果您想要停用自動更新，您可以停用所有擴充功能或僅停用特定擴充功能。

::: moniker range="vs-2017"

- 若要停用所有延伸模組的自動更新，請選擇 [延伸模組更新] 對話方塊中的 [變更您的 [延伸模組和更新] 設定] 連結。 在 [選項] 對話方塊中，取消核取 [自動更新延伸模組]。

- 若要停用特定延伸模組的自動更新，請取消核取 [自動更新此延伸模組] 選項，該選項位於 [延伸模組和更新] 對話方塊右側之延伸模組的詳細資料窗格中。

::: moniker-end

::: moniker range=">=vs-2019"

- 若要停用所有擴充功能的自動更新，請選擇 [管理擴充功能] 對話方塊中的 [變更您的延伸模組設定] 連結。 在 [選項] 對話方塊中，取消核取 [自動更新延伸模組]。

- 若要停用特定擴充功能的自動更新，請取消核取 [自動更新此擴充功能] 選項，該選項位於 [管理擴充功能] 對話方塊右側的擴充功能詳細資料窗格中。

::: moniker-end

## <a name="extension-crash-and-unresponsiveness-notifications"></a>延伸模組當機和無回應通知

如果 Visual Studio 懷疑某個延伸模組與之前工作階段期間的當機有關，則會通知您。 Visual Studio 當機時，會儲存例外狀況堆疊。 下次 Visual Studio 啟動時會檢查堆疊，而且是從分葉節點和工作節點開始往基礎節點方向開始檢查。 如果 Visual Studio 判斷框架屬於已安裝並啟用之延伸模組的模組，則會顯示通知。

如果 Visual Studio 懷疑某個延伸模組導致 UI 無回應，也會通知您。

當顯示這些通知時，您可以略過此通知，或採取下列其中一個動作：

::: moniker range="vs-2017"

- 選擇 [停用此延伸模組]。 Visual Studio 會停用延伸模組，並可讓您知道是否需要重新啟動系統，以讓停用生效。 想要的話，您可以在 [延伸模組和更新] 對話方塊中重新啟用延伸模組。

::: moniker-end

::: moniker range=">=vs-2019"

- 選擇 [停用此延伸模組]。 Visual Studio 會停用延伸模組，並可讓您知道是否需要重新啟動系統，以讓停用生效。 您可以視需要在 [管理擴充功能] 對話方塊中重新啟用擴充功能。

::: moniker-end

- 選擇 [一律不再顯示此訊息]。

  - 如果是有關前一個工作階段中當機的通知，當發生與此延伸模組相關的當機時，Visual Studio 將不再顯示通知。 當無回應可能與此延伸模組相關聯，或者當機或無回應可能與其他延伸模組相關聯時，Visual Studio 仍將顯示通知。
  - 如果通知與無回應有關，則當此延伸模組於無回應相關聯時，IDE 將不再顯示通知。 Visual Studio 仍將顯示此延伸模組的當機相關通知，以及其他延伸模組的當機與無回應相關通知。

- 選擇 [深入了解] 返回此頁面。

- 選擇通知結尾的 [X] 按鈕，以關閉通知。 未來與當機或 UI 無回應相關聯之延伸模組的執行個體，將會顯示新的通知。

> [!NOTE]
> UI 無回應或當機通知表示當 UI 無回應或者發生當機時，延伸模組的其中一個模組是在堆疊上。 這不一定表示延伸模組本身為問題。 有可能是延伸模組呼叫屬於 Visual Studio 一部分的程式碼，而該程式碼會反過來造成無回應 UI 或當機。 不過，如果導致 UI 無回應或當機的延伸模組對您而言不重要，則此通知可能仍然十分有用。 在此情況下，停用延伸模組可避免未來發生 UI 無回應或損毀，而且不會影響產能。

## <a name="sample-master-copies-and-working-copies"></a>範例主複本與工作複本

當您安裝線上範例時，方案會儲存在兩個位置中：

- 工作複本會儲存在您建立專案時指定的位置。

- 個別的主複本則會儲存在您的電腦中。

::: moniker range="vs-2017"

您可以使用 [擴充功能和更新] 視窗來執行這些範例相關工作：

::: moniker-end

::: moniker range=">=vs-2019"

您可以使用 [管理擴充功能] 視窗來執行這些範例相關工作：

::: moniker-end

- 列出您安裝的範例的主複本。

- 停用或解除安裝範例的主複本。

- 安裝範例套件 (是與某個技術或功能相關的範例集合)。

- 安裝個別的線上範例

- 當安裝的範例原始程式碼變更發行時，檢視更新通知。

- 當有更新通知時，更新已安裝範例的主複本。

::: moniker range="vs-2017"

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>不使用延伸模組和更新對話方塊安裝延伸模組

在 Visual Studio Marketplace 以外的位置中，可能也會提供已封裝在 .vsix 檔案中的延伸模組。 雖然 [延伸模組和更新] 對話方塊偵測不到這些檔案，但您可以按兩下該檔案來安裝 .vsix 檔案，或選取檔案並按 **Enter** 鍵。 接下來只需遵循指示進行。 當擴充功能安裝完成時，您可以使用 [ **擴充功能和更新** ] 對話方塊來啟用、停用或將它解除安裝。

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>延伸模組和更新對話方塊不支援的延伸模組類型

Visual Studio 會繼續支援 Microsoft Installer (MSI) 所安裝的擴充功能，但無法不經修改即使用 [擴充功能和更新]  對話方塊。

> [!TIP]
> 如果以 MSI 為基礎的延伸模組包含 extension.vsixmanifest 檔案，則此延伸模組會出現在 [延伸模組和更新] 對話方塊中。

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="installing-without-using-the-manage-extensions-dialog-box"></a>不使用 [管理擴充功能] 對話方塊進行安裝

在 Visual Studio Marketplace 以外的位置中，可能也會提供已封裝在 .vsix 檔案中的延伸模組。 雖然 [管理擴充功能] 對話方塊偵測不到這些檔案，但您可以按兩下該檔案，或選取該檔案並按 **Enter** 鍵，來安裝 *.vsix* 檔案。 接下來只需遵循指示進行。 安裝擴充功能之後，您就能使用 [管理擴充功能] 對話方塊來將它啟用、停用或解除安裝。

## <a name="extension-types-not-supported-by-the-manage-extensions-dialog-box"></a>[管理擴充功能] 對話方塊不支援的擴充功能類型

Visual Studio 會繼續支援 Microsoft Installer (MSI) 所安裝的擴充功能，但不支援在不經修改的情況下透過 [管理擴充功能]  對話方塊所安裝的擴充功能。

> [!TIP]
> 如果 MSI 架構的擴充功能包含 *extension.vsixmanifest* 檔案，則此擴充功能會出現在 [管理擴充功能] 對話方塊中。

::: moniker-end