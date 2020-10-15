---
title: 檢視最近的作業
description: 瞭解一旦提交作業之後，您就可以查看作業清單以查看其狀態、持續時間等等。
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: d67ee5810c1776176e1370839f0f7f43b9d0c55e
ms.sourcegitcommit: 9c57730000d5ced37d3887f3928b17076f49d0f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2020
ms.locfileid: "92099215"
---
# <a name="view-recent-job-performance-and-details"></a>檢視最近的作業效能和詳細資料

提交作業之後，您可以檢視作業清單，以查看它們的狀態、期間及其他資訊。

1. 在 **伺服器總管**中，展開特定的計算內容。
2. 按兩下 [作業]****。
3. 您會看到已提交到該計算內容的作業清單。
4. 選取清單中的特定 **工作** 以查看詳細資料。

![監視作業](media/job-details/monitor-jobs.png)

> 提交到 Linux VM 的作業歷程記錄會儲存在 VM 上的 /tmp 目錄中。 因此，每當重新啟動時，作業歷程記錄便會清除。 若要永久儲存您的作業歷程記錄，請在 Azure Machine Learning 中將您的 VM 設定為計算內容，然後提交作業到 Azure Machine Learning (選取您的 VM 作為計算內容)。
