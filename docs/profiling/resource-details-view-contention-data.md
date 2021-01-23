---
title: 資源詳細資料檢視 - 爭用資料 | Microsoft Docs
description: 瞭解 [資源詳細資料] view 如何呈現由所選資源的爭用所造成之封鎖事件的時間軸圖形。
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcedetails
helpviewer_keywords:
- Resource Details view
ms.assetid: a4ecfe1c-abbc-4fb3-9ab2-34de50486901
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 45babe50e794e0831fd0e93048b32feaf18be87a
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720354"
---
# <a name="resource-details-view---contention-data"></a>資源詳細資料檢視 - 爭用資料
資源詳細資料檢視會在時間軸圖形顯示因爭用所選取的資源而造成的封鎖事件。 因為另一個執行緒已鎖定資源的存取權時，所以會強制執行緒暫停執行而發生封鎖事件。

 此檢視會在執行緒時間軸上，以橫條表示每個執行緒的執行時間軸，並以直條表示每個封鎖事件。 如有必要，您可以放大時間軸的某區段來檢視個別事件。 若要檢視造成該事件的函式執行路徑 (呼叫堆疊)，請按一下事件列。 該函式隨即出現在 [呼叫堆疊] 視窗中。 當函式的原始程式碼可供使用時，您可以按一下函式名稱，在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的介面中編輯原始程式檔。

## <a name="procedures"></a>程序

#### <a name="to-magnify-a-timeline-segment"></a>放大時間軸區段

- 將滑鼠指標拖曳時間軸的某一區域上方。

     放開滑鼠按鈕之後，檢視就會縮放為選取的時間區段。 您可以重複此流程，以進一步放大該區段。 時間捲軸的捲動方塊代表出現在檢視中的時間區段相對大小。

#### <a name="to-zoom-out-on-a-timeline"></a>在時間軸上縮小

- 請執行下列其中一個步驟：

  - 按一下 [縮小] 以返回上一個縮放層級。

  - 按一下 [顯示比例重設]，在檢視中顯示所有的時間軸。

#### <a name="to-view-the-call-stack-of-an-event"></a>檢視事件的呼叫堆疊

- 在時間軸圖形中，按一下事件列。

#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>檢視或編輯呼叫堆疊中函式的原始程式碼

- 在 [呼叫堆疊] 視窗中，按一下該函式名稱。

  該函式的原始程式碼必須是目前專案的一部分。

#### <a name="to-view-the-call-tree-of-contention-events-for-the-resource"></a>檢視資源的爭用事件呼叫樹狀圖

- 在時間軸圖形中，按一下 [總計]。

     資源的爭用檢視隨即顯示。 如需詳細資訊，請參閱 [資源爭用視圖](../profiling/resource-contentions-view-contention-data.md)。

#### <a name="to-view-all-the-contention-events-of-a-thread"></a>檢視執行緒的所有爭用事件

- 在時間軸圖形中，按一下該執行緒的名稱或 ID。

     所選取執行緒的執行緒詳細資料檢視隨即顯示。 如需詳細資訊，請參閱[執行緒詳細資料檢視](../profiling/thread-details-view-contention-data.md)。
