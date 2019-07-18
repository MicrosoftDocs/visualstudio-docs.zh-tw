---
title: 效能提示 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aac7068fae27e2f0ba699f404374859ef7b91d1a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675303"
---
# <a name="perftips"></a>效能提示
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 偵錯工具 *「效能提示」* (PerfTips) 和已整合偵錯工具的 [診斷工具]  幫助您在偵錯時監視及分析應用程式效能。  
  
 雖然已整合偵錯工具的診斷工具是讓您在開發過程中注意效能問題的好方式，但偵錯工具可以對您的應用程式效能有重大的影響。 若要收集更精確的效能資料，請考慮使用也會在偵錯工具外部執行的 Visual Studio 診斷工具，做為效能調查額外之一部分。 請參閱[來執行分析工具，但不偵錯](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)。  
  
## <a name="perftips"></a>效能提示  
 當偵錯工具於中斷點或逐步執行的作業停止執行時，該中斷與上一個中斷點之間經過的時間會在 [編輯器] 視窗中顯示為提示。 如需詳細資訊，請參閱 [PerfTips:Performance Information at-a-glance while Debugging with Visual Studio](http://blogs.msdn.com/b/visualstudioalm/archive/2014/08/18/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio.aspx) (效能提示：使用 Visual Studio 偵錯時的效能資訊一覽)。  
  
 ![PerfTip](../profiling/media/dbgdiag-perf-perftip.png "DBGDIAG_PERF_PerfTip")  
  
## <a name="diagnostics-tools-window"></a>診斷工具視窗  
 在 [診斷工具] 視窗中會記錄中斷點和相關聯的計時資料  
  
 下圖顯示 Visual Studio 2015 Update 1 中的 [診斷工具] 視窗：  
  
 ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
- [中斷事件]  時間軸會標記在偵錯工作階段中叫用的中斷點。 按一下事件，以選取 [偵錯工具]  詳細資料清單。  
  
- [CPU 使用率]  圖形顯示偵錯工作階段中跨所有處理器核心的 CPU 使用變化。  
  
- [偵錯工具]  詳細資料窗格的 [事件]  清單包含每個中斷事件的項目。  
  
- 中斷事件的 [持續期間]  資料行會顯示此事件和上一個中斷點之間經過的時間。  
  
## <a name="turn-perftips-on-or-off"></a>開啟或關閉效能提示  
 若要啟用或停用效能提示：  
  
1. 在 [ **偵錯** ] 功能表上選擇 [ **選項**]。  
  
2. 請選取或清除 [偵錯時顯示已耗用的效能提示] 。  
  
## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>開啟或關閉 [診斷工具] 視窗  
 若要啟用或停用 [診斷工具] 視窗：  
  
1. 在 [ **偵錯** ] 功能表上選擇 [ **選項**]。  
  
2. 核取或清除 [偵錯時啟用診斷工具] 。
