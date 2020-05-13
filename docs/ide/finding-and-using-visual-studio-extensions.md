---
title: 查找並安裝擴展
ms.date: 09/18/2019
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f016af58b5799ca37b1a8f0cc54366d639c57c03
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594405"
---
# <a name="manage-extensions-for-visual-studio"></a>管理視覺化工作室的擴展

擴展是在 Visual Studio 中運行並提供新的或改進的功能的代碼包。 擴展可以是控制項、示例、範本、工具或其他元件，這些元件向 Visual Studio 添加功能，例如，[即時共用](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsls-vs)或[視覺化工作室 IntelliCode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.VSIntelliCode)。

有關創建視覺化工作室擴展的資訊，請參閱[視覺化工作室 SDK](../extensibility/visual-studio-sdk.md)。 有關使用擴展的資訊，請參閱[Visual Studio 應用商店](https://marketplace.visualstudio.com)上的單個擴展頁。

::: moniker range="vs-2017"

## <a name="extensions-and-updates-dialog-box"></a>[擴充功能和更新] 對話方塊

使用 [延伸模組和更新]**** 對話方塊，即可安裝和管理 Visual Studio 延伸模組。 若要開啟 [擴充功能和更新]**** 對話方塊，請選擇 [工具]**** > [擴充功能和更新]****，或是在 [快速啟動]**** 搜尋方塊中輸入**擴充功能**。

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="manage-extensions-dialog-box"></a>管理擴展對話方塊

使用 [管理擴充功能]**** 對話方塊來安裝和管理 Visual Studio 擴充功能。 若要開啟 [管理擴充功能]**** 對話方塊，請選擇 [擴充功能]**** > [管理擴充功能]****。 或者，在搜尋方塊中輸入**延伸模組**，然後選擇 [管理延伸模組]****。

::: moniker-end

![Visual Studio 中的 [擴充功能] 視窗](media/finding-using-visual-studio-extensions/extensions-and-updates.png)

左側窗格會依據已安裝、可在 Visual Studio Marketplace (**Online**) 取得以及有更新可用的延伸模組進行分類。 **漫遊擴充管理員**會保留您已在任何電腦或 Visual Studio 執行個體上安裝的所有 Visual Studio 延伸模組清單。 它設計成可讓您更輕鬆地找到您最愛的延伸模組。

## <a name="find-and-install-extensions"></a>查找並安裝擴展

::: moniker range="vs-2017"

您可以在[視覺化工作室中](https://marketplace.visualstudio.com)安裝 Visual Studio 應用商店或"擴展和更新"對話方塊中的擴展。

要在視覺化工作室內安裝擴展：

1. 從 **"工具** > **擴展"和"更新**"中，找到要安裝的擴展。 如果您知道副檔名的名稱或部分名稱，則可以在 **"搜索"視窗中進行搜索**。

2. 選擇**下載**。

   延伸模組將會排程安裝。 關閉所有 Visual Studio 實例後，將安裝您的擴展。

如果您嘗試安裝具有相依性的擴充功能，安裝程式會確認是否已經安裝相依性。 如果尚未安裝，[ **擴充功能和更新** ] 對話方塊會列出在安裝擴充功能之前必須安裝的相依性。

### <a name="install-without-using-the-extensions-and-updates-dialog-box"></a>不使用 [延伸模組和更新] 對話方塊進行安裝

在 Visual Studio Marketplace 以外的位置中，可能也會提供已封裝在 .vsix** 檔案中的延伸模組。 "**工具** > **副檔名和更新"** 對話方塊無法檢測這些檔，但您可以通過按兩下檔或選擇該檔並按**Enter**來安裝 *.vsix*檔。 接下來只需遵循指示進行。 當擴充功能安裝完成時，您可以使用 [ **擴充功能和更新** ] 對話方塊來啟用、停用或將它解除安裝。

> [!NOTE]
> - Visual Studio Marketplace 包含 VSIX 和 MSI 擴充功能。 "擴展"和"更新"對話方塊無法啟用或禁用基於 MSI 的擴展。
> - 如果以 MSI 為基礎的延伸模組包含 extension.vsixmanifest** 檔案，則此延伸模組會出現在 [延伸模組和更新]**** 對話方塊中。

::: moniker-end

::: moniker range=">=vs-2019"

您可以在[視覺化工作室中](https://marketplace.visualstudio.com)安裝 Visual Studio 應用商店或"管理擴展"對話方塊中的擴展。

要在視覺化工作室內安裝擴展：

1. 從**擴展** > **管理擴展**，找到要安裝的擴展。 (如果您知道延伸模組的名稱或部分名稱，則可以在 [搜尋]**** 視窗中搜尋)。

2. 選擇**下載**。

   延伸模組將會排程安裝。 關閉所有 Visual Studio 實例後，將安裝您的擴展。

如果您嘗試安裝具有相依性的擴充功能，安裝程式會確認是否已經安裝相依性。 如果尚未安裝，[管理擴充功能]**** 對話方塊就會列出必須在安裝擴充功能之前安裝的相依性。

### <a name="install-without-using-the-manage-extensions-dialog-box"></a>不使用 [管理延伸模組] 對話方塊進行安裝

在 Visual Studio Marketplace 以外的位置中，可能也會提供已封裝在 .vsix** 檔案中的延伸模組。 擴展**Extensions** > **管理副檔名**對話方塊無法檢測這些檔，但您可以通過按兩下檔或選擇檔並按**Enter**來安裝 *.vsix*檔。 接下來只需遵循指示進行。 安裝擴充功能之後，您就能使用 [管理擴充功能]**** 對話方塊來將它啟用、停用或解除安裝。

> [!NOTE]
> - Visual Studio Marketplace 包含 VSIX 和 MSI 擴充功能。 "管理擴展"對話方塊無法啟用或禁用基於 MSI 的擴展。
> - 如果 MSI 架構的擴充功能包含 *extension.vsixmanifest* 檔案，則此擴充功能會出現在 [管理擴充功能]**** 對話方塊中。

::: moniker-end

## <a name="uninstall-or-disable-an-extension"></a>卸載或禁用擴展

如果您要停止使用擴充功能，則可以停用或將它解除安裝。 停用擴充功能會保持它的安裝狀態，但是不載入。 尋找擴充功能，然後按一下 [解除安裝] **** 或 [停用] ****。 重新啟動 Visual Studio 以卸載某個已停用的延伸模組。

> [!NOTE]
> 您可以禁用 VSIX 擴展，但不能禁用使用 MSI 安裝的擴展。 只能卸載 MSI 安裝的擴展。

## <a name="per-user-and-administrative-extensions"></a>個別使用者和管理延伸模組

大多數擴展是每個使用者，並安裝在 *%LocalAppData%*Microsoft_VisualStudio\\<Visual Studio\>版本 [\\擴展]* 資料夾中。 一些擴展是管理擴展，並安裝在*\<Visual Studio 安裝資料夾中\\>_Common7_IDE_擴展資料夾*。

若要保護您的系統以避免可能包含錯誤或惡意程式碼的擴充功能，您可以限制只在使用一般使用者權限執行 Visual Studio 時才能載入個別使用者擴充功能。 這意味著，當使用較高的權限運行 Visual Studio 時，將禁用每個使用者擴展。

要限制每個使用者擴展載入時：

1. 打開擴展選項頁 （**工具** > **選項** > **環境** > **擴展**）。

2. **以管理員身份運行時清除每個使用者擴展的載入**情況。核取方塊。

3. 重新啟動 Visual Studio。

## <a name="automatic-extension-updates"></a>自動延伸模組更新

當 Visual Studio 應用商店中有新版本時，擴展會自動更新。 偵測到新版本的延伸模組，並且會在背景安裝。 當您下一次開啟 Visual Studio 時，將執行新版的擴充功能。

如果要禁用自動更新，可以禁用所有擴展的功能，也可以僅針對特定擴展禁用該功能。

::: moniker range="vs-2017"

- 若要停用所有延伸模組的自動更新，請選擇 [工具]**** > [延伸模組和更新]**** 對話方塊中的 [變更您的延伸模組和更新設定]**** 連結。 在 [選項]**** 對話方塊中，取消核取 [自動更新延伸模組]****。

- 若要停用特定延伸模組的自動更新，請取消核取 [自動更新此延伸模組]**** 選項，該選項位於 [延伸模組和更新]**** 對話方塊右側之延伸模組的詳細資料窗格中。

::: moniker-end

::: moniker range=">=vs-2019"

- 若要停用所有延伸模組的自動更新，請選擇 [延伸模組]**** > [管理延伸模組]**** 對話方塊中的 [變更您的延伸模組和更新設定]**** 連結。 在 [選項]**** 對話方塊中，取消核取 [自動更新延伸模組]****。

- 若要停用特定擴充功能的自動更新，請取消核取 [自動更新此擴充功能]**** 選項，該選項位於 [管理擴充功能]**** 對話方塊右側的擴充功能詳細資料窗格中。

::: moniker-end

## <a name="crash-and-unresponsiveness-notifications"></a>崩潰和無回應通知

如果 Visual Studio 懷疑某個延伸模組與之前工作階段期間的當機有關，則會通知您。 Visual Studio 當機時，會儲存例外狀況堆疊。 下次 Visual Studio 啟動時會檢查堆疊，而且是從分葉節點和工作節點開始往基礎節點方向開始檢查。 如果 Visual Studio 判斷框架屬於已安裝並啟用之延伸模組的模組，則會顯示通知。

如果 Visual Studio 懷疑某個延伸模組導致 UI 無回應，也會通知您。

當顯示這些通知時，您可以略過此通知，或採取下列其中一個動作：

::: moniker range="vs-2017"

- 選擇 [停用此延伸模組]****。 Visual Studio 會停用延伸模組，並可讓您知道是否需要重新啟動系統，以讓停用生效。 如果需要，可以在"**工具** > **擴展和更新**"對話方塊中重新啟用擴展。

::: moniker-end

::: moniker range=">=vs-2019"

- 選擇 [停用此延伸模組]****。 Visual Studio 會停用延伸模組，並可讓您知道是否需要重新啟動系統，以讓停用生效。 如果需要，可以在 **"擴展** > **管理擴展"** 對話方塊中重新啟用擴展。

::: moniker-end

- 選擇 [一律不再顯示此訊息]****。

  - 如果是有關前一個工作階段中當機的通知，當發生與此延伸模組相關的當機時，Visual Studio 將不再顯示通知。 當無回應可能與此延伸模組相關聯，或者當機或無回應可能與其他延伸模組相關聯時，Visual Studio 仍將顯示通知。
  - 如果通知涉及無回應性，則當此擴展與無回應關聯時，整合式開發環境 （IDE） 將不再顯示通知。 Visual Studio 仍將顯示此擴展的與崩潰相關的通知，以及其他擴展的崩潰和回應性通知。

- 選擇 **"瞭解更多**"以導航到此頁面。

- 選擇通知結尾的 [X]**** 按鈕，以關閉通知。 未來與當機或 UI 無回應相關聯之延伸模組的執行個體，將會顯示新的通知。

> [!NOTE]
> UI 無回應或當機通知表示當 UI 無回應或者發生當機時，延伸模組的其中一個模組是在堆疊上。 這不一定表示延伸模組本身為問題。 擴展可能稱為 Visual Studio 的一部分的代碼，這反過來又導致 UI 無回應或崩潰。 不過，如果導致 UI 無回應或當機的延伸模組對您而言不重要，則此通知可能仍然十分有用。 在此情況下，停用延伸模組可避免未來發生 UI 無回應或損毀，而且不會影響產能。

## <a name="samples"></a>範例

當您安裝線上範例時，方案會儲存在兩個位置中：

- 工作複本會儲存在您建立專案時指定的位置。

- 個別的主複本則會儲存在您的電腦中。

::: moniker range="vs-2017"

您可以使用 [工具]** [延伸模組和更新]** > **** 對話方塊來執行這些範例相關工作：

::: moniker-end

::: moniker range=">=vs-2019"

您可以使用 [延伸模組]** [管理延伸模組]** > **** 對話方塊來執行這些範例相關工作：

::: moniker-end

- 列出您安裝的範例的主複本。

- 停用或解除安裝範例的主複本。

- 安裝範例套件 (是與某個技術或功能相關的範例集合)。

- 安裝個別的線上範例

- 當安裝的範例原始程式碼變更發行時，檢視更新通知。

- 當有更新通知時，更新已安裝範例的主複本。

## <a name="see-also"></a>另請參閱

- [Visual Studio Marketplace](https://marketplace.visualstudio.com)
- [視覺化工作室 SDK](../extensibility/visual-studio-sdk.md)
