---
title: "圖形 API 和記憶體統計資料 |Microsoft 文件"
ms.custom: 
ms.date: 03/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c34c505751153410896da66040c866676c3a7ee2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="graphics-api-and-memory-statistics"></a>圖形 API 和記憶體統計資料
<!-- VERSIONLESS -->
Visual Studio 2017 和更佳的支援圖形 API 統計資料和記憶體統計資料的工具。  這兩個工具可讓您檢視 Direct3D API 使用方式，以及 GPU 記憶體耗用量的各種資源的各種不同的位元的資訊。

## <a name="graphics-api-statistics"></a>圖形 API 統計資料
在 Visual Studio 圖形診斷中的圖形 API 統計資料可讓您檢視所做的 Direct3D 呼叫，以及每個呼叫的計數。  若要檢視視窗，請選取**檢視 > API 統計資料**功能表項目。

![應用程式開發介面的統計資料](media/gfx_diag_api_statistics.png)

此工具可能很方便探索您可能不了解您的 DirectX 呼叫正在進行，或呼叫您要經常進行中。

您可以以滑鼠右鍵按一下 [全部複製資料] 視窗中以 csv 格式，可以貼到類似 Excel，以便進一步分析。

## <a name="memory-statistics"></a>記憶體統計資料
此工具會顯示在框架中建立圖形驅動程式資源配置的記憶體數量。  若要檢視此視窗，請選取**檢視 > 記憶體統計資料**功能表項目。

![記憶體統計資料](media/gfx_diag_memory_statistics.png)

**GPU 配置**資料行會顯示中顯示的事件所使用的記憶體數量**事件**資料行。  您也可以選取 [監看式] 圖示![監看式 圖示](media/gfx_watch.png)檢視[資源記錄](graphics-event-list.md#resource-history)針對選取的事件。

如同 API 統計資料工具中，您可以滑鼠右鍵按一下 [全部複製資料] 視窗中以 csv 格式，可以貼到類似 Excel，以便進一步分析。

## <a name="see-also"></a>請參閱  
[圖形診斷 （偵錯 DirectX 圖形）](visual-studio-graphics-diagnostics.md)   
[資源記錄](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->