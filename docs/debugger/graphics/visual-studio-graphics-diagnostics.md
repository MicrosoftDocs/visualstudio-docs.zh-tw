---
title: 圖形診斷 |Microsoft Docs
description: Visual Studio 圖形診斷是一組用來記錄和分析 Direct3D 活動的工具。 您可以使用它們來針對轉譯和效能問題進行疑難排解。
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 679b9464ef10f121bbe38f486291b135872fb36b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861487"
---
# <a name="visual-studio-graphics-diagnostics"></a>Visual Studio 圖形診斷
>[!NOTE]
> Visual Studio 針對 DirectX 12 遊戲建議 Windows 上的 PIX。 [Windows 上的 PIX](https://aka.ms/PIXonWindows) 是可完全支援 DirectX 12 的效能調整和偵錯工具。 請參閱這裡的[詳細資訊](visual-studio-graphics-diagnostics-directx-12.md)或[下載](https://aka.ms/downloadPIX)。

Visual Studio 圖形診斷是一組工具，用來記錄並分析 Direct3D 應用程式中的轉譯和效能問題。 圖形診斷可以用於 Windows 電腦、Windows 裝置模擬器或者遠端電腦或裝置上本機執行的應用程式。

 圖形診斷工作流程會開始擷取您應用程式如何使用 Direct3D 的一筆記錄 (執行時為即時)，以立即分析、共用或儲存其行為以供稍後使用。 您可以從 Visual Studio 或使用命令列捕捉工具 **dxcap.exe**，手動起始和控制 Capture 會話。 您也可以使用圖形診斷 capture Api，以程式設計方式起始和控制 Capture 會話。

 記錄擷取工作階段之後，Visual Studio「圖形分析器」隨時都可以播放其內容，方法是使用完全相同資源並轉譯應用程式所使用的命令來重建所擷取畫面格。 然後，使用 [圖形分析器] 視窗中提供的工具，可以詳細分析任何已捕捉的畫面格。 這些工具可以用來檢查任何 Direct3D API 呼叫、資源、管線狀態物件、管線階段，甚至所擷取畫面格中任何像素的完整歷史記錄。 透過搭配使用這些工具，可以直覺式探索轉譯問題，這是從它如何出現在所擷取的畫面格中開始，並向下鑽研至其在應用程式原始程式碼、著色器或圖形資產中的根本原因。

 若要診斷效能問題，可以使用「畫面分析」工具分析所擷取的畫面格。 這項工具透過自動變更應用程式使用 Direct3D 的方式，並對所有變化進行基準測試，來探索潛在的效能最佳化。 過去，您可能已經手動進行這些類型的變更並只對其進行基準測試，以找出哪些變更造成差異。 使用畫面格分析，您只需要進行已知道成功的變更。

 圖形診斷有助於您具有豐富圖形之 Direct3D 應用程式的外觀而且執行效果最佳。

 繼續進行 [總覽](overview-of-visual-studio-graphics-diagnostics.md) ，深入瞭解圖形診斷提供的 Visual Studio。

## <a name="in-this-section"></a>本節內容
 [總覽](overview-of-visual-studio-graphics-diagnostics.md) 介紹圖形診斷的工作流程和工具。

 [開始使用](getting-started-with-visual-studio-graphics-diagnostics.md) 在本節中，您將瞭解如何安裝 Visual Studio 圖形診斷，以及如何開始搭配使用圖形診斷與 Direct3D 應用程式。

 [捕獲圖形資訊](capturing-graphics-information.md) 若要使用圖形診斷檢查應用程式中的轉譯問題，您必須先記錄應用程式如何使用 DirectX 的相關資訊。 在記錄工作階段期間，如果您的應用程式正常地執行，請「擷取」(亦即選取) 感興趣的畫面格。 擷取包含如何呈現畫面格的詳細資訊。 您可以將擷取到的資訊儲存為圖形記錄文件，以供稍後再檢查，或與您小組的其他成員共用。

 [GPU 使用量](../../profiling/gpu-usage.md) 若要使用圖形診斷來分析您的應用程式，請使用 [GPU 使用量] 工具。 GPU 使用量可以用於與其他程式碼剖析工具 (例如 CPU 使用量) 搭配使用，以關聯可能造成應用程式中效能問題的 CPU 和 GPU 活動。

 [圖形記錄檔](graphics-log-document.md) 若要開始檢查所記錄的圖形記錄，請使用圖形記錄文件視窗來選取已捕捉的框架（或甚至是特定圖元），讓您可以詳細檢查 *事件* (也就是 DirectX API 會呼叫影響它的) 。

 [畫面格分析](graphics-frame-analysis.md) 選取畫面格之後，您可以使用圖形畫面格分析來檢查和調整轉譯效能。

 [事件清單](graphics-event-list.md) 選取框架之後，您可以使用 [ **圖形事件清單** ] 來檢查其事件，以判斷它們是否與轉譯問題相關。

 [狀態](graphics-state.md) [狀態] 視窗可協助您瞭解在目前事件時作用的圖形狀態。

 [管線階段](graphics-pipeline-stages.md) 在 [ **圖形管線階段** ] 視窗中，您可以調查圖形管線的每個階段如何處理目前選取的事件，讓您可以識別呈現問題第一次出現的位置。 如果物件因轉換錯誤而未出現，或其中一個階段產生不符合下個階段所預期的輸出，則檢查管線階段會特別有用。

 [事件呼叫堆疊](graphics-event-call-stack.md) 您可以使用 [ **圖形事件呼叫堆疊** ] 檢查目前所選取事件的呼叫堆疊，以便流覽至與轉譯問題相關的應用程式程式碼。

 [圖元歷程記錄](graphics-pixel-history.md) 藉由使用 [ **圖形圖元歷史記錄** ] 視窗來分析受影響的事件，目前選取的圖元如何受到影響，您可以識別導致特定類型之轉譯問題的事件或事件組合。 如果因像素著色器輸出不正確，或已錯誤地與畫面格緩衝區合併，導致錯誤地呈現物件；或者，如果因為在物件像素到達畫面格緩衝區之前捨棄物件像素，使得物件未顯示，則像素歷史記錄特別有用。

 [物件資料表](graphics-object-table.md) 您可以使用 [ **繪圖物件表** ] 來檢查特定 Direct3D 物件的屬性和內容，以及目前所選事件的有效資源。 物件表可以協助您判斷在事件期間使用中的圖形裝置內容，以及檢查圖形資源的內容 (例如常數緩衝區、端點緩衝區和紋理)。

 [HLSL 偵錯工具](hlsl-shader-debugger.md) 若要檢查著色器程式碼針對目前所選取事件和圖形管線階段的行為方式，您可以使用 **HLSL 偵錯工具** 來逐步執行程式碼、檢查變數內容，以及執行其他一般的偵錯工具。 您也可以使用 HLSL 偵錯工具，檢查計算著色器程式碼，不論圖形管線是否進一步處理結果，或應用程式是否讀回結果。

 [命令列捕獲工具](command-line-capture-tool.md) 使用命令列捕捉工具可快速捕捉和播放圖形資訊，而不需使用 Visual Studio 或程式設計的捕捉。 特別是，您可以使用命令列的擷取工具自動化，或在測試環境中使用。

 [範例](graphics-diagnostics-examples.md) 數個範例示範如何搭配使用圖形診斷工具來診斷不同種類的轉譯問題。

## <a name="related-sections"></a>相關章節

| 標題 | 描述 |
| - | - |
| [偵錯工具功能導覽](../debugger-feature-tour.md) | 介紹 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 中的偵錯功能。 |
| [DirectX 圖形與遊戲](/windows/win32/directx) | 提供討論 DirectX 圖形技術的文章。 |
| [Visual Studio 中的 DirectX 12 支援](visual-studio-graphics-diagnostics-directx-12.md) | 瞭解 Visual Studio 中的 DirectX 12 支援 |
