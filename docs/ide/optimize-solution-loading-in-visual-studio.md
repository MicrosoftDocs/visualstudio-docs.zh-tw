---
title: "Visual Studio 中的最佳化方案載入 | Microsoft Docs"
ms.custom: 
ms.date: 08/31/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: 84989983-84bc-4f81-97a8-2131e3a25138
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.performancecenter
ms.technology: vs-ide-general
ms.openlocfilehash: 2102fc026b566c89108f0d74dcf604020653e358
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="optimize-solution-loading-in-visual-studio"></a>Visual Studio 中的最佳化方案載入
許多解決方案包含大量的專案，這會影響載入這些解決方案所花費的時間。 不過，在小組環境中，開發人員通常是處理這些專案的不同子集，不需要載入所有個別專案。

Visual Studio 2017 支援**輕量型解決方案載入**。 當啟用輕量型解決方案載入 (LSL) 模式時，Visual Studio 2017 會載入專案的小子集，而不是載入大型解決方案的所有專案。 大部分的常用 IDE 功能都是在 LSL 模式下運作，它能讓您建置、搜尋及偵錯整個解決方案。 (LSL 模式中不支援的主要功能是編輯後繼續)。

> [!NOTE]
> 此內容適用於 Visual Studio 2017 Update 3

凡是專案數逾 30 的大型解決方案，LSL 載入的速度通常是 (平均值) 兩倍快。 雖然 LSL 模式可以使用大部分的 IDE 功能，但某些 IDE 功能可能需要載入所有專案。 在這些情況下，Visual Studio 會自動載入整個解決方案，方便您使用此功能。 最差的狀況是在輕量級模式中結束載入所有專案。 

如果您對目前未載入的專案使用 IDE 功能，Visual Studio 會為您載入適當的專案。 例如，如果您嘗試為未開啟的專案建立或開啟類別圖表，Visual Studio 會自動載入適當的專案。 以下各節有詳細的功能清單可供參考。

下列各節會示範如何啟用輕量型解決方案載入以及協助您決定是否啟用此功能。

## <a name="enable-or-disable-lightweight-solution-load"></a>啟用或停用輕量型解決方案載入

以滑鼠右鍵按一下方案總管中的方案名稱，並選取 [啟用輕量型解決方案載入]。 選取選項之後，必須關閉並重新開啟方案，才能啟動輕量型解決方案載入。

> [!NOTE]
> 類似步驟適用於停用 LSL。 若要停用輕量型解決方案載入，請選取 [停用輕量型解決方案載入]，然後關閉再重新開啟解決方案。 

![底下提供說明，包括方案總管](../ide/media/VSIDE_LSL_Solution_Setting.png)

## <a name="global_solution_load_settings"></a>設定輕量型方案載入的全域設定

您可以選擇 [工具] > [選項] > [專案和方案]，全域停用或設定所有解決方案的 LSL。

![工具選項對話方塊](../ide/media/VSIDE_LightweightSolutionLoad.png)

## <a name="how-does-lightweight-solution-load-work-behind-the-scenes"></a>輕量型解決方案載入如何在幕後運作？

當您載入解決方案時，Visual Studio 會記住您之前開啟過哪些專案，只載入這些專案。 所有其他專案會顯示在方案總管中，但不載入。 只要展開的專案或以滑鼠右鍵按一下專案，Visual Studio 就會自動載入該專案。 自動載入專案通常不到一秒，但某些專案可能需時較長。
不過，Visual Studio 可在整個解決方案中使用搜尋、偵錯、建置和原始檔控制等 IDE 功能。 例如，即使輕量級模式中只載入幾個專案，您仍可以搜尋整個解決方案。 

當您展開更多專案時，Visual Studio 會記住已展開專案的清單。 重新開啟解決方案時，Visual Studio 會自動載入之前展開過的專案。

## <a name="visual-studio-prompts-developers-likely-to-see-significant-performance-gains"></a>Visual Studio 會提示開發人員可能看到效能提升顯著的解決方案

從 Visual Studio 遙測中，專案數逾 30 的大型解決方案顯著受益於 LSL 模式。 因此，我們會提示開發人員利用大型解決方案嘗試 LSL 模式。 大部分初次嘗試 LSL 的開發人員，最後都會定期使用它。 

我們經常檢閱 Visual Studio 使用狀況遙測，改善啟發學習法，向可能獲益最多的開發人員提供 LSL 模式。 

## <a name="visual-studio-makes-recommendations-to-turn-on-lightweight-solution-load-based-on-heuristics"></a>Visual Studio 會建議根據啟發學習法開啟輕量型解決方案載入

根據預設，Visual Studio 會為最有可能受益的使用者開啟 LSL。 如果您有多個解決方案，Visual Studio 會提供最可能看到效能提升顯著的解決方案 LSL 模式。 如果您選取輕量級模式選項 [Let Visual Studio decide] (讓 Visual Studio 決定) (預設選項)，Visual Studio 會根據啟發學習法在輕量級模式中開啟解決方案。 訊息列，指出解決方案是否為輕量級模式。 當訊息列出現時，您可以選擇深入了解，或更新設定。

![快顯視窗](../ide/media/VSIDE_LSL_Popup.png)

## <a name="ide-features-fully-supported-in-lightweight-mode"></a>IDE 功能，在輕量級模式中受到完全支援

