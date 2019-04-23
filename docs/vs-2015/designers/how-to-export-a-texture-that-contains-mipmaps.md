---
title: HOW TO：匯出包含 Mipmap 的材質 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f525f4b31a3535f6ea7b89d0443402240365cc7d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60088648"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>HOW TO：匯出包含 Mipmap 的紋理
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

影像內容管線可以在您的專案建置階段中，從來源影像產生 mipmap 。 當您不需要手動指定每個 MIP 層級的影像內容時 — 您可能會為了取得特定的效果而這麼做 — 在建置時產生 mipmap 可確保 mipmap 內容永遠不會變成不同步，並且能消除在執行階段產生 mipmap 的效能成本。  
  
 本文件示範下列活動︰  
  
- 設定要由「影像內容管線」處理的來源影像。  
  
- 設定影像內容管線以產生 mipmap。  
  
## <a name="exporting-mipmaps"></a>匯出 Mipmap  
 Mipmap 在 3D 遊戲或應用程式中提供材質表面的自動螢幕空間詳細層級。 它藉由預先計算材質的縮小取樣版本，使得不必讓整個材質在每次取樣時都得縮小取樣，而增強遊戲或應用程式的呈現效能。  
  
#### <a name="to-export-a-texture-that-has-mipmaps"></a>匯出具有 mipmap 的材質  
  
1. 從基本材質著手。 載入現有的影像檔案，或建立下列文章中所述的影像檔案：[如何：建立基本材質](../designers/how-to-create-a-basic-texture.md)。 若要支援 mipmap，指定的材質寬度和高度大小都是 2 的相同乘冪，例如 64x64、256x256 或 512x512。  
  
2. 設定您剛剛建立的材質檔案，以便供「影像內容管線」處理。 在 [方案總管] 中，開啟您剛建立之材質檔案的捷徑功能表，然後選擇 [屬性]。 在 [組態屬性] > [一般] 頁面上，將 [項目類型] 屬性設定為 [影像內容管線]。 確定 [內容] 屬性是設定為 [是]，且 [從組建中排除] 是設定為 [否]，然後選擇 [套用] 按鈕。 此時會顯示 [影像內容管線] 組態屬性頁面。  
  
3. 設定影像內容管線以產生 mipmap。 在 [組態屬性] > [影像內容管線] > [一般] 頁面上，將 **產生 Mips** 屬性設定為 [是] (/generatemips)。  
  
4. 選擇 [確定]  按鈕。  
  
   當您建置專案時，「影像內容管線」會將來源影像從工作格式轉換成您指定的輸出格式 (包括 MIP 層級)，然後將結果複製到專案的輸出目錄。
