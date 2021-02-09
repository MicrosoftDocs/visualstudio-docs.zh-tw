---
title: 圖形 API 和記憶體統計資料 |Microsoft Docs
description: 請參閱「圖形 API 統計資料」和「記憶體統計資料工具」，其中顯示各種資源的 Direct3D API 使用量和 GPU 記憶體耗用量資訊。
ms.custom: SEO-VS-2020
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 08c9f518f6d56f2ec211ef494da3890a56bf1369
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882293"
---
# <a name="graphics-api-and-memory-statistics"></a>圖形 API 和記憶體統計資料
<!-- VERSIONLESS -->
Visual Studio 2017 及更高版本的支援圖形 API 統計資料和記憶體統計資料工具。  這兩項工具可讓您查看有關 Direct3D API 使用量的各種資訊，以及各種資源的 GPU 記憶體耗用量。

## <a name="graphics-api-statistics"></a>圖形 API 統計資料
Visual Studio 圖形診斷中的圖形 API 統計資料可讓您查看所有已進行的 Direct3D 呼叫，以及每個呼叫的計數。  若要查看視窗，請選取 [ **view > API Statistics]** 功能表項目。

![API 統計資料](media/gfx_diag_api_statistics.png)

這項工具在探索您可能不知道您正在進行的 DirectX 呼叫時很方便，或呼叫您太常進行的呼叫。

您可以在視窗中按一下滑鼠右鍵，將所有資料複製為 CSV，並將其貼入 Excel 之類的資料，以供進一步分析。

## <a name="memory-statistics"></a>記憶體統計資料
此工具會顯示圖形驅動程式配置給您在畫面格中建立之資源所需的記憶體數量。  若要查看這個視窗，請選取 [ **> 記憶體統計資料]** 功能表項目的 [view]。

![記憶體統計資料](media/gfx_diag_memory_statistics.png)

[ **GPU 配置** ] 資料行會 **顯示事件資料行中** 顯示的事件所使用的記憶體數量。  您也可以選取 [監看式 ![ ] 圖示監看圖示 ](media/gfx_watch.png) ，以查看所選事件的 [資源歷程記錄](graphics-event-list.md#resource-history) 。

如同 API 統計資料工具，您可以在視窗中按一下滑鼠右鍵，將所有資料複製為 CSV，然後將其貼入 Excel 之類的資料，以供進一步分析。

## <a name="see-also"></a>另請參閱
- [圖形診斷 (對 DirectX 圖形進行偵錯)](visual-studio-graphics-diagnostics.md)
- [資源歷程記錄](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->