---
title: 檢視最近的作業
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 55865e4907175664e8a8bfb8a813ff8d02c85b69
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638436"
---
# <a name="view-recent-job-performance-and-details"></a>檢視最近的作業效能和詳細資料

提交作業之後，您可以檢視作業清單，以查看它們的狀態、期間及其他資訊。

1. 在**伺服器資源管理員**中,展開特定的計算上下文。
2. 按兩下 [作業]****。
3. 您會看到已提交到該計算內容的作業清單。
4. 在清單中選擇特定**作業**以詳細資訊。

![監視作業](media/job-details/monitor-jobs.png)

> 提交到 Linux VM 的作業歷程記錄會儲存在 VM 上的 /tmp 目錄中。 因此，每當重新啟動時，作業歷程記錄便會清除。 若要永久儲存您的作業歷程記錄，請在 Azure Machine Learning 中將您的 VM 設定為計算內容，然後提交作業到 Azure Machine Learning (選取您的 VM 作為計算內容)。
