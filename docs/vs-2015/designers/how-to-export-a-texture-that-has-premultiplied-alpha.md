---
title: 如何：匯出包含預乘 Alpha 的材質 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 05348afa-f079-4f53-a05b-ecd91d13adab
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a68f6c58ad7e497dfc0e91e92f2cf40e4bd8d992
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897530"
---
# <a name="how-to-export-a-texture-that-has-premultiplied-alpha"></a>如何：匯出包含預乘 Alpha 的材質
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

影像內容管線可以從來源影像產生預乘 Alpha 的材質。 這些使用起來可以更簡單，且比起不包含預乘 Alpha 的材質更穩固。  
  
 本文件示範下列活動︰  
  
-   設定要由「影像內容管線」處理的來源影像。  
  
-   設定影像內容管線以產生預乘 Alpha。  
  
## <a name="premultiplied-alpha"></a>預乘 Alpha  
 預乘的 alpha 提供了許多優於傳統非預乘 alpha 的因為它更能代表實體物質與真實世界互動的光線分隔材質的色彩比重 (它會將加入的色彩場景） 從其半透明 （允許的基礎色彩量）。 使用預乘 Alpha 的一些優點包括︰  
  
-   使用預乘 Alpha 透明混色是關聯的作業。混用多種半透明材質的結果是相同的，而不論材質的混合順序。  
  
-   由於使用預乘 Alpha 透明混色的關聯本質，半透明物件的多階段呈現便簡化了。  
  
-   藉由使用預乘 Alpha，純粹加色法透明混色 (將 Alpha 設定為零) 和線性插補透明混色可以同時達成。 比方說，在粒子系統中的混合火粒子可能會變成使用線性插補混合成半透明煙霧物件。 若沒有預乘 Alpha，您將必須分別繪製火粒子與煙霧粒子，並修改繪製呼叫之間的呈現狀態。  
  
-   使用預乘的 alpha 的材質壓縮的更高品質會比不這麼做，和它們不會表現出變色的邊緣，或 「 光圈效果 」，這可能會讓您混合不使用預乘的 alpha 的材質時。  
  
#### <a name="to-create-a-texture-that-uses-premultiplied-alpha"></a>建立使用預乘 Alpha 的材質  
  
1. 從基本材質著手。 載入現有的影像檔案，或遵循[如何：建立基本材質](../designers/how-to-create-a-basic-texture.md)所述，建立影像檔案。  
  
2. 設定材質檔案，以便由影像內容管線處理。 在方案總管中，開啟材質檔案的捷徑功能表，然後選擇 [屬性]。 在 [組態屬性] > [一般] 頁面上，將 [項目類型] 屬性設定為 [影像內容管線]。 確定 [內容] 屬性是設定為 [是]，且 [從組建中排除] 是設定為 [否]，然後選擇 [套用] 按鈕。 此時會顯示 [影像內容管線] 組態屬性頁面。  
  
3. 設定影像內容管線以產生預乘 Alpha。 在 [組態屬性] > [影像內容管線] > [一般] 頁面上，將 [轉換成預乘 Alpha 格式] 屬性設定為 [是 (/generatepremultipliedalpha)]。  
  
4. 選擇 [確定]  按鈕。  
  
   當您建置專案時，「 影像內容管線來源映像將從工作格式轉換成您指定的輸出格式，這包括將影像轉換成預乘 alpha 格式，而且結果複製到專案的輸出目錄。



