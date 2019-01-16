---
title: 圖形 API 和記憶體統計資料 |Microsoft Docs
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 36feec786ba0bba71723073fb990054cc0206847
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916675"
---
# <a name="graphics-api-and-memory-statistics"></a>圖形 API 和記憶體統計資料
<!-- VERSIONLESS --> Visual Studio 2017 和更新版本支援的圖形 API 統計資料和記憶體統計資料的工具。  這兩個工具可讓您檢視資訊的各種部分 Direct3D API 使用方式，以及各種資源的 GPU 記憶體耗用量。

## <a name="graphics-api-statistics"></a>圖形 API 統計資料
在 Visual Studio 圖形診斷中的圖形 API 統計資料可讓您檢視所做的 Direct3D 呼叫和每個呼叫的計數。  若要檢視視窗，請選取**檢視 > API 統計資料**功能表項目。

![API 統計資料](media/gfx_diag_api_statistics.png)

這項工具可以探索您可能不知道您的 DirectX 呼叫正在進行，或您太常進行的呼叫中好用。

您可以以滑鼠右鍵按一下 [全部複製資料] 視窗中以 csv 格式，可以貼到類似 Excel 供進一步分析。

## <a name="memory-statistics"></a>記憶體統計資料
此工具會顯示在框架中建立圖形驅動程式資源配置的記憶體數量。  若要檢視此視窗，請選取**檢視 > 記憶體統計資料**功能表項目。

![記憶體統計資料](media/gfx_diag_memory_statistics.png)

**GPU 配置**資料行會顯示中顯示的事件所使用的記憶體數量**事件**資料行。  您也可以選取 [監看式] 圖示![監看式 圖示](media/gfx_watch.png)若要檢視[資源歷程記錄](graphics-event-list.md#resource-history)針對選取的事件。

如同 [API 統計資料] 工具中，您可以以滑鼠右鍵按一下 [全部複製資料] 視窗中以 csv 格式，可以貼到類似 Excel 供進一步分析。

## <a name="see-also"></a>請參閱  
[圖形診斷 (偵錯 DirectX 圖形)](visual-studio-graphics-diagnostics.md)   
[資源歷程記錄](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->