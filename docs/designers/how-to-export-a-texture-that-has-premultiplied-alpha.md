---
title: 如何：匯出包含預乘 Alpha 的材質
description: 瞭解影像內容管線如何從可能更容易使用且更健全的來源影像產生預乘 Alpha 紋理。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 05348afa-f079-4f53-a05b-ecd91d13adab
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 56e8d198e55b521b761f8f3a7b54f6c2c0ee2c33
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930926"
---
# <a name="how-to-export-a-texture-that-has-premultiplied-alpha"></a>如何：匯出包含預乘 Alpha 的材質

影像內容管線可以從來源影像產生預乘 Alpha 的材質。 這些使用起來可以更簡單，且比起不包含預乘 Alpha 的材質更穩固。

本文件示範下列活動︰

- 設定要由「影像內容管線」處理的來源影像。

- 設定影像內容管線以產生預乘 Alpha。

## <a name="premultiplied-alpha"></a>預乘 Alpha
預乘 Alpha 提供了許多優於傳統非預乘 Alpha 的優點，因為它更能代表實體物質與真實世界光線的互動，方法是將材質的色彩比重 (它新增至場景的色彩) 與半透明性 (它允許透出來的基礎色彩量) 分開。 使用預乘 Alpha 的一些優點包括︰

- 使用預乘 Alpha 透明混色是關聯的作業。混用多種半透明材質的結果是相同的，而不論材質的混合順序。

- 由於使用預乘 Alpha 透明混色的關聯本質，半透明物件的多階段呈現便簡化了。

- 藉由使用預乘 Alpha，純粹加色法透明混色 (將 Alpha 設定為零) 和線性插補透明混色可以同時達成。 比方說，在粒子系統中，加色法透明混色的火粒子可能會變成使用線性插補透明混色的半透明煙霧粒子。 若沒有預乘 Alpha，您將必須分別繪製火粒子與煙霧粒子，並修改繪製呼叫之間的呈現狀態。

- 使用預乘 Alpha 的材質壓縮品質會比不使用的材質高，而且它們不會表現出變色的邊緣，或稱「光環效果」(當您將不使用預乘 Alpha 的材質透明混色時可能會產生此結果)。

#### <a name="to-create-a-texture-that-uses-premultiplied-alpha"></a>建立使用預乘 Alpha 的材質

1. 從基本材質著手。 載入現有的影像檔案，或依照 [如何：建立基本材質](../designers/how-to-create-a-basic-texture.md)中所述，建立一個影像檔案。

2. 設定材質檔案，以便供「影像內容管線」處理。 在方案總管中，開啟材質檔案的捷徑功能表，然後選擇 [屬性]。 在 [設定 **屬性**] 的  >  **[一般**] 頁面上，將 [**專案類型**] 屬性設定為 [**影像內容管線**]。 確定 [內容] 屬性是設定為 [是]，且 [從組建中排除] 是設定為 [否]，然後選擇 [套用] 按鈕。 此時會顯示 [影像內容管線] 組態屬性頁面。

3. 設定影像內容管線以產生預乘 Alpha。 在 [設定 **屬性**  >  **影像內容管線**  >  **一般**] 頁面上，將 [**轉換成前置字母格式**] 屬性設定為 **[是] (/generatepremultipliedAlpha)**。

4. 選擇 [確定]  按鈕。

   當您建置專案時，「影像內容管線」會將來源影像從工作格式轉換成您指定的輸出格式 (這包括將影像轉換成預乘 Alpha 格式)，然後將結果複製到專案的輸出目錄。