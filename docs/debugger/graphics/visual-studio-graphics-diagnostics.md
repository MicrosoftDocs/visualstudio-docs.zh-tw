---
title: "Visual Studio 圖形診斷 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
caps.latest.revision: "39"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 513404a9abda00844e8ba68e5e207961d6de4868
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-graphics-diagnostics"></a>Visual Studio 圖形診斷
Visual Studio*圖形診斷*是一組的記錄並分析 Direct3D 應用程式中的轉譯和效能問題的工具。 圖形診斷可以用於在 Windows 電腦、Windows 裝置模擬器或者遠端電腦或裝置上本機執行的應用程式。  
  
 圖形診斷工作流程會開始擷取您應用程式如何使用 Direct3D 的一筆記錄 (執行時為即時)，以立即分析、共用或儲存其行為以供稍後使用。 您可以啟動擷取工作階段和控制手動從 Visual Studio 或使用命令列擷取工具**dxcap.exe**。 也可以使用圖形診斷擷取 API，透過程式設計方式起始和控制擷取工作階段。  
  
 已記錄擷取工作階段之後，其內容可以播放由 Visual Studio*圖形分析器*在任何時間，重新建立擷取的畫面格使用相同的資源，並呈現命令使用的應用程式。 然後，使用 [圖形分析器] 視窗中所提供的工具，可以詳細分析所有擷取的畫面格。 這些工具可以用來檢查任何 Direct3D API 呼叫、資源、管線狀態物件、管線階段，甚至所擷取畫面格中任何像素的完整歷史記錄。 透過搭配使用這些工具，可以直覺式探索轉譯問題，這是從它如何出現在所擷取的畫面格中開始，並向下鑽研至其在應用程式原始程式碼、著色器或圖形資產中的根本原因。  
  
 若要診斷效能問題，可以擷取的畫面格分析使用*畫面格分析*工具。 這項工具透過自動變更應用程式使用 Direct3D 的方式，並對所有變化進行基準測試，來探索潛在的效能最佳化。 過去，您可能已經手動進行這些類型的變更並只對其進行基準測試，以找出哪些變更造成差異。 使用畫面格分析，您只需要進行已知道成功的變更。  
  
 圖形診斷有助於您具有豐富圖形之 Direct3D 應用程式的外觀而且執行效果最佳。  
  
 若要繼續[概觀](overview-of-visual-studio-graphics-diagnostics.md)來進一步了解 Visual Studio 圖形診斷所提供的功能。  
  
## <a name="in-this-section"></a>本章節內容  
 [概觀](overview-of-visual-studio-graphics-diagnostics.md)  
 介紹圖形診斷工作流程和工具。  
  
 [快速入門](getting-started-with-visual-studio-graphics-diagnostics.md)  
 在本節中，您將學習如何安裝 Visual Studio 圖形診斷，以及如何開始搭配使用圖形診斷與 Direct3D 應用程式。  
  
 [Capturing Graphics Information](capturing-graphics-information.md)  
 若要使用圖形診斷檢查您應用程式中的呈現問題，請先記錄有關應用程式如何使用 DirectX 的資訊。 在錄製工作階段中，為您的應用程式將會正常執行，您*擷取*（也就是選取） 感興趣的畫面格。 擷取包含如何呈現畫面格的詳細資訊。 您可以將擷取到的資訊儲存為圖形記錄文件，以供稍後再檢查，或與您小組的其他成員共用。  
  
 [GPU 使用量](gpu-usage.md)  
 若要使用圖形診斷進行您應用程式的程式碼分析，請使用 [GPU 使用量] 工具。 GPU 使用量可以用於與其他程式碼剖析工具 (例如 CPU 使用量) 搭配使用，以關聯可能造成應用程式中效能問題的 CPU 和 GPU 活動。  
  
 [圖形記錄文件](graphics-log-document.md)  
 若要開始檢查所記錄的圖形記錄檔，您可以使用圖形記錄文件視窗中選取所擷取的畫面，甚至是特定像素 —，以便您可以檢查詳細*事件*(亦即 DirectX API 呼叫） 會影響它.  
  
 [畫面格分析](graphics-frame-analysis.md)  
 在您選取畫面格之後，請使用圖形畫面格分析檢查和調整呈現效能。  
  
 [事件清單](graphics-event-list.md)  
 選取的畫面格之後，您使用**圖形事件清單**來檢查其事件，以判斷它們是否相關與呈現問題。  
  
 [狀態](graphics-state.md)  
 [狀態] 視窗可協助您了解在目前事件時作用的圖形狀態。  
  
 [管線階段](graphics-pipeline-stages.md)  
 在**圖形管線階段**視窗中，檢閱您目前所選取的事件處理的方式圖形管線各階段，讓您可以識別呈現問題第一次出現。 如果物件因轉換錯誤而未出現，或其中一個階段產生不符合下個階段所預期的輸出，則檢查管線階段會特別有用。  
  
 [事件呼叫堆疊](graphics-event-call-stack.md)  
 您使用**圖形事件呼叫堆疊**檢查目前所選取事件的呼叫堆疊，讓您可以瀏覽至與呈現問題相關的應用程式程式碼。  
  
 [像素歷史記錄](graphics-pixel-history.md)  
 使用**圖形像素歷史記錄**視窗，分析目前所選取像素如何受到影響，事件的事件或造成特定種類的轉譯問題的事件組合，您可以識別。 如果因像素著色器輸出不正確，或已錯誤地與畫面格緩衝區合併，導致錯誤地呈現物件；或者，如果因為在物件像素到達畫面格緩衝區之前捨棄物件像素，使得物件未顯示，則像素歷史記錄特別有用。  
  
 [物件表](graphics-object-table.md)  
 您使用**圖形物件表**來檢查屬性和特定 Direct3D 物件和資源的作用中目前所選事件的內容。 物件表可以協助您判斷在事件期間使用中的圖形裝置內容，以及檢查圖形資源的內容 (例如常數緩衝區、端點緩衝區和紋理)。  
  
 [HLSL 偵錯工具](hlsl-shader-debugger.md)  
 若要檢查著色器程式碼針對目前所選取的事件和圖形管線階段的行為方式，使用**HLSL 偵錯工具**，逐步執行程式碼，檢查變數內容，以及執行其他一般偵錯工作。 您也可以使用 HLSL 偵錯工具，檢查計算著色器程式碼，不論圖形管線是否進一步處理結果，或應用程式是否讀回結果。  
  
 [命令列擷取工具](command-line-capture-tool.md)  
 使用命令列擷取工具可快速擷取及播放圖形資訊，而不需使用 Visual Studio 或以程式設計方式擷取。 特別是，您可以使用命令列的擷取工具自動化，或在測試環境中使用。  
  
 [範例](graphics-diagnostics-examples.md)  
 數個範例示範如何同時使用多個圖形診斷工具，診斷不同類型的呈現問題。  
  
## <a name="related-sections"></a>相關章節  
  
|標題|說明|  
|-----------|-----------------|  
|[偵錯工具功能導覽](../debugging-in-visual-studio.md)|介紹 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 中的偵錯功能。|  
|[DirectX 圖形和遊戲](http://go.microsoft.com/fwlink/?LinkId=256498)|提供討論 DirectX 圖形技術的文章。|