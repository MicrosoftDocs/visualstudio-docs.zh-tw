---
title: 圖形診斷總覽 |Microsoft Docs
description: Visual Studio 圖形診斷是一組用來記錄 Direct3D 活動的工具，並會分析記錄以針對轉譯和效能問題進行疑難排解。
ms.custom: SEO-VS-2020, seodec18
ms.date: 02/09/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ae7969a3eb0e33b46755cdb3fa92cc2bcbe19c8a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905184"
---
# <a name="overview-of-visual-studio-graphics-diagnostics"></a>Visual Studio 圖形診斷概觀
Visual Studio 圖形診斷是一組工具，用來記錄並分析 Direct3D 應用程式中的轉譯和效能問題。 圖形診斷可用於在 Windows 電腦本機或遠端電腦或裝置上執行的應用程式。

## <a name="using-graphics-diagnostics-to-debug-rendering-problems"></a>使用圖形診斷偵錯轉譯問題
 在圖形化的應用程式中偵測轉譯問題，並不像開始偵錯工具和逐步執行一些程式碼一樣簡單。 在每個框架中會根據狀態、資料、參數和程式碼的複雜來產生數十個唯一的像素，其中可能只有一些像素會出現您嘗試診斷的問題。 讓問題更複雜的情況是，產生各個像素的程式碼是在平行處理數百個像素的特殊硬體上執行。 傳統偵錯工具和技術 (即使在輕量的執行緒程式碼中也難以充分利用) 在面臨大量資料時的效果不佳。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的圖形診斷工具的目的是要協助您尋找轉譯問題，方式是開始使用可以識別問題的視覺成品，然後透過專注在相關的著色器程式碼、管線階段、繪製呼叫、資源和裝置狀態，在應用程式本身的原始程式碼中向後追蹤。

## <a name="directx-version-compatibility"></a>DirectX 版本相容性
 圖形診斷支援使用 Direct3D 10 或更新版本的應用程式，並為使用 Direct2D 的應用程式提供有限的支援。 不支援使用舊版 Direct3D、DirectDraw 或其他圖形應用程式開發介面的應用程式。

