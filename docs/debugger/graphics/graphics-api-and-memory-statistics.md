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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa808e76e6655c5d57108c923b19794d0398b80c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735580"
---
# <a name="graphics-api-and-memory-statistics"></a>圖形 API 和記憶體統計資料
<!-- VERSIONLESS -->
Visual Studio 2017 和更新版本支援圖形 API 統計資料和記憶體統計資料工具。  這兩個工具可讓您查看 Direct3D API 使用方式的各種資訊，以及各種資源的 GPU 記憶體耗用量。

## <a name="graphics-api-statistics"></a>圖形 API 統計資料
Visual Studio 圖形診斷中的圖形 API 統計資料可讓您查看所有已進行的 Direct3D 呼叫，以及每個呼叫的計數。  若要查看視窗，請選取 [**觀看 > API 統計資料]** 功能表項目。

![API 統計資料](media/gfx_diag_api_statistics.png)

這項工具在探索您可能不知道的 DirectX 呼叫，或您經常進行的呼叫時，是很方便的。

您可以在視窗中按一下滑鼠右鍵，將所有資料複製成 CSV，這可以貼入 Excel 之類的專案進行進一步的分析。

## <a name="memory-statistics"></a>記憶體統計資料
此工具會顯示圖形驅動程式針對您在畫面格中建立的資源所配置的記憶體數量。  若要查看這個視窗，請選取 [ **view > Memory Statistics]** 功能表項目。

![記憶體統計資料](media/gfx_diag_memory_statistics.png)

[ **GPU 配置**] 資料行會顯示**事件**資料行中顯示的事件所使用的記憶體數量。  您也可以選取 [監看式] 圖示 ![watch 圖示 ](media/gfx_watch.png)，以查看所選事件的[資源歷程記錄](graphics-event-list.md#resource-history)。

就像 API 統計資料工具一樣，您可以在視窗中按一下滑鼠右鍵，將所有資料複製成 CSV，這可以貼入 Excel 之類的專案進行進一步的分析。

## <a name="see-also"></a>請參閱
- [圖形診斷 (偵錯 DirectX 圖形)](visual-studio-graphics-diagnostics.md)
- [資源歷程記錄](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->