|功能|輕量級模式是否支援？|
|-|-|-|
|IntelliSense|是|
|搜尋|是|
|偵錯|是|
|組建|是|
|程式碼瀏覽 (前往定義以及尋找所有參考)|是|
|Code Lens|是|
|靜態程式碼分析|是|
|部署並發佈|是|
|新增及移除參考|是|
|多目標|是|
|IntelliTrace|是|
|Live Unit Testing|是|
|IntelliTest|是|
|Microsoft Fakes|是|
|編輯後繼續|不支援|
|單元測試|需要載入後面接著解決方案組建的測試專案|

## <a name="scenarios-in-which-lightweight-solution-loads-the-appropriate-projects-to-complete-the-operation"></a>輕量型解決方案載入適當專案以完成操作的案例

如果您處理的不是解決方案中的專案，就不會在輕量級模式中載入專案。 針對某些功能，會自動載入其他專案以支援功能案例。 (我們想要減少這些案例。) 針對這些案例，Visual Studio 會載入專案本身，或提示您視需要載入專案。

|分類|問題|
|-|-|-|
|單元測試|目前未載入的專案不會顯示在 [建立 IntelliTest 精靈] 和 [建立單元測試精靈] 的測試專案清單中。 </br>您需要載入建立測試的專案 (您可以展開專案節點載入專案)。|
|類別圖表|如果建立或開啟專案的類別圖表，Visual Studio 會自動載入與該專案直接相依的專案。 </br>如果未載入整個解決方案，我們會關閉相依性驗證圖表參考的過時成品驗證。|

## <a name="scenarios-in-which-lightweight-solution-loads-the-entire-solution"></a>輕量型解決方案載入整個解決方案的案例 

針對某些功能，Visual Studio 會自動載入整個解決方案，以支援案例。 此動作可確保您一律取得完整的功能。 例如，某些 TFS 作業可能需要載入整個方案。 為提供完整功能，Visual Studio 會載入整個解決方案。

|分類|情節|
|-|-|-|
|解決方案節點上的 TFS SCC 命令|如果在 (方案總管的) 解決方案節點上觸發 SCC 命令，Visual Studio 會先自動載入整個解決方案，再完成命令。|
|專案載入|如果解決方案包含 .NET Core 專案及共用專案，Visual Studio 一律會在初始解決方案自行載入期間，自動載入這些專案。 這些專案目前不支援輕量型模式。|
|解決方案組態管理員|如果使用解決方案組態管理員或批次組建，Visual Studio 會自動載入整個解決方案，以提供完整的體驗。|
|NuGet 套件管理員|如果開啟 NuGet 套件管理員的使用者介面或 NuGet 套件管理員主控台，Visual Studio 會自動載入整個解決方案，以提供完整的體驗。|

## <a name="known-issues"></a>已知問題

有些情況無法使用 LSL 模式，需要載入其他專案或整個解決方案。 我們正積極努力解決這些情況。 

|分類|問題|因應措施|
|-|-|-|-|
|IntelliSense|組態變更 (例如將版本組建變更為偵錯或反過來) 之後，IntelliSense 可能不會更新。 該影響取決於組態變更所造成的程式碼差異。|變更組態之後，請重新載入解決方案。|
|重構 C#/VB 專案的限制|變更專案檔的程式碼修正第一次可能會無聲無息地失敗。|如果需要對這些專案檔進行程式碼修正，請載入專案。 輕量級模式不會修正未載入的專案。|
|單元測試探索|手動載入專案時，不執行延後專案上探索到的測試。|重建專案以重新探索測試，並再次執行選取的測試。|
|Live Unit Testing (LUT)|在 LSL 模式中，您會看到 LUT 未啟用。 因為 LUT 需要載入其中一項測試專案，所以不啟動它。|載入任何測試專案，以啟用解決方案的 Live Unit Testing。|
|方案總管搜尋|1.  LSL 模式中的方案總管搜尋不會在檔案內搜尋，所以沒有進度結果 (亦即搜尋樹狀結構下只會顯示檔案，但不顯示類別、方法等等)。</br>2.  屬於某個專案的所有檔案會顯示為一般清單，而非樹狀結構檢視。 當檔案屬於專案的資料夾時，我們會顯示檔案的相對路徑，而不是僅在搜尋檢視上顯示檔案名稱。</br>搜尋檢視中的檔案項目沒有操作功能表。|以非 LSL 模式載入整個解決方案可獲得傳統的方案總管搜尋。</br>您也可以使用 Visual Studio IDE 搜尋。|
|C++ 專案的物件瀏覽器|物件瀏覽器只會顯示已載入專案的組件/WinMD 參考。|載入想要以物件瀏覽器查看資訊的專案。|

> [!Note]
> 感謝我們的合作夥伴，包括 Resharper 在內的熱門延伸模組也能搭配套輕量型解決方案載入使用。

我們欣然樂見能夠最佳化開發人員解決方案載入時間效能的創新。 因為這是一項新功能，所以我們會主動查看客戶的意見反應以及解決已知問題。 我們期待收到您的意見反應。 您可以向 Visual Studio 解決方案載入最佳化小組傳送電子郵件：lslsupport@microsoft.com

## <a name="see-also"></a>另請參閱
[Visual Studio 效能祕訣和訣竅](../ide/visual-studio-performance-tips-and-tricks.md)
