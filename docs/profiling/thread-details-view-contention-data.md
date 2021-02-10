---
title: 執行緒詳細資料檢視 - 爭用資料 | Microsoft Docs
description: 瞭解 [執行緒詳細資料] view 如何在分析執行的選取執行緒中，顯示封鎖事件的時間軸圖形。
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threaddetails
helpviewer_keywords:
- Thread Details view
ms.assetid: 874c3b1c-88d8-479a-bb35-1291d9aa8e67
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 535b87a7bfd87a0d3932f33370cf31510787d7e5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949346"
---
# <a name="thread-details-view---contention-data"></a>執行緒詳細資料檢視 - 爭用資料
執行緒詳細資料檢視會在時間軸圖形顯示因爭用資源，而在程式碼剖析執行選取的執行緒中造成的封鎖事件。 因為另一個執行緒已鎖定資源的存取權時，所以會強制該執行緒暫停執行而發生封鎖事件。

 此檢視會在執行緒的水平時間軸上，以橫條表示執行緒的執行時間軸，並以直條表示封鎖事件。 如有必要，您可以放大時間軸的某區段來檢視個別事件。 若要檢視造成該事件的函式執行路徑，請按一下事件列。 該函式隨即出現在 [呼叫堆疊] 視窗中。 當函式的原始程式碼可供使用時，您可以按一下函式名稱，在 Visual Studio IDE 中編輯原始程式檔。

## <a name="navigate-the-timeline"></a>巡覽時間軸

#### <a name="to-zoom-in-on-a-timeline-segment"></a>放大時間軸區段

- 按下並拖曳滑鼠指標以選取時間軸的某一區域。

     放開滑鼠之後，檢視就會縮放為選取的時間區段。 您可以重複這個更細部放大的流程。 時間捲軸的捲動方塊代表顯示在檢視中的時間區段相對大小。

#### <a name="to-zoom-out-on-a-timeline"></a>在時間軸上縮小

- 按一下 [縮小] 以返回上一個縮放層級。

- 按一下 [顯示比例重設]，在檢視中顯示整個時間軸。

#### <a name="to-view-the-call-stack-of-an-event"></a>檢視事件的呼叫堆疊

- 在時間軸圖形中，按一下代表事件的直條。

#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>檢視或編輯呼叫堆疊中函式的原始程式碼

- 在 [呼叫堆疊] 視窗中，按一下該函式名稱。

  該函式的原始程式碼必須是目前專案的一部分。

#### <a name="to-view-the-contention-events-of-a-resource-in-all-threads-in-the-profiling-run"></a>檢視程式碼剖析執行時所有執行緒中的資源爭用事件

- 在時間軸圖形中，按一下該資源的名稱或識別碼。

     所選取資源的[資源詳細資料檢視](../profiling/resource-details-view-contention-data.md)隨即顯示。

#### <a name="to-view-the-thread-contention-data-in-the-processes-window"></a>在 [處理序] 視窗中檢視執行緒爭用資料

- 在時間軸圖形中，按一下 [總計]。

     [處理序檢視](../profiling/process-view-contention-data.md)隨即顯示，並選取該執行緒。
