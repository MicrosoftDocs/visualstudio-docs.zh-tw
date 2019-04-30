---
title: 圖形記錄文件 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.vsglog.error
- vs.graphics.experiment
- vs.graphics.vsglog
ms.assetid: 6ccb1269-d55f-49c4-920d-baedf7de2888
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aed2acd4dbf921d99bcefe2e74575401fc01c7d7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62895976"
---
# <a name="graphics-log-document"></a>圖形記錄文件
圖形記錄文件是在圖形診斷工作階段下執行應用程式時所發生圖形事件的記錄。 錄製之後，您可以在 Visual Studio 圖形分析器中檢查記錄來診斷轉譯和效能問題。

 這是圖形記錄文件在圖形分析器中的樣子：

 ![圖形記錄，其中包含兩個擷取的畫面格。](media/gfx_diag_demo_graphics_log_orientation.png "gfx_diag_demo_graphics_log_orientation")

## <a name="understanding-graphics-log-documents"></a>了解圖形記錄文件
 使用圖形分析器檢查圖形記錄文件，可以將對擷取期間所發生的轉譯目標造成影響的 Direct3D 事件視覺化。 您可以找出含有非預期輸出之呈現目標的區域。 當您在受影響區域中選取像素時，可以使用圖形診斷檢查像素及其著色器、影響它的 Direct3D 事件、導致那些事件的應用程式呼叫堆疊，以及支援那些事件的 DirectX 物件。 您可以使用此資訊診斷遊戲或應用程式中的呈現問題。

 視窗 (**Graphics Experiment.vsglog**) 上方顯示所選取畫面目前的轉譯目標輸出，而下方顯示含有所擷取畫面之縮圖影像的 [畫面清單]。

#### <a name="to-inspect-a-frame"></a>檢查畫面格

- 在 [畫面清單] 中，選取您要檢查的畫面。 圖形記錄文件上方的呈現目標輸出隨即更新，以顯示選取的畫面格。

#### <a name="to-inspect-a-pixel"></a>檢查像素

- 在圖形記錄文件上方，從呈現目標輸出中選取您要的像素。 選取像素後，您可以使用 [圖形像素記錄] 視窗，檢視所選取像素的詳細資訊。 如需詳細資訊，請參閱 <<c0> [ 像素歷史記錄](graphics-pixel-history.md)。

## <a name="playback-machine"></a>播放電腦
 [播放電腦] 也會顯示在 [畫面清單] 右上角。 播放電腦是一部電腦或一個裝置，用來在稍後的圖形診斷工作階段期間，從圖形記錄檔播放圖形事件。 透過使用不同的裝置 (非開發電腦) 播放所擷取的事件，您可以更精確地重現發生問題的執行環境；例如，您可以使用具有與開發電腦所使用之圖形硬體或驅動程式不同的電腦，或其他類型的裝置 (例如 ARM Windows RT 平板電腦或 Windows Phone 裝置)。

 如需有關如何指定播放電腦的資訊，請參閱[How to:變更圖形診斷播放電腦](how-to-change-the-graphics-diagnostics-playback-machine.md)。

## <a name="graphics-log-summary-information"></a>圖形記錄摘要資訊
 當圖形記錄檔是使用中文件時，[屬性] 視窗會顯示裝載圖形診斷擷取工作階段之環境的相關資訊。 隨即顯示數個分類的資訊。

 **Direct3D 資訊**列出擷取工作階段期間所使用之顯示卡的硬體和驅動程式功能的相關資訊。

|屬性|描述|
|--------------|-----------------|
|**10 位元 XR 高彩格式**|如果支援 10 位元 XR 高彩格式，則為 **True**，否則為 **False**。|
|**DirectCompute CS 4.x**|如果支援計算著色器 4.0，則為 **True**，否則為 **False**。|
|**雙精確度著色器**|如果顯示卡支援雙精確度 (64 位元) 浮點數，則為 **True**，否則為 **False**。|
|**驅動程式命令清單**|如果驅動程式支援命令清單，則為 **True**，否則為 **False**。|
|**驅動程式同時建立**|如果驅動程式支援同時 (非同步) 建立，則為 **True**，否則為 **False**。|
|**延伸格式 (BGRA 等)**|如果支援延伸格式 (例如 BGRA)，則為 **True**，否則為 **False**。|
|**最大 HW 功能層級**|顯示顯示卡所支援的最高功能層級。|

 **顯示資訊**列出擷取工作階段期間所使用之顯示卡的相關資訊。

|屬性|描述|
|--------------|-----------------|
|**描述**|顯示卡描述字串。|
|**顯示記憶體**|已安裝在圖形卡上的記憶體數量。|
|**驅動程式名稱**|圖形卡驅動程式的名稱。|
|**驅動程式版本**|圖形卡驅動程式的版本。|
|**名稱**|圖形卡的名稱。|

 **實驗檔案**列出擷取工作階段相關聯之實驗檔案的相關資訊。

|屬性|描述|
|--------------|-----------------|
|**路徑**|.vsglog 檔案的路徑。 **注意：** 在舊版擷取下，未使用此屬性。|

 **模組資訊**列出擷取工作階段期間由應用程式已載入的動態連結程式庫 (Dll) 的版本與名稱。

 **系統資訊**列出擷取工作階段期間，裝載應用程式的作業系統與硬體的相關資訊。

|屬性|描述|
|--------------|-----------------|
|**記憶體**|已安裝在電腦中的記憶體數量。|
|**OS 架構**|作業系統的目標 CPU 架構。|
|**OS 版本**|作業系統版本。|
|**處理器**|已安裝在電腦中的處理器。|
|**目標應用程式架構**|應用程式的目標 CPU 架構。 這可能與 **OS 架構**不同。|

 **目標應用程式**列出擷取工作階段的主體的應用程式的相關資訊。

|屬性|描述|
|--------------|-----------------|
|**上次修改日期/時間**|建置應用程式的日期和時間。|
|**路徑**|應用程式的路徑。|
|**處理序 ID**|指定給應用程式的處理序 ID。|
|**版本**|應用程式版本。|

 **VSG 記錄檔**列出圖形記錄文件的資訊。

| 屬性 | 描述 |
|------------------------| - |
| **建立者** | 已建立圖形記錄文件的應用程式名稱。 例如，如果已從 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 啟動擷取工作階段 (手動擷取)，則此屬性的值為 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 |
| **工作階段開始時間** | 擷取工作階段開始的日期和時間。 |
| **Size** | 圖形記錄文件的大小。 |

## <a name="see-also"></a>另請參閱
- [逐步解說：因端點著色而遺漏的物件](walkthrough-missing-objects-due-to-vertex-shading.md)
- [逐步解說：針對因著色而產生的顯示錯誤進行偵錯](walkthrough-debugging-rendering-errors-due-to-shading.md)