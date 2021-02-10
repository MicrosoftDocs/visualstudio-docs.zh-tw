---
title: GPU 使用量 | Microsoft Docs
description: 瞭解如何使用效能分析工具中的 GPU 使用量工具，更瞭解 Direct3D 應用程式的高階硬體使用量。
ms.date: 11/01/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 78f847acaf67a61064e64b765d9c138ec2fe93a9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959021"
---
# <a name="gpu-usage"></a>GPU 使用量

使用效能分析工具中的 GPU 使用量工具，更瞭解 Direct3D 應用程式的高階硬體使用量。 它可協助您瞭解應用程式的效能是否為 CPU 系結或 GPU 系結，並深入瞭解如何更有效地使用平臺的硬體。 GPU 使用量支援使用 Direct3D 12、Direct3D 11 和 Direct3D 10 的應用程式。 它不支援其他圖形 Api，例如 Direct2D 或 OpenGL。

以下是 [ **GPU 使用量報告** ] 視窗的樣子：

![GPU 使用量報告的螢幕擷取畫面，包含 CPU 和 GPU 時間軸](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")

## <a name="requirements"></a>規格需求

除了圖形診斷的需求以外，使用 GPU 使用量工具還需要下列條件：

- 支援所需計時檢測的 GPU 和驅動程式。

  > [!NOTE]
  > 如需所支援硬體和驅動程式的詳細資訊，請參閱本文件結尾的[硬體和驅動程式支援](#hwsupport)。

如需圖形診斷需求的詳細資訊， [請參閱開始](../debugger/graphics/getting-started-with-visual-studio-graphics-diagnostics.md)使用。

## <a name="use-the-gpu-usage-tool"></a>使用 GPU 使用量工具

當您在 [GPU 使用量] 工具下執行應用程式時，Visual Studio 會建立診斷會話。 此會話會即時繪製應用程式轉譯效能和 GPU 使用量的高階資訊。

啟動 GPU 使用量工具：

1. 在主功能表中，選擇 [ **Debug**  >  **效能和診斷** (]，或在鍵盤上按 Alt + F2) 。

2. 在 [ **效能及診斷** ] 中樞中，核取 [ **GPU 使用量**] 旁的方塊。 選擇性地核取您感興趣之其他工具旁邊的方塊。 您可以同時執行數個效能和診斷工具，以更完整地瞭解應用程式的效能。

    ![效能分析工具的螢幕擷取畫面，其中已選取 GPU 使用量](media/gpuusageselected.png "選取的 GPU 使用量")

   > [!NOTE]
   > 並非所有效能和診斷工具都可以同時使用。

3. 在 [ **效能及診斷** ] 中樞底部，選取 [ **開始** ]，在您選取的工具下執行您的應用程式。

即時顯示的高階資訊包括畫面格計時、畫面播放速率和 GPU 使用量。 這其中的每一項資訊都是單獨繪製的，但它們都使用一般的時間範圍，讓您可以輕鬆瞭解關聯性。

**畫面格時間 (ms)** 和 **每秒的畫面格 (FPS)** 圖形各有兩個紅色水平線，分別顯示60和每秒30個畫面格的效能目標。 在畫面時間圖形中，您的應用程式在圖形低於該線時超出效能目標，而在圖形高於該線時則會錯過目標。 針對每秒畫面格，這是相反的：當圖形高於該線時，您的應用程式超出效能目標，而在圖形低於該線時則會錯過目標。 您主要使用這些圖形來取得應用程式效能的高階概念，並找出您可能想要調查的較慢水準。 例如，如果您看到畫面播放速率突然下降或 GPU 使用率尖峰，則可能會有進一步的調查。

當您的應用程式在 GPU 使用量工具下執行時，診斷會話也會收集在 GPU 上執行之圖形事件的詳細資訊。 您可以使用這項資訊來產生應用程式如何利用硬體的更精細報告。 因為需要一些時間才能從所收集的資訊產生這份報告，所以只有在診斷工作階段完成資訊收集之後才能使用它。

當您想要更仔細地查看效能或使用率問題時，請停止收集效能資訊，以便產生報表。

若要產生和查看 GPU 使用量報表：

1. 在 [診斷會話] 視窗的下半部，選擇 [ **停止收集** ] 連結，或從左上角選取 [ **停止** ]。

   ![[GPU 使用量] 工具中 [診斷會話] 視窗的螢幕擷取畫面，其中顯示 [每秒畫面格數]、[GPU 使用量]、[停止] 按鈕和 [停止收集] 連結。](media/gfx_diag_gpu_usage_collect.png "gfx_diag_gpu_usage_collect")

2. 在報告的上半部，選取其中一個圖形中的一個區段，以顯示您想要調查的問題。 您的選取範圍最長可達3秒。 較長的區段會被截斷一開始。

   ![選取 [診斷會話] 時間軸部分的 [GPU 使用量] 工具中 [診斷會話] 視窗的螢幕擷取畫面。](media/gfx_diag_gpu_usage_select1.png "gfx_diag_gpu_usage_select1")

3. 若要在報表的下半部查看您選取範圍的詳細時間軸，請 **在 [...]按一下這裡以查看該範圍訊息的 GPU 使用量詳細資料，然後** 選取 [ **視圖詳細資料**]。

   ![診斷會話視窗的螢幕擷取畫面，其中已選取範圍](media/gfx_diag_gpu_usage_select2.png "gfx_diag_gpu_usage_select2")

此選取項目會開啟包含報表的新索引標籤式文件。 [GPU 使用量] 報告可協助您查看何時在 CPU 上啟動圖形事件、何時到達 GPU，以及 GPU 花費多少時間來執行它。 這項資訊可協助您找出瓶頸以及提高程式碼中平行處理的機會。

<!-- VERSIONLESS -->
## <a name="export-to-gpuview-or-windows-performance-analyzer"></a>匯出到 GPUView 或 Windows Performance Analyzer

從 Visual Studio 2017 開始，您可以透過 [GPUView](/windows-hardware/drivers/display/using-gpuview) 和 [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer) 來開啟此資料。 只需選取位於診斷會話右下角的 [ **在 GpuView 中開啟** ] 或 [ **在 WPA 中開啟** ] 連結。

![[診斷會話] 視窗的螢幕擷取畫面，其中已反白顯示連結](media/gfx_diag_open_in.png)
<!-- /VERSIONLESS -->

## <a name="use-the-gpu-usage-report"></a>使用 GPU 使用量報表

[GPU 使用量] 報表的上半部會顯示 CPU 處理活動、GPU 轉譯活動和 GPU 複製活動的時間軸。 這些時間軸會以淺灰色的垂直線分割，指出顯示器的垂直同步處理 (vsync) 。 橫條的頻率與使用收集 GPU 使用量資料) 的 [ **顯示** ] 下拉式清單中選取的其中一個顯示 (的重新整理率相符。

因為顯示器的重新整理頻率可能高於應用程式效能目標，所以 vsync 與您想要應用程式達到的畫面播放速率之間不會有 1 對 1 關聯性。 為了符合其效能目標，應用程式必須完成所有處理、進行轉譯，然後 `Present()` 以目標的畫面播放速率進行呼叫。 不過，在下一次 vsync 之後，將不會顯示轉譯的畫面格 `Present()` 。

[GPU 使用量] 報表的下半部會列出報表期間發生的圖形事件。 當您選取事件時，標記會出現在相關時間軸中的對應事件上。 通常，CPU 執行緒上的一個事件會顯示 API 呼叫，而其中一個 GPU 時間軸上的另一個事件會顯示 GPU 何時完成工作。 同樣地，當您在時間軸中選取事件時，報表會在報表的下半部反白顯示對應的圖形事件。

當您在報表的上半部放大時間軸時，只會顯示最耗時的事件。 若要查看持續時間較短的事件，請在指標裝置上使用 Ctrl + 滾輪，或是上方面板左下角的縮放控制，以放大時間軸。 您也可以拖曳時間軸面板的內容，以在所記錄的事件之間移動。

若要協助找出您要尋找的專案，請根據進程名稱、執行緒 Id 和事件名稱來篩選 GPU 使用量報表。 此外，您可以選擇決定 vsync 線條的顯示器重新整理頻率。 如果您的應用程式使用 [ ID3DUserDefinedAnnotation](/windows/desktop/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) 介面對轉譯命令進行分組，則可以使用階層方式對事件進行排序。

 以下是更多詳細資料：

|篩選控制項|Description|
|--------------------|-----------------|
|**處理**|您感興趣之進程的名稱。 在診斷會話期間使用 GPU 的所有進程都會包含在此下拉式清單中。 與進程相關聯的色彩是時間軸中線程活動的色彩。|
|**執行緒**|您感興趣的執行緒識別碼。 在多執行緒應用程式中，此資訊可協助您隔離出您感興趣之處理序的特定執行緒。 在每個時間軸中會反白顯示與所選取執行緒相關聯的事件。|
|**顯示器**|顯示其重新整理頻率的顯示器數目。 有些驅動程式可以設定成以單一大型虛擬顯示器形式來呈現多個實體顯示器。 您可能只會看到列出一個顯示器，即使電腦連接多部顯示器也是一樣。|
|**Filter**|您感興趣的關鍵字。 報表下半部中的事件只會包含完全或部分符合關鍵字的事件。 您可以指定用分號 (;) 分隔的多個關鍵字。|
|**階層排序**|這個核取方塊會指出是否保留或忽略透過使用者標記定義的事件階層。|

[GPU 使用量] 報表下半部中的事件清單會顯示每個事件的詳細資料。

|資料行|描述|
|------------|-----------------|
|**活動名稱**|圖形事件的名稱。 事件通常會對應至 CPU 執行緒時間軸中的事件以及 GPU 時間軸事件。 如果 GPU 使用量無法判斷事件的名稱，則可能會 *未歸屬* 事件名稱。 如需詳細資訊，請參閱此表格後面的附注。|
|**CPU 啟動 (奈秒)**|透過呼叫 Direct3D API 對 CPU 起始事件的時間。 時間的測量單位是奈秒，相對於應用程式的啟動時間。|
|**GPU 啟動 (奈秒)**|對 GPU 起始事件的時間。 時間的測量單位是奈秒，相對於應用程式的啟動時間。|
|**GPU 持續期間 (奈秒)**|在 GPU 上完成事件所花費的時間（以毫微秒為單位）。|
|**進程名稱**|事件的來源應用程式名稱。|
|**執行緒識別碼**|事件的來源執行緒 ID。|

> [!IMPORTANT]
> 如果您的 GPU 或驅動程式不支援所需的檢測功能，則所有事件都會顯示為 *未歸屬*。 如果您遇到此問題，請更新您的 GPU 驅動程式，然後再試一次。 如需詳細資訊，請參閱本檔結尾的 [硬體和驅動程式支援](#hwsupport) 。

## <a name="gpu-usage-settings"></a>GPU 使用量設定

您可以設定 GPU 使用量工具延後收集程式碼剖析資訊，而不是在應用程式啟動時立即開始收集資訊。 由於分析資訊的大小可能很大，因此當您知道應用程式效能的降低直到稍後才會出現時，此動作非常有用。

從啟動應用程式延後程式碼剖析：

1. 在主功能表中，選擇 [ **Debug**  >  **效能和診斷** (]，或在鍵盤上按 Alt + F2) 。

2. 在 [ **效能及診斷** ] 中樞的 [ **GPU 使用量**] 旁，選取 [ **設定** ] 連結。

3. 在 [ **GPU 分析設定]** 下的 **[一般** ] 屬性頁上，清除 [ **在應用程式啟動時開始分析]** 核取方塊，以延遲分析。

   ![物件屬性頁的螢幕擷取畫面，其中顯示集合選項](media/gfx_diag_gpu_usage_config.png "gfx_diag_gpu_usage_config")

> [!IMPORTANT]
> 目前，您無法延遲 Direct3D 12 應用程式的程式碼剖析。

在 GPU 使用量工具下執行應用程式後，GPU 使用量工具視窗下半部會顯示額外連結。 若要開始收集程式碼剖析資訊，請選擇 [開始收集其他詳細 GPU 使用量資料] 訊息中的 [開始] 連結。

## <a name="hardware-and-driver-support"></a><a name="hwsupport"></a> 硬體和驅動程式支援

下列是支援的 GPU 硬體和驅動程式：

|廠商|GPU 描述|需要驅動程式版本|
|------------|---------------------|-----------------------------|
|Intel®|第四代 Intel® 核心處理器 ("Haswell")<br /><br /> -   Intel® HD 圖形 (GT1)<br />-   Intel® HD 圖形 4200 (GT2)<br />-   Intel® HD 圖形 4400 (GT2)<br />-   Intel® HD 圖形 4600 (GT2)<br />-   Intel® HD 圖形 P4600 (GT2)<br />-   Intel® HD 圖形 P4700 (GT2)<br />-   Intel® HD 圖形 5000 (GT3)<br />-   Intel® Iris™ 圖形 5100 (GT3)<br />-   Intel® Iris™ Pro 圖形 5200 (GT3e)|(使用最新驅動程式)|
|AMD®|大部分的情況是因為 AMD Radeon™ HD 7000 系列 (排除 AMD Radeon™ HD 7350-7670) <br /><br /> AMD Radeon™ GPU、AMD FirePro™ Gpu 和 AMD FirePro GPU 加速器，採用圖形核心 (GCN) 架構<br /><br /> 具備 Graphics Core Next (GCN) 架構的 AMD® E 系列和 AMD A 系列加速處理單位 (APU) ('Kaveri'、'Kabini'、'Temash'、'Beema'、'Mullins')|14.7 RC3 或更新版本|
|NVIDIA®|自從 NVIDIA® GeForce®400系列<br /><br /> NVIDIA® GeForce® Gpu、NVIDIA Quadro® Gpu 和 NVIDIA® Tesla™具有 Fermi™、Kepler™或 Maxwell™架構的 GPU 加速器|343.37 或更新版本|

 目前不支援多 GPU 設定，例如 NVIDIA® SLI™和 AMD Crossfire™。 支援混合式圖形設置，例如 NVIDIA® Optimus™和 AMD Enduro™。
