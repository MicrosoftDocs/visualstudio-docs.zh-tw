---
title: HOW TO：匯出材質以搭配 Direct2D 或 Javascipt 應用程式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 241c25fe-764e-4e1b-ad32-b1377dcbb605
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 98b08fc8ebf2fca207d41b644032d7abbcd97a24
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65681733"
---
# <a name="how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps"></a>HOW TO：匯出紋理以與 Direct2D 或 Javascipt 應用程式搭配使用
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

「影像內容管線」能夠產生可與 Direct2D 的內部轉譯慣例相容的材質。 這種類型的材質適合在使用 Direct2D 的應用程式中使用，以及在使用 JavaScript 建立的 Windows 市集應用程式中使用。  
  
 本文件示範下列活動︰  
  
- 設定要由「影像內容管線」處理的來源影像。  
  
- 設定「影像內容管線」來產生可在 Direct2D 或 JavaScript 應用程式中使用的材質。  
  
    - 產生區塊壓縮 .dds 檔案。  
  
    - 產生預乘 Alpha。  
  
    - 停用 Mipmap 產生。  
  
## <a name="rendering-conventions-in-direct2d"></a>Direct2D 中的轉譯慣例  
 在 Direct2D 內容中使用的材質必須符合 Direct2D 內部轉譯慣例：  
  
- Direct2D 會使用預乘 Alpha 來實作透明度和半透明度。 與 Direct2D 搭配使用的材質即使不使用透明度或半透明度，也必須包含預乘 Alpha。 如需預乘 Alpha 的詳細資訊，請參閱[如何：匯出包含預乘 Alpha 的材質](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md)。  
  
- 提供材質時，必須使用下列其中一種區塊壓縮格式，以 .dds 格式提供：  
  
    - BC1_UNORM 壓縮  
  
    - BC2_UNORM 壓縮  
  
    - BC3_UNORM 壓縮  
  
- 不支援 Mipmap。  
  
#### <a name="to-create-a-texture-thats-compatible-with-direct2d-rendering-conventions"></a>建立與 Direct2D 轉譯慣例相容的材質  
  
1. 從基本材質著手。 載入現有的影像，或建立下列文章中所述的新影像：[如何：建立基本材質](../designers/how-to-create-a-basic-texture.md)。 若要支援以 .dds 格式支援區塊壓縮，請指定寬度和高度大小是 4 的倍數 (例如 100x100、128x128 或 256x192) 的材質。 由於不支援 Mipmap，因此材質不一定要是正方形，且大小不一定要是 2 的乘冪。  
  
2. 設定材質檔案，以便供「影像內容管線」處理。 在 [方案總管] 中，開啟您剛建立之材質檔案的捷徑功能表，然後選擇 [屬性]。 在 [組態屬性] > [一般] 頁面上，將 [項目類型] 屬性設定為 [影像內容管線]。 確定 [內容] 屬性是設定為 [是]，且 [從組建中排除] 是設定為 [否]，然後選擇 [套用] 按鈕。 此時會顯示 [影像內容管線] 組態屬性頁面。  
  
3. 將輸出格式設定為其中一種區塊壓縮格式。 在 [組態屬性] > [影像內容管線] > [一般] 頁面上，將 [壓縮] 屬性設定為 [BC3_UNORM 壓縮 (/compress:BC3_UNORM)]。 您可以依據您的需求，選擇任何其他 BC1、BC2 或 BC3 格式。 Direct2D 目前不支援 BC4、BC5、BC6 或 BC7 材質。 如需有關不同 BC 格式的詳細資訊，請參閱[區塊壓縮 (Direct3D 10) (英文)](https://msdn.microsoft.com/library/windows/desktop/bb694531.aspx)。  
  
   > [!NOTE]
   > 指定的壓縮格式會決定「影像內容管線」所產生之檔案的格式。 這與「影像編輯器」中來源影像的 [格式] 屬性不同，該屬性所決定的是儲存在磁碟上的來源影像檔案格式，亦即「工作格式」。 一般而言，您不會想要壓縮工作格式。  
  
4. 設定「影像內容管線」以產生使用預乘 Alpha 的輸出。 在 [組態屬性] > [影像內容管線] > [一般] 頁面上，將 [轉換成預乘 Alpha 格式] 屬性設定為 [是 (/generatepremultipliedalpha)]。  
  
5. 設定影像內容管線，使其不會產生 Mipmap。 在 [組態屬性] > [影像內容管線] > [一般] 頁面上，將 [產生 Mips] 屬性設定為 [否]。  
  
6. 選擇 [確定]  按鈕。  
  
   當您建置專案時，「影像內容管線」會將來源影像從工作格式轉換成您指定的輸出格式 (此轉換包括產生預乘 Alpha)，然後將結果複製到專案的輸出目錄。
