---
title: 使用 TensorBoard 監視
description: 瞭解如何使用 Visual Studio 以 TensorBoard 將模型定型進度視覺化。
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: edb6fe17902ad84ec6d7a6e5b9929bd965e7c29b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841389"
---
# <a name="monitor-with-tensorboard"></a>使用 TensorBoard 監視

您可以使用 TensorBoard 視覺化您的模型定型。

1. 以滑鼠右鍵按一下您的專案，按一下 [Run TensorBoard] \(執行 TensorBoard\)，然後選取您輸出 TensorBoard 記錄檔的目錄。

    ![已選取 MNIST 專案 Visual Studio 方案總管的螢幕擷取畫面。 開啟內容功能表，然後選取 [執行 TensorBoard] 命令。](media/monitor-tensorboard/run-tensorboard.png)

2. 請注意，錯誤已隨著時間遞減，表示品質正在改善。

    ![[主要 TensorBoard] 視窗的螢幕擷取畫面，其中顯示 TensorBoard 記錄中資料的圖形視覺效果。](media/monitor-tensorboard/tensorboard.png)
