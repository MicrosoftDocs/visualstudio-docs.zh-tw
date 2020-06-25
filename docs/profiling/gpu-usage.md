---
title: GPU 使用量 | Microsoft Docs
ms.date: 11/01/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6aa4cce032a5eb80a11568a83c1166b5690bd688
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85279872"
---
# <a name="gpu-usage"></a>GPU 使用量

使用 Visual Studio 效能和診斷中樞中的 [GPU 使用量] 工具，進一步瞭解 Direct3D 應用程式的高階硬體使用狀況。 它可協助您查看應用程式的效能是否符合 CPU 界限或 GPU 界限，並深入瞭解如何更有效地使用平臺的硬體。 GPU 使用量支援使用 Direct3D 12、Direct3D 11 和 Direct3D 10 的應用程式。 它不支援其他圖形 Api，例如 Direct2D 或 OpenGL。

[ **GPU 使用量報告**] 視窗看起來像這樣：

![GPU 使用量報告的螢幕擷取畫面，包含 CPU 和 GPU 時間軸](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")

## <a name="requirements"></a>規格需求

除了圖形診斷的需求之外，使用 GPU 使用量工具也需要下列各項：

- 支援所需計時檢測的 GPU 和驅動程式。

  > [!NOTE]
  > 如需所支援硬體和驅動程式的詳細資訊，請參閱本文件結尾的[硬體和驅動程式支援](#hwsupport)。

如需圖形診斷需求的詳細資訊，請參閱[開始](../debugger/graphics/getting-started-with-visual-studio-graphics-diagnostics.md)使用。

## <a name="use-the-gpu-usage-tool"></a>使用 GPU 使用量工具

當您在 [GPU 使用量] 工具下執行應用程式時，Visual Studio 會建立診斷會話。 此會話會將有關應用程式轉譯效能和 GPU 使用量的高階資訊，即時繪製在圖表中。

啟動 GPU 使用量工具：

1. 在主功能表中 **，選擇 [** 偵測  >  **效能及診斷**] （或在鍵盤上按 Alt + F2）。

2. 在 [**效能及診斷**] 中樞中，核取 [ **GPU 使用量**] 旁的方塊。 選擇性地核取您感興趣之其他工具旁邊的方塊。 您可以同時執行數個效能與診斷工具，以更完整地瞭解應用程式的效能。

    ![[效能及診斷] 中樞的螢幕擷取畫面，其中已選取 GPU 使用量](media/gpuusageselected.png "選取的 GPU 使用量")

   > [!NOTE]
   > 並非所有的效能和診斷工具都可以同時使用。

3. 在 [**效能及診斷**] 中樞的底部，選取 [**啟動**]，以在您選取的工具下執行您的應用程式。

即時顯示的高階資訊包括畫面格計時、畫面播放速率和 GPU 使用量。 這其中每一項資訊都是獨立繪製的，但它們全都使用共同的時間調整，讓您可以輕鬆地瞭解關聯性。

[**畫面格時間（毫秒）** ] 和 [**每秒畫面格數（FPS）** ] 圖形各有兩個紅色水平線，分別顯示60和每秒30個畫面格的效能目標。 在畫面時間圖形中，您的應用程式在圖形低於該線時超出效能目標，而在圖形高於該線時則會錯過目標。 針對每秒畫面數圖形，這是相反的：當圖形高於該線時，您的應用程式會超過效能目標，而當圖形低於該線時，就會遺漏目標。 您主要會使用這些圖表來取得應用程式效能的高階概念，並找出您可能想要調查的緩慢。 例如，如果您看到畫面播放速率突然下降或 GPU 使用率尖峰，可能會有進一步的調查。

當您的應用程式在 GPU 使用量工具下執行時，診斷會話也會收集在 GPU 上執行之圖形事件的詳細資訊。 您可以使用這項資訊來產生更精細的應用程式如何利用硬體的報告。 因為需要一些時間才能從所收集的資訊產生這份報告，所以只有在診斷工作階段完成資訊收集之後才能使用它。

當您想要更仔細地查看效能或使用率問題時，請停止收集效能資訊，讓您可以產生報告。

若要產生及查看 GPU 使用量報告：

1. 在 [診斷會話] 視窗的下半部，選擇 [**停止收集**] 連結，或選取左上角的 [**停止**]。

   ![[診斷會話] 視窗的螢幕擷取畫面](media/gfx_diag_gpu_usage_collect.png "gfx_diag_gpu_usage_collect")

2. 在報告的上半部，選取其中一個圖形中的一個區段，以顯示您想要調查的問題。 您的選取範圍最長可達3秒。 較長的區段會在一開始截斷。

   ![[診斷會話] 視窗的螢幕擷取畫面](media/gfx_diag_gpu_usage_select1.png "gfx_diag_gpu_usage_select1")

3. 若要在報表的下半部查看選取範圍的詳細時間軸，請在 [ **...]按一下這裡以查看該範圍訊息的 GPU 使用量詳細資料**，選取 [**查看詳細資料**]。

   ![[診斷會話] 視窗的螢幕擷取畫面，其中已選取範圍](media/gfx_diag_gpu_usage_select2.png "gfx_diag_gpu_usage_select2")

此選取項目會開啟包含報表的新索引標籤式文件。 [GPU 使用量] 報告可協助您查看何時在 CPU 上啟動圖形事件、何時到達 GPU，以及 GPU 執行它所需的時間。 這項資訊可協助您找出瓶頸以及提高程式碼中平行處理的機會。

<!-- VERSIONLESS -->
## <a name="export-to-gpuview-or-windows-performance-analyzer"></a>匯出到 GPUView 或 Windows Performance Analyzer

從 Visual Studio 2017 開始，您可以透過 [GPUView](/windows-hardware/drivers/display/using-gpuview) 和 [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer) 來開啟此資料。 只要選取 [**在 GpuView 中開啟**] 或 [**在 WPA 中開啟**]，位於診斷會話的右下角。

![[診斷會話] 視窗的螢幕擷取畫面，其中已反白顯示連結](media/gfx_diag_open_in.png)
<!-- /VERSIONLESS -->

## <a name="use-the-gpu-usage-report"></a>使用 GPU 使用量報告

[GPU 使用量] 報告的上半部會顯示 CPU 處理活動、GPU 轉譯活動和 GPU 複製活動的時間軸。 這些時間軸是以淺灰色的分隔號分割，表示顯示的 vsync。 橫條的頻率符合從中收集 GPU 使用量資料的其中一個顯示器（使用 [**顯示**] 下拉式清單選取）的重新整理頻率。

因為顯示器的重新整理頻率可能高於應用程式效能目標，所以 vsync 與您想要應用程式達到的畫面播放速率之間不會有 1 對 1 關聯性。 為了符合其效能目標，應用程式必須完成所有處理、進行轉譯，並在 `Present()` 目標的畫面播放速率上進行呼叫。 不過，在下一個 vsync 之後，才會顯示呈現的框架 `Present()` 。

[GPU 使用量] 報表的下半部會列出在報表期間發生的圖形事件。 當您選取事件時，標記會出現在相關時間軸的對應事件中。 通常，CPU 執行緒上的一個事件會顯示 API 呼叫，而其中一個 GPU 時間軸上的另一個事件會顯示 GPU 何時完成工作。 同樣地，當您在時間軸中選取事件時，報表會反白顯示報表下半部的對應圖形事件。

當您縮小報表上半部的時間軸時，只會顯示最耗費時間的事件。 若要查看持續時間較短的事件，請在指標裝置上使用 Ctrl + 滾輪，或上方面板左下角的縮放控制項來放大時間軸。 您也可以拖曳時間軸面板的內容，以在所記錄的事件之間移動。

若要協助尋找您要尋找的專案，請根據進程名稱、執行緒 Id 和事件名稱來篩選 GPU 使用量報告。 此外，您可以選擇決定 vsync 線條的顯示器重新整理頻率。 如果您的應用程式使用 [ ID3DUserDefinedAnnotation](/windows/desktop/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) 介面對轉譯命令進行分組，則可以使用階層方式對事件進行排序。

 以下是詳細資料：

|篩選控制項|說明|
|--------------------|-----------------|
|**處理程序**|您感興趣的進程名稱。 在診斷會話期間使用 GPU 的所有處理常式都會包含在此下拉式清單中。 與進程相關聯的色彩是時間軸中線程活動的色彩。|
|**執行緒**|您感興趣的執行緒識別碼。 在多執行緒應用程式中，此資訊可協助您隔離出您感興趣之處理序的特定執行緒。 在每個時間軸中會反白顯示與所選取執行緒相關聯的事件。|
|**顯示器**|顯示其重新整理頻率的顯示器數目。 有些驅動程式可以設定成以單一大型虛擬顯示器形式來呈現多個實體顯示器。 您可能只會看到列出一個顯示器，即使電腦連接多部顯示器也是一樣。|
|**Filter**|您想要的關鍵字。 報表下半部中的事件只會包含符合關鍵字的全部或部分。 您可以指定用分號 (;) 分隔的多個關鍵字。|
|**階層排序**|核取方塊，指出是否保留或忽略透過使用者標記定義的事件階層。|

[GPU 使用量] 報表下半部的事件清單會顯示每個事件的詳細資料。

|資料行|描述|
|------------|-----------------|
|**事件名稱**|圖形事件的名稱。 事件通常會對應至 CPU 執行緒時間軸中的事件以及 GPU 時間軸事件。 如果 GPU 使用量無法判斷事件的名稱，可能會*未歸屬*事件名稱。 如需詳細資訊，請參閱此表格後面的附注。|
|**CPU 啟動 (奈秒)**|透過呼叫 Direct3D API 對 CPU 起始事件的時間。 時間的測量單位是奈秒，相對於應用程式的啟動時間。|
|**GPU 啟動 (奈秒)**|對 GPU 起始事件的時間。 時間的測量單位是奈秒，相對於應用程式的啟動時間。|
|**GPU 持續期間 (奈秒)**|在 GPU 上完成事件所需的時間（以毫微秒為單位）。|
|**進程名稱**|事件的來源應用程式名稱。|
|**執行緒識別碼**|事件的來源執行緒 ID。|

> [!IMPORTANT]
> 如果您的 GPU 或驅動程式不支援所需的檢測功能，則所有事件都會顯示為*未歸屬*。 如果您遇到此問題，請更新您的 GPU 驅動程式，然後再試一次。 如需詳細資訊，請參閱本檔結尾的[硬體和驅動程式支援](#hwsupport)。

## <a name="gpu-usage-settings"></a>GPU 使用量設定

您可以設定 GPU 使用量工具延後收集程式碼剖析資訊，而不是在應用程式啟動時立即開始收集資訊。 由於分析資訊的大小可能很大，因此當您知道應用程式效能的降低直到稍後才會出現時，此動作非常有用。

從啟動應用程式延後程式碼剖析：

1. 在主功能表中 **，選擇 [** 偵測  >  **效能及診斷**] （或在鍵盤上按 Alt + F2）。

2. 在 [**效能及診斷**] 中樞的 [ **GPU 使用量**] 旁，選取 [**設定**] 連結。

3. 在 [ **GPU 分析設定]** 下的 [**一般**] 屬性頁面上，清除 [**在應用程式啟動時開始分析]** 核取方塊，以延後分析。

   ![物件屬性頁的螢幕擷取畫面，其中顯示集合選項](media/gfx_diag_gpu_usage_config.png "gfx_diag_gpu_usage_config")

> [!IMPORTANT]
> 目前，您無法延遲 Direct3D 12 應用程式的分析。

在 GPU 使用量工具下執行應用程式後，GPU 使用量工具視窗下半部會顯示額外連結。 若要開始收集程式碼剖析資訊，請選擇 [開始收集其他詳細 GPU 使用量資料]**** 訊息中的 [開始]**** 連結。

## <a name="hardware-and-driver-support"></a><a name="hwsupport"></a> 硬體和驅動程式支援

下列是支援的 GPU 硬體和驅動程式：

|廠商|GPU 描述|需要驅動程式版本|
|------------|---------------------|-----------------------------|
|Intel®|第四代 Intel® 核心處理器 ("Haswell")<br /><br /> -   Intel® HD 圖形 (GT1)<br />-   Intel® HD 圖形 4200 (GT2)<br />-   Intel® HD 圖形 4400 (GT2)<br />-   Intel® HD 圖形 4600 (GT2)<br />-   Intel® HD 圖形 P4600 (GT2)<br />-   Intel® HD 圖形 P4700 (GT2)<br />-   Intel® HD 圖形 5000 (GT3)<br />-   Intel® Iris™ 圖形 5100 (GT3)<br />-   Intel® Iris™ Pro 圖形 5200 (GT3e)|(使用最新驅動程式)|
|AMD®|大多數自 AMD Radeon™ HD 7000 系列（不包括 AMD Radeon™ HD 7350-7670）<br /><br /> AMD Radeon™ GPU、AMD FirePro™ Gpu 和 AMD FirePro GPU 加速器，具備圖形核心下一（GCN）架構<br /><br /> 具備 Graphics Core Next (GCN) 架構的 AMD® E 系列和 AMD A 系列加速處理單位 (APU) ('Kaveri'、'Kabini'、'Temash'、'Beema'、'Mullins')|14.7 RC3 或更新版本|
|NVIDIA®|由於 NVIDIA® GeForce®400系列<br /><br /> NVIDIA® GeForce® Gpu、NVIDIA Quadro® Gpu 和 NVIDIA® Tesla™ GPU 加速器，其中配備 Fermi™、Kepler™或 Maxwell™架構|343.37 或更新版本|

 目前不支援多 GPU 設定，例如 NVIDIA® SLI™和 AMD Crossfire™。 支援混合式圖形設置，例如 NVIDIA® Optimus™和 AMD Enduro™。
