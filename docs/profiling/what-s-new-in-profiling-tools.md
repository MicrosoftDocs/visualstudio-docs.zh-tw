---
title: Visual Studio 2017 中分析的新功能 | Microsoft Docs
description: 瞭解診斷工具組含新的視覺效果，可協助您識別應用程式中需要修正的問題。
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling
- what's new
ms.assetid: d4736cc8-8961-4089-be9e-d5190ce8353c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 9619daea30960f72b183447839db89adbaee7eb2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938482"
---
# <a name="whats-new-in-profiling-tools-in-includevs_dev15"></a>[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] 中分析工具的新功能

診斷工具所包含的新視覺效果可協助您識別 App 中需要修正的問題。 診斷工具現已支援 ASP.NET App。

如需詳細資訊，請參閱的[版本 [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](/visualstudio/releasenotes/vs2017-relnotes)資訊。

已在工具中新增 [摘要] 索引標籤，可協助您專注在效能分析的重要區域。 此索引標籤顯示所發生事件的數量、讓您拍攝堆積的快照，以及快速啟用 CPU 使用量收集。 這個視圖會顯示任何 [application insights](/azure/azure-monitor/app/visual-studio) 或 [UI 分析](/visualstudio/releasenotes/vs2017-relnotes) 事件。 此外，在 Visual Studio Enterprise 中，此檢視會顯示 IntelliTrace 事件。

![診斷工具摘要索引標籤](../profiling/media/diag-tools-summary-tab-2.png ">diagtoolssummarytab")

CPU 使用量工具有[新的視覺效果](../profiling/Beginners-Guide-to-Performance-Profiling.md)，可協助您識別最可能造成效能問題的函數。 新的 [呼叫端/被呼叫端] 檢視可讓您調查對所選函數進行來回呼叫的函數呼叫成本。

![診斷工具呼叫端的被呼叫端視圖](../profiling/media/diag-tools-caller-callee-2.png ">diagtoolscallercallee")

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中的設定檔](../profiling/index.yml)
- [初步認識分析工具](../profiling/profiling-feature-tour.md)