### <a name="windows-10-and-direct3d-12"></a>Windows 10 和 Direct3D 12
> [!NOTE]
> Visual Studio 針對 DirectX 12 遊戲建議 Windows 上的 PIX。 [Windows 上的 PIX](https://aka.ms/PIXonWindows) 是可完全支援 DirectX 12 的效能調整和偵錯工具。 請參閱這裡的[詳細資訊](visual-studio-graphics-diagnostics-directx-12.md)或[下載](https://aka.ms/downloadPIX)。


 Windows 10 引進了 *direct3d 12*，其本質上與 direct3d 10 和 direct3d 11 不同。 這些差異讓 DirectX 回復為符合現代圖形硬體，並釋放其所有潛力，但也帶來大量 API 變更，並讓程式設計人員對管理資源存留期和競爭負有更大的責任。 儘管有差異，但是與 direct3d 12 圖形診斷保持功能與 Direct3D 11.2 的圖形診斷相同。

 Windows 10 也支援舊版 Direct3D 以及依賴它們的遊戲和應用程式。 Visual Studio 中的圖形診斷繼續支援 Windows 10 上的 Direct3D 10 和 Direct3D 11。

### <a name="limited-direct2d-support"></a>有限的 Direct2D 支援
 由於 Direct2D 是一個建置於 Direct3D 之上的使用者模式應用程式開發介面，您可以使用 [圖形診斷] 協助偵錯 Direct2D 應用程式中的轉譯問題。 不過，由於只會記錄基礎 Direct3D 事件，而不會記錄較高層級的 Direct2D 事件，所以 Direct2D 事件不會出現在圖形事件清單。 此外，由於 Direct2D 事件與產生 Direct3D 事件之間的關聯性並不一定是明確的，因此對 Direct2D 應用程式使用圖形診斷並不簡單。 儘管如此，您可以使用圖形診斷取得那些使用 Direct2D 應用程式的低階轉譯問題的資訊。

## <a name="graphics-diagnostics-features-in-visual-studio"></a>Visual Studio 中的圖形診斷功能
 [圖形診斷] 具有用於診斷轉譯問題的專用介面 ([圖形分析器] 視窗)，但也會將一些工具新增至 Visual Studio 介面。

### <a name="the-graphics-toolbar-visual-studio"></a>圖形工具列 (Visual Studio)
 [圖形] 工具列可快速存取圖形診斷命令。

 [開始診斷] 按鈕會在 [圖形診斷] 下執行應用程式。 在 [圖形診斷] 下執行應用程式時，會啟用 [擷取下一個呈現的畫面格] 按鈕。

### <a name="diagnostics-capture-interface"></a>診斷擷取介面
 使用圖形診斷執行應用程式時，Visual Studio 會顯示一個診斷工作階段介面，可用來擷取畫面格，同時顯示目前的 CPU 和 GPU 負載。 會顯示 CPU 和 GPU 負載，以協助您識別因其效能特性 (非轉譯錯誤) 而想要擷取的畫面格。

 但這不是擷取畫面格的唯一方式。 使用程式設計擷取介面，或使用命令列擷取程式 (dxcap.exe)，也可以擷取畫面格。

 如需詳細資訊，請參閱[擷取圖形資訊](capturing-graphics-information.md)。

### <a name="gpu-usage"></a>GPU 使用量
 圖形診斷也可以分析 Direct3D 應用程式的效能。 因為記錄圖形事件詳細資料會扭曲程式碼分析資料，所以這與擷取圖形分析器要檢查的畫面格不同。

 如需詳細資訊，請參閱 [GPU 使用量](../../profiling/gpu-usage.md)。

### <a name="directx-control-panel"></a>DirectX 控制台
 DirectX 控制台是可以用來變更 DirectX 行為的 DirectX 元件。例如，您可以啟用 DirectX 執行階段元件的偵錯版本，選取要報告的偵錯訊息種類和禁止某些圖形硬體功能去模擬功能很少的硬體。 這個 DirectX 控制層級可以協助您偵錯及測試 DirectX 應用程式。 您可以從 Visual Studio 存取 DirectX 控制台。

#### <a name="to-open-the-directx-control-panel"></a>開啟 DirectX 控制台

- 在功能表列上，選擇 [偵錯]、[圖形]、[DirectX 控制台]。

## <a name="graphics-analyzer"></a>圖形分析器
 Visual Studio 圖形分析器是一個專用介面，用於檢查已擷取畫面格中的轉譯和效能問題。 在圖形分析器內，有數個工具可協助您探索和了解應用程式的轉譯行為。 每個工具都會公開正在檢查之畫面格的不同種類的資訊，而且工具設計成與直覺式縮小轉譯問題來源搭配使用，並從其在畫面格緩衝區中的外觀開始。

 此圖顯示圖形分析器中工具的一般版面配置。

 ![所有圖形偵錯工具視窗](media/graphicsdebuggerwindows.png "GraphicsDebuggerWindows")

### <a name="the-graphics-toolbar-graphics-analyzer"></a>圖形工具列 (圖形分析器)
 [圖形] 工具列可快速存取圖形分析器工具視窗。

 ![圖形診斷模式中的 [圖形] 工具列](media/vsg_toolbar.png "vsg_toolbar")

### <a name="graphics-log-document"></a>圖形記錄文件
 在圖形分析器內，圖形記錄文件是最重要的工具視窗。 這個視窗代表透過使用圖形診斷執行您的應用程式而擷取的所有畫面格。 在這裡，您可以選取要檢查的不同畫面格，或選取您想要使用像素歷史記錄工具檢查的特定像素。 本文件中顯示的畫面格緩衝區影像會變更以反映目前選取的事件，讓您可以看到一段時間後對畫面格緩衝區的影響。

 [圖形記錄文件](graphics-log-document.md)也是畫面格分析工具的進入點，可協助您透過下列方式了解畫面格效能：變更特定轉譯層面的設定方式，並提供要與原始比較的基準測試結果。

### <a name="event-list"></a>事件清單
 圖形事件會標示每個 Direct3D API 呼叫和使用者定義的事件。

 [事件清單](graphics-event-list.md)會顯示您正在檢查的畫面格期間所記錄的所有圖形事件。 為了協助您找到重要項目，可以透過階層方式 (在後續繪製呼叫下方會有最新狀態變更) 或做為時間軸來檢視事件清單。 此外，還會根據所屬佇列將事件加上顏色，而且您可以篩選清單，使其只包括您感興趣的事件。

 選取清單中的事件時，圖形分析工具的其餘部分會反映畫面格在該事件時的狀態。 如此一來，您可以看到任何事件對 GPU 的影響。 例如，您可以看到畫面格緩衝區上任何繪製呼叫的立即效果，即使它因後續繪製呼叫而變成模糊也是一樣。 部分事件也具有超連結，而您可以遵循以查看其參數或相關資源物件的詳細資料。

### <a name="pipeline-stages"></a>管線階段
 您應用程式中的每個繪製呼叫都會通過 Direct3D 所提供的圖形管線。 在管線的每個階段中，會有一個小程式 (稱為著色器) 轉換上一個階段的輸出，然後傳遞給下一個階段，直到它最後轉譯在螢幕上。 如果輸出格式與下一個階段不同，或任何一個階段只會產生不正確的結果，則許多轉譯錯誤都發生在管線階段之間的界限。 一般來說，您只能取得螢幕上看到的最終結果，並無法輕易地得知管線的哪個位置發生錯誤。

 [ [管線階段](graphics-pipeline-stages.md) ] 視窗會個別視覺化每個階段的結果，讓您可以更輕鬆地判斷呈現問題首次出現的階段。 決定好階段之後，就可以立即從 [管線階段] 視窗開始偵錯其著色器。

### <a name="graphics-state"></a>圖形狀態
 轉譯作業取決於一些通常會分散到多個物件的狀態。 許多種類的轉譯問題都是設定不正確的狀態所導致。

 [狀態](graphics-state.md)視窗會將每個繪製呼叫的相關狀態資訊都收集在一個位置，以方便尋找，同時醒目提示自前一個繪製呼叫之後發生的狀態變更。

### <a name="pixel-history"></a>像素歷史記錄
 在複雜的場景中，經常會看到像素在單一畫面格中著色多次。 有時，只是覆寫較早的色彩，但其他時候則是合併色彩以達到透明這類效果。 將它們合併在一起的結果沒有正確的外觀時，無法輕鬆地分辨是因為其中一種色彩不正確，還是問題合併方式發生問題。 其他時候，物件可能會遺失，因為基於某個原因而拒絕其對像素的比重。

 [ [圖元歷程記錄](graphics-pixel-history.md) ] 視窗會以視覺化方式呈現框架中每個圖元的完整著色器歷程記錄，包括已拒絕的投稿。 對於未拒絕的比重，它會顯示原始著色器結果，以及如何合併每個新色彩與前一個色彩。 運用這項資訊，較容易找出像素中混合著色器結果的錯誤來源，或在轉譯的物件因不正確地拒絕其對像素的比重時較容易找出錯誤來源。

### <a name="event-call-stack"></a>事件呼叫堆疊
 著色器程式碼不是 Direct3D 應用程式中的唯一轉譯問題來源，有時，您的應用程式原始碼傳遞錯誤的參數，或未正確地設定 Direct3D。 先前討論的像素歷史記錄功能可協助您找到一種錯誤，是轉譯的物件因其所有像素都遭拒而遺漏時。 這種錯誤通常發生在您錯誤地設定某個設定時 (例如，控制如何執行深度測試的設定)，而您通常可以在遺漏物件繪製呼叫之呼叫堆疊中的某處找到您的錯誤。

 [[事件呼叫堆疊](graphics-event-call-stack.md)] 視窗會顯示 [事件] 清單中，每個圖形事件的完整呼叫堆疊，甚至可讓您跳到您應用程式的原始程式碼 (如有偵錯資訊)。 這是功能強大的工具，用於從 GPU 上第一次出現錯誤的位置追蹤回您應用程式原始程式碼中產生錯誤的位置。

### <a name="object-table"></a>物件表
 可能有數百甚至數千個資源物件支援您應用程式所轉譯的每個畫面格。 這些可以包括背景緩衝區以及轉譯目標、紋理、頂點緩衝區、索引緩衝區、一般緩衝區；Direct3D 記住的所有項目幾乎都是物件。

 [物件資料表](graphics-object-table.md)會顯示在事件清單中選取的圖形事件時存在的所有物件。 因為一般應用程式中的大部分物件都是紋理，所以已最佳化事件清單，概略顯示影像的相關詳細資料。 [類型] 資料行告訴您每個資料列中是何種物件，[格式] 資料行則進一步顯示物件的子類型或版本。 也會顯示其他詳細資料。 有些物件也有超連結，您可以遵循以使用更特殊的檢視器，例如紋理 (您可以將紋理檢視為影像) 或緩衝區 (您可以選擇緩衝區檢視器如何透過定義緩衝區格式來剖析和顯示原始緩衝區位元組) 來檢視物件。

### <a name="frame-analysis"></a>畫面格分析
 您應用程式的圖形不只需要正確，也需要更快速。 甚至在功能較不強大的裝置 (例如使用整合式圖形的膝上型電腦或是行動電話) 上也是一樣。 而且它們仍然需要看起來不錯。

 [畫面分析](graphics-frame-analysis.md)工具透過自動變更應用程式使用 Direct3D 的方式，並提供進行比較的基準測試結果，來探索潛在的效能最佳化。 例如，畫面格分析可以在每個紋理上啟用 MIP 對應，這樣可能會顯示受益於 MIP 對應但目前尚未予以啟用的紋理。 在支援它的硬體上，畫面格分析也提供收集自 GPU 之效能計數器的資訊；這個層級的資訊可以識別硬體層級的效能問題，例如大量紋理擷取區位或快取遺漏。

 但是，畫面格分析不只是快速，還可以在放棄最少視覺品質的同時獲得最高效能。 有時，在大型顯示器上看起來很棒的昂貴效果，在電話的小型螢幕上檢視時不會有相同的影響，而較簡單的效果則可能會看起來不錯，並且不會耗盡電池。 [圖形分析] 所提供的自動變更和基準測試可協助您找出多種裝置上您應用程式適合的平衡。

## <a name="see-also"></a>另請參閱
- [命令列擷取工具](command-line-capture-tool.md)
- [HLSL 偵錯工具](hlsl-shader-debugger.md)
