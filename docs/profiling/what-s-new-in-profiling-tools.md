---
title: 程式碼剖析的新功能 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling
- what's new
ms.assetid: d4736cc8-8961-4089-be9e-d5190ce8353c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0acc7d48967fba4e05d139a6f84107800cea5393
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/20/2018
ms.locfileid: "36297773"
---
# <a name="whats-new-in-profiling-tools-in-includevsdev15miscincludesvsdev15mdmd"></a>[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] 中分析工具的新功能

診斷工具所包含的新視覺效果可協助您識別 App 中需要修正的問題。 診斷工具現已支援 ASP.NET App。

如需其他資訊，請參閱 [[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] 版本資訊](/visualstudio/releasenotes/vs2017-relnotes#debuggingdiag)。

已在工具中新增 [摘要] 索引標籤，可協助您專注在效能分析的重要區域。 此索引標籤顯示所發生事件的數量、讓您拍攝堆積的快照，以及快速啟用 CPU 使用量收集。 此檢視會顯示任何的 [Application Insights](https://azure.microsoft.com/en-us/documentation/articles/app-insights-visual-studio/) 或 [UI 分析](/visualstudio/releasenotes/vs2017-relnotes#UIAnalysis)事件。 此外，在 Visual Studio Enterprise 中，此檢視會顯示 IntelliTrace 事件。

![診斷工具摘要索引標籤](../profiling/media/DiagToolsSummaryTab-2.png "DiagToolsSummaryTab")

CPU 使用量工具有[新的視覺效果](../profiling/Beginners-Guide-to-Performance-Profiling.md)，可協助您識別最可能造成效能問題的函數。 新的 [呼叫端/被呼叫端] 檢視可讓您調查對所選函數進行來回呼叫的函數呼叫成本。

![診斷工具的呼叫端/被呼叫端檢視](../profiling/media/DiagToolsCallerCallee.png "DiagToolsCallerCallee")

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中分析](../profiling/index.md)
- [初步認識分析工具](../profiling/profiling-feature-tour.md)