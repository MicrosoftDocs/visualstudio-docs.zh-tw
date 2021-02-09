---
title: 如何：建立和修改 MIP 層級
description: 瞭解如何使用影像編輯器來產生和修改紋理空間詳細資料層級的 MIP 層級。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f64d4369-2307-4175-a39a-2e45506f7fa1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: be95611d7d1c931e1b349e7a8c6dc0be75c7c832
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930976"
---
# <a name="how-to-create-and-modify-mip-levels"></a>如何：建立和修改 MIP 層級
本文件將示範如何使用「影像編輯器」來產生和修改材質空間「詳細層級」(LoD) 的「MIP 層級」。

## <a name="generating-mip-levels"></a>產生 MIP 層級
*Mipmapping* 是一項技術，可透過預先計算及儲存數個不同大小的材質複本，用來提升轉譯速度和降低材質物件上產生鋸齒化成品的情況。 每個複本 (稱為 MIP 層級) 的寬度和高度都是前一個複本的一半。 在物件表面上轉譯材質時，會自動選取與材質表面之螢幕空間區域最密切對應的 MIP 層級。 這意謂著圖形硬體不一定要篩選過大的材質以維持一致的視覺品質。 雖然儲存 MIP 層級的記憶體成本比只儲存原始材質高出 33%，但效能和影像品質上的提升為此做法提供了充分的理由。

#### <a name="to-generate-mip-levels"></a>產生 MIP 層級

1. 從基本材質開始，如 [如何：建立基本材質](../designers/how-to-create-a-basic-texture.md)中所述。 為了獲得最佳結果，請指定寬度和高度大小是 2 的乘冪 (例如 256、512、1024 等) 的材質。

2. 產生 MIP 層級。 在 [影像編輯器模式] 工具列上，選擇 [進階] > [工具] > [產生 Mips]。

     請注意，[移至下一個 MIP 層級] 和 [移至上一個 MIP 層級] 按鈕現在出現在 [影像編輯器模式] 工具列上。 如果顯示 [屬性] 視窗，請一併注意唯獨屬性 [MIP 層級] 和 [MIP 層級計數] 現在出現在影像屬性中。

## <a name="modifying-mip-levels"></a>修改 MIP 層級
若要達成特殊效果或提升特定詳細層級的影像品質，您可以個別修改每個 MIP 層級。 例如，您可以賦予材質物件一個從遠處看的不同外觀 (較大的距離與較小的 MIP 層級對應)，或是確保包含文字和符號的材質即使在較小的 MIP 層級也能維持清楚易讀。

#### <a name="to-modify-an-individual-mip-level"></a>修改個別的 MIP 層級

1. 選取您想要修改的 MIP 層級。 在 [影像編輯器模式] 工具列上，使用 [移至下一個 MIP 層級] 和 [移至上一個 MIP 層級] 按鈕在 MIP 層級之間移動。

2. 選取您想要修改的 MIP 層級之後，您可以使用繪圖工具來修改它，而不需變更其他 MIP 層級的內容。 「影像編輯器」工具列上會提供繪圖工具。 選取工具之後，您可以在 [屬性] 視窗中變更其屬性。 如需有關繪圖工具及其屬性的資訊，請參閱[影像編輯器](../designers/image-editor.md)。

> [!NOTE]
> 如果您不需要修改個別 MIP 層級的內容 (就像您想要達成特定效果時可能會做的)，建議您在建置階段從來源材質產生 Mipmap。 這有助於確保 MIP 層級與來源材質保持同步，因為對某個 MIP 層級的修改並不會自動傳播至其他層級。 如需有關如何在組建階段產生 mipmap 的詳細資訊，請參閱 [如何：匯出包含 mipmap 的材質](../designers/how-to-export-a-texture-that-contains-mipmaps.md)。

## <a name="see-also"></a>另請參閱

- [如何：建立基本材質](../designers/how-to-create-a-basic-texture.md)
