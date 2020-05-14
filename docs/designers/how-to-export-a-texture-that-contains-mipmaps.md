---
title: 如何：匯出包含 Mipmap 的材質
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 71d570e6dc7544911ebe2bb279aafb3a07620cbc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589405"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>如何：匯出包含 Mipmap 的材質

影像內容管線可以在您的專案建置階段中，從來源影像產生 mipmap 。 為達到特定的效果，有時候您必須以手動方式指定每個 MIP 層級的影像內容。 當不需要手動指定每個 MIP 級別的圖像內容時，在生成時生成 mipmap 可確保 mipmap 內容永遠不會變得不同步。它還消除了在運行時生成 mipmap 的性能成本。

本文將說明：

- 設定要由「影像內容管線」處理的來源影像。

- 設定影像內容管線以產生 mipmap。

## <a name="export-mipmaps"></a>匯出 Mipmap

Mipmap 在 3D 遊戲或應用程式中提供材質表面的自動螢幕空間詳細層級。 透過預先計算的紋理縮小採樣版本，增強遊戲或應用程式的轉譯效能。 預先計算的縮小採樣版本，表示整個紋理不必在每次被採樣時都縮小圖像。

### <a name="to-export-a-texture-that-has-mipmaps"></a>匯出具有 mipmap 的材質

1. 從基本材質著手。 載入現有影像檔，或創建一個，如["如何：創建基本紋理](../designers/how-to-create-a-basic-texture.md)"。 若要支援 mipmap，指定的材質寬度和高度大小都是 2 的相同乘冪，例如 64x64、256x256 或 512x512。

2. 設定您剛剛建立的材質檔案，以便供「影像內容管線」處理。 在**方案總管**中，開啟您建立之紋理檔案的捷徑功能表，然後選擇 [屬性]****。 在 **"配置屬性** > **常規"** 頁上，將 **"專案類型"** 屬性設置為**圖像內容管道**。 確定 [內容]**** 屬性是設定為 [是]****，且 [從組建中排除]**** 是設定為 [否]****。 選取 [**套用**]。

   此時會顯示 [影像內容管線]**** 組態屬性頁面。

3. 設定影像內容管線以產生 mipmap。 在 **"配置屬性** > **圖像內容管道** > **"一般**頁上，將**生成 Mips**屬性設置為 **"是"（/生成 mips）。**

4. 選取 [確定]****。

當您建置專案時，「影像內容管線」會將來源影像從工作格式轉換成您指定的輸出格式 (包括 MIP 層級)。 結果會複製到專案的輸出目錄。
