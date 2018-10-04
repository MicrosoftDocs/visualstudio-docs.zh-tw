---
title: Visual Studio 圖形診斷概觀 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddd429d9-ac70-4ac4-9e69-299c6ea2df09
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2321e590591d6c3d80b41c58147820cf0248f403
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487663"
---
# <a name="overview-of-visual-studio-graphics-diagnostics"></a>Visual Studio 圖形診斷概觀
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[的 Visual Studio 圖形診斷概觀](https://docs.microsoft.com/visualstudio/debugger/graphics/overview-of-visual-studio-graphics-diagnostics)。  
  
Visual Studio*圖形診斷*是一份記錄並分析 Direct3D 應用程式中的轉譯和效能問題的工具。 圖形診斷可以用於在 Windows 電腦、Windows 裝置模擬器或者遠端電腦或裝置上本機執行的應用程式。  
  
## <a name="using-graphics-diagnostics-to-debug-rendering-problems"></a>使用圖形診斷偵錯轉譯問題  
 在具有豐富圖形的應用程式中偵錯轉譯問題，並不像啟動偵錯工具和逐步執行某些程式碼一樣簡單。 在每個框架中會根據狀態、資料、參數和程式碼的複雜來產生數十個唯一的像素，其中可能只有一些像素會出現您嘗試診斷的問題。 讓問題更複雜的情況是，產生各個像素的程式碼是在平行處理數百個像素的特殊硬體上執行。 傳統偵錯工具和技術 (即使在輕量的執行緒程式碼中也難以充分利用) 在面臨大量資料時的效果不佳。  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的圖形診斷工具的目的是要協助您尋找轉譯問題，方式是開始使用可以識別問題的視覺成品，然後透過專注在相關的著色器程式碼、管線階段、繪製呼叫、資源和裝置狀態，在應用程式本身的原始程式碼中向後追蹤。  
  
## <a name="directx-version-compatibility"></a>DirectX 版本相容性  
 圖形診斷支援使用 Direct3D 12、Direct3D 11 和 Direct3D 10 的應用程式，並為使用 Direct2D 的應用程式提供有限的支援。 不支援使用舊版 Direct3D、DirectDraw 或其他圖形應用程式開發介面的應用程式。  
  
### <a name="windows-10-and-direct3d-12"></a>Windows 10 和 Direct3D 12  
 Windows 10 導入新版的 Direct3D 中， *Direct3D 12*，本質上與 Direct3D 10 和 Direct3D 11 不同。 這些差異讓 DirectX 回復為符合現代圖形硬體，並釋放其所有潛力，但也帶來大量 API 變更，並讓程式設計人員對管理資源存留期和競爭負有更大的責任。 擁有絕佳偵錯工具對於協助圖形程式設計人員進行這項轉換十分重要，以讓 Visual Studio 2015 中的圖形診斷從一開始就支援 Direct3D12。 儘管有這些差異，具有 Direct3D 12 的圖形診斷還是會維護具有 Direct3D 11.2 之圖形診斷的功能同位檢查，但目前的例外是畫面格分析功能。 很快將會加入 Direct3D 12 中的畫面格分析支援，接著收入新的診斷工具，協助您解決可能會在 Direct3D 12 中遇到的新類型錯誤。  
  
 Windows 10 也支援舊版 Direct3D 以及依賴它們的遊戲和應用程式。 Visual Studio 2015 中的圖形診斷會繼續支援 Windows 10 以及 Windows 8.1 上的 Direct3D 10 和 Direct3D 11。  
  
### <a name="windows-81-and-direct3d-112"></a>Windows 8.1 和 Direct3D 11.2  
 在 [!INCLUDE[win81](../includes/win81-md.md)] 中，DirectX 11.2 引進支援透過其執行階段擷取圖形資訊的新功能。 [!INCLUDE[win81](../includes/win81-md.md)] 使用新的執行階段型擷取 — 稱為*穩固擷取*— 專屬於之所有 DirectX 版本的[!INCLUDE[win81](../includes/win81-md.md)]支援。 穩固擷取也支援 Direct3D 11.2 的新功能。  
  
### <a name="limited-direct2d-support"></a>有限的 Direct2D 支援  
 由於 Direct2D 是一個建置於 Direct3D 之上的使用者模式應用程式開發介面，您可以使用圖形診斷協助偵錯 Direct2D 應用程式中的轉譯問題。 不過，由於只會記錄基礎 Direct3D 事件，而不會記錄較高層級的 Direct2D 事件，所以 Direct2D 事件不會出現在圖形事件清單。 此外，由於 Direct2D 事件與產生 Direct3D 事件之間的關聯性並不一定是明確的，因此對 Direct2D 應用程式使用圖形診斷並不簡單。 儘管如此，您可以使用圖形診斷取得那些使用 Direct2D 應用程式的低階轉譯問題的資訊。  
  
## <a name="graphics-diagnostics-features-in-visual-studio"></a>Visual Studio 中的圖形診斷功能  
 圖形診斷具有用於診斷轉譯問題的專用介面 (圖形分析器視窗)，但也會將一些工具加入 Visual Studio 介面。  
  
### <a name="the-graphics-toolbar-visual-studio"></a>圖形工具列 (Visual Studio)  
 [圖形] 工具列可快速存取圖形診斷命令。  
  
 **開始診斷**按鈕執行應用程式在圖形診斷下的。 圖形診斷下執行應用程式時**擷取下一個呈現的畫面格**按鈕已啟用。  
  
### <a name="diagnostics-capture-interface"></a>診斷擷取介面  
 使用圖形診斷執行應用程式時，Visual Studio 會顯示一個診斷工作階段介面，可用來擷取畫面格，同時顯示目前的 CPU 和 GPU 負載。 會顯示 CPU 和 GPU 負載，以協助您識別因其效能特性 (非轉譯錯誤) 而想要擷取的畫面格。  
  
 但這不是擷取畫面格的唯一方式。 使用程式設計擷取介面，或使用命令列擷取程式 (dxcap.exe)，也可以擷取畫面格。  
  
 請參閱[擷取圖形資訊](../debugger/capturing-graphics-information.md)如需詳細資訊。  
  
### <a name="gpu-usage"></a>GPU 使用量  
 圖形診斷也可以分析 Direct3D 應用程式的效能。 因為記錄圖形事件詳細資料會扭曲程式碼分析資料，所以這與擷取圖形分析器要檢查的畫面格不同。  
  
 請參閱[GPU 使用量](../debugger/gpu-usage.md)如需詳細資訊。  
  
### <a name="directx-control-panel"></a>DirectX 控制台  
 DirectX 控制台是可以用來變更 DirectX 行為的 DirectX 元件。例如，您可以啟用 DirectX 執行階段元件的偵錯版本，選取要報告的偵錯訊息種類和禁止某些圖形硬體功能去模擬功能很少的硬體。 這個 DirectX 控制層級可以協助您偵錯及測試 DirectX 應用程式。 您可以從 Visual Studio 存取 DirectX 控制台。  
  
##### <a name="to-open-the-directx-control-panel"></a>開啟 DirectX 控制台  
  
-   在功能表列上選擇 **偵錯**，**圖形**， **DirectX 控制台**。  
  
## <a name="graphics-analyzer"></a>圖形分析器  
 Visual Studio 圖形分析器是一個專用介面，用於檢查已擷取畫面格中的轉譯和效能問題。 在圖形分析器內，有數個工具可協助您探索和了解應用程式的轉譯行為。 每個工具都會公開正在檢查之畫面格的不同種類的資訊，而且工具設計成與直覺式縮小轉譯問題來源搭配使用，並從其在畫面格緩衝區中的外觀開始。  
  
 此圖顯示圖形分析器中工具的一般版面配置。  
  
 ![所有的圖形偵錯工具視窗](../debugger/media/graphicsdebuggerwindows.png "GraphicsDebuggerWindows")  
  
### <a name="the-graphics-toolbar-graphics-analyzer"></a>圖形工具列 (圖形分析器)  
 [圖形] 工具列可快速存取圖形分析器工具視窗。  
  
 ![圖形診斷模式中的 [圖形] 工具列](../debugger/media/vsg-toolbar.png "vsg_toolbar")  
  
### <a name="graphics-log-document"></a>圖形記錄文件  
 在圖形分析器內，圖形記錄文件是最重要的工具視窗。 這個視窗代表透過使用圖形診斷執行您的應用程式而擷取的所有畫面格。 在這裡，您可以選取要檢查的不同畫面格，或選取您想要使用像素歷史記錄工具檢查的特定像素。 本文件中顯示的畫面格緩衝區影像會變更以反映目前選取的事件，讓您可以看到一段時間後對畫面格緩衝區的影響。  
  
 [圖形記錄文件](../debugger/graphics-log-document.md)是也進入點，畫面格分析工具，可協助您了解畫面格效能變更特定轉譯層面所設定的方式，並提供基準測試結果與與原始比較。  
  
### <a name="event-list"></a>事件清單  
 圖形事件會標示每個 Direct3D API 呼叫和使用者定義的事件。  
  
 [事件清單](../debugger/graphics-event-list.md)顯示所有您所檢查的畫面格期間所記錄的圖形事件。 為了協助您找到重要項目，可以透過階層方式 (在後續繪製呼叫下方會有最新狀態變更) 或做為時間軸來檢視事件清單。 此外，還會根據所屬佇列將事件加上顏色，而且您可以篩選清單，使其只包括您感興趣的事件。  
  
 選取清單中的事件時，圖形分析工具的其餘部分會反映畫面格在該事件時的狀態。 如此一來，您可以看到任何事件對 GPU 的影響。 例如，您可以看到畫面格緩衝區上任何繪製呼叫的立即效果，即使它因後續繪製呼叫而變成模糊也是一樣。 部分事件也具有超連結，而您可以遵循以查看其參數或相關資源物件的詳細資料。  
  
### <a name="pipeline-stages"></a>管線階段  
 您應用程式中的每個繪製呼叫都會通過 Direct3D 所提供的圖形管線。 在管線的每個階段中，會有一個小程式 (稱為著色器) 轉換上一個階段的輸出，然後傳遞給下一個階段，直到它最後轉譯在螢幕上。 如果輸出格式與下一個階段不同，或任何一個階段只會產生不正確的結果，則許多轉譯錯誤都發生在管線階段之間的界限。 一般來說，您只能取得螢幕上看到的最終結果，並無法輕易地得知管線的哪個位置發生錯誤。  
  
 [管線階段](../debugger/graphics-pipeline-stages.md) 視窗會單獨視覺化每個階段的結果，以便您可以更輕鬆地判斷哪一個階段中第一次出現轉譯問題。 決定好階段之後，就可以立即從 [管線階段] 視窗開始偵錯其著色器。  
  
### <a name="graphics-state"></a>圖形狀態  
 轉譯作業取決於一些通常會分散到多個物件的狀態。 許多種類的轉譯問題都是設定不正確的狀態所導致。  
  
 [狀態](../debugger/graphics-state.md)視窗以便更輕鬆地尋找，並反白顯示狀態變更發生自前一個繪製呼叫的也會收集在一處同時每個繪製呼叫的相關狀態資訊。  
  
### <a name="pixel-history"></a>像素歷史記錄  
 在複雜的場景中，經常會看到像素在單一畫面格中著色多次。 有時，只是覆寫較早的色彩，但其他時候則是合併色彩以達到透明這類效果。 將它們合併在一起的結果沒有正確的外觀時，無法輕鬆地分辨是因為其中一種色彩不正確，還是問題合併方式發生問題。 其他時候，物件可能會遺失，因為基於某個原因而拒絕其對像素的比重。  
  
 [像素歷史記錄](../debugger/graphics-pixel-history.md) 視窗會視覺化在框架中，包括已拒絕的比重的每個像素的完整著色器歷程記錄。 對於未拒絕的比重，它會顯示原始著色器結果，以及如何合併每個新色彩與前一個色彩。 運用這項資訊，較容易找出像素中混合著色器結果的錯誤來源，或在轉譯的物件因不正確地拒絕其對像素的比重時較容易找出錯誤來源。  
  
### <a name="event-call-stack"></a>事件呼叫堆疊  
 著色器程式碼不是 Direct3D 應用程式中的唯一轉譯問題來源，有時，您的應用程式原始碼傳遞錯誤的參數，或未正確地設定 Direct3D。 先前討論的像素歷史記錄功能可協助您找到一種錯誤，是轉譯的物件因其所有像素都遭拒而遺漏時。 這種錯誤通常發生在您錯誤地設定某個設定時 (例如，控制如何執行深度測試的設定)，而您通常可以在遺漏物件繪製呼叫之呼叫堆疊中的某處找到您的錯誤。  
  
 [事件呼叫堆疊](../debugger/graphics-event-call-stack.md)視窗會顯示 [事件] 清單中，每個圖形事件的完整呼叫堆疊，甚至可讓您跳到您的應用程式原始碼，如果偵錯資訊可用。 這是功能強大的工具，用於從 GPU 上第一次出現錯誤的位置追蹤回您應用程式原始程式碼中產生錯誤的位置。  
  
### <a name="object-table"></a>物件表  
 可能有數百甚至數千個資源物件支援您應用程式所轉譯的每個畫面格。 這些可以包括背景緩衝區以及轉譯目標、紋理、頂點緩衝區、索引緩衝區、一般緩衝區；Direct3D 記住的所有項目幾乎都是物件。  
  
 [物件表](../debugger/graphics-object-table.md)會顯示所有選取的圖形事件時存在的物件事件清單中。 因為一般應用程式中的大部分物件都是紋理，所以已最佳化事件清單，概略顯示影像的相關詳細資料。 [類型] 資料行告訴您每個資料列中是何種物件，[格式] 資料行則進一步顯示物件的子類型或版本。 也會顯示其他詳細資料。 有些物件也有超連結，您可以遵循以使用更特殊的檢視器，例如紋理 (您可以將紋理檢視為影像) 或緩衝區 (您可以選擇緩衝區檢視器如何透過定義緩衝區格式來剖析和顯示原始緩衝區位元組) 來檢視物件。  
  
### <a name="frame-analysis"></a>畫面格分析  
 您應用程式的圖形不只需要正確，也需要更快速。 甚至在功能較不強大的裝置 (例如使用整合式圖形的膝上型電腦或是行動電話) 上也是一樣。 而且它們仍然需要看起來不錯。  
  
 [畫面格分析](../debugger/graphics-frame-analysis.md)工具將透過自動變更應用程式使用 Direct3D 的方式，並提供用於比較的基準測試結果來探索潛在的效能最佳化。 例如，畫面格分析可以在每個紋理上啟用 MIP 對應，這樣可能會顯示受益於 MIP 對應但目前尚未予以啟用的紋理。 在支援它的硬體上，畫面格分析也提供收集自 GPU 之效能計數器的資訊；這個層級的資訊可以識別硬體層級的效能問題，例如大量紋理提取區位或快取遺漏。  
  
 但是，畫面格分析不只是快速，還可以在放棄最少視覺品質的同時獲得最高效能。 有時，在大型顯示器上看起來很棒的昂貴效果，在電話的小型螢幕上檢視時不會有相同的影響，而較簡單的效果則可能會看起來不錯，並且不會耗盡電池。 圖形分析所提供的自動變更和基準測試可協助您找出多種裝置上您應用程式適合的平衡。  
  
## <a name="see-also"></a>另請參閱  
 [命令列擷取工具](../debugger/command-line-capture-tool.md)   
 [HLSL 偵錯工具](../debugger/hlsl-shader-debugger.md)



