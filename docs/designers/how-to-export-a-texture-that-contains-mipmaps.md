---
title: 如何：匯出包含 Mipmap 的材質
description: 瞭解在建立專案時，影像內容管線如何從來源映射產生 mipmap，以確保 mipmap 永遠不會被同步處理。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 783f8935b5d9eee25d6569dea9ba48b0eaeae8bd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930927"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>如何：匯出包含 Mipmap 的材質

影像內容管線可以在您的專案建置階段中，從來源影像產生 mipmap 。 為達到特定的效果，有時候您必須以手動方式指定每個 MIP 層級的影像內容。 如果您不需要以手動方式指定每個 MIP 層級的影像內容，在組建階段產生 mipmap 可確保 mipmap 內容永遠不會被同步處理。它也可消除在執行時間產生 mipmap 的效能成本。

本文將說明：

- 設定要由「影像內容管線」處理的來源影像。

- 設定影像內容管線以產生 mipmap。

## <a name="export-mipmaps"></a>匯出 Mipmap

Mipmap 在 3D 遊戲或應用程式中提供材質表面的自動螢幕空間詳細層級。 透過預先計算的紋理縮小採樣版本，增強遊戲或應用程式的轉譯效能。 預先計算的縮小採樣版本，表示整個紋理不必在每次被採樣時都縮小圖像。

### <a name="to-export-a-texture-that-has-mipmaps"></a>匯出具有 mipmap 的材質

1. 從基本材質著手。 載入現有的影像檔案，或依照 [如何：建立基本材質](../designers/how-to-create-a-basic-texture.md)中所述，建立一個影像檔案。 若要支援 mipmap，指定的材質寬度和高度大小都是 2 的相同乘冪，例如 64x64、256x256 或 512x512。

2. 設定您剛剛建立的材質檔案，以便供「影像內容管線」處理。 在 **方案總管** 中，開啟您建立之紋理檔案的捷徑功能表，然後選擇 [屬性]。 在 [設定 **屬性**] 的  >  **[一般**] 頁面上，將 [**專案類型**] 屬性設定為 [**影像內容管線**]。 確定 [內容] 屬性是設定為 [是]，且 [從組建中排除] 是設定為 [否]。 選取 [套用]  。

   此時會顯示 [影像內容管線] 組態屬性頁面。

3. 設定影像內容管線以產生 mipmap。 在 [設定 **屬性**  >  **映射內容管線**  >  **一般**] 頁面上，將 [**產生 Mips** ] 屬性設定為 **[是] (/generatemips)**。

4. 選取 [確定]。

當您建置專案時，「影像內容管線」會將來源影像從工作格式轉換成您指定的輸出格式 (包括 MIP 層級)。 結果會複製到專案的輸出目錄。
