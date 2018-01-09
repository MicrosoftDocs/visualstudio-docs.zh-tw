---
title: "繪製圖形與路徑 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c51f7217942f755eee45c4901cf0f8eecdbac605
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="draw-shapes-and-paths"></a>繪製圖案與路徑
在 XAML 設計工具中，「圖形」(Shape) 正如您所預期。 例如：矩形、圓形或橢圓形。 *「路徑」* (path) 是圖形的更靈活版本。 您可以執行像是調整形狀，或將圖形合併在一起形成新的圖形等動作。  
  
 圖形與路徑都會使用向量圖形，因此可以適切地調整為高解析度顯示。 如果您想要深入了解向量圖形，請參閱 [What are Vector Graphics](https://www.youtube.com/watch?v=MoCSwF0n-io) 或 [vector graphics](http://www.webopedia.com/TERM/V/vector_graphics.html)。  
  
 **本主題內容：**  
  
-   [繪製圖形](#Shape)  
  
-   [繪製路徑](#Path)  
  
-   [將圖形轉換成路徑](#Convert)  
  
-   [合併路徑](#Combine)  
  
-   [建立複合路徑](#Compound)  
  
-   [建立裁剪路徑](#Clipping)  
  
##  <a name="Shape"></a> 繪製圖形  
 您可以在 [資產]  面板中找到許多圖形。  
  
 ![[資產] 面板上的 [圖形] 分類](../designers/media/b4_shapes_assetspanel.png "b4_Shapes_AssetsPanel")  
  
 將您想要的任何圖形拖曳至畫板。 然後，您可以使用圖形控點來調整、旋轉、移動或扭曲圖形。  
  
 ![](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png "84261e83-3091-4490-ab58-4218b188439e")  
  
##  <a name="Path"></a> 繪製路徑  
 路徑是一系列連接的直線和曲線。 使用路徑可建立 [資產]  面板中所沒有的有趣圖形。  
  
 您可以使用線條、畫筆或鉛筆來繪製路徑。 您可以在 [工具]  面板中找到這些工具。  
  
 ![](../designers/media/717956a8-b6a5-4e37-8af3-70bcfc78c82a.png "717956a8-b6a5-4e37-8af3-70bcfc78c82a") ![](../designers/media/8fbbbb21-be83-4cf6-903b-3a49f00c9860.png "8fbbbb21-be83-4cf6-903b-3a49f00c9860")  
  
### <a name="draw-a-straight-line"></a>繪製直線  
 使用**畫筆**工具 ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54")，或**線條**工具 ![](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "eb618397-5283-48be-8396-3449be7b6fbf")。  
  
 **使用畫筆工具** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54")  
  
 在畫板上，按一次可定義起始點，然後再按一次可定義線條的結尾。  
  
 **使用線條工具** ![](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "eb618397-5283-48be-8396-3449be7b6fbf")  
  
 在畫板上，從想要讓線條開始的地方拖曳起，然後再於想要線條結束的點上放開。  
  
### <a name="draw-a-curve"></a>繪製曲線  
 使用**畫筆**工具 ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54")。  
  
 在畫板上，按一次可定義線條的起始點，然後按一下並拖曳指標可建立所需的曲線。  
  
 如果您想要關閉路徑，請按一下線條的第一個點。  
  
### <a name="change-the-shape-of-a-curve"></a>變更曲線的形狀  
 使用**直接選取**工具 ![](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f-c116-451d-8dd2-1f88b8406362")。  
  
 按一下圖形，然後拖曳圖形上的任一點可變更曲線圖形。  
  
### <a name="draw-a-free-form-path"></a>繪製任意形狀的路徑  
 使用**鉛筆**工具 ![](../designers/media/509dc167-734f-46c9-b012-987ee63450cd.png "509dc167-734f-46c9-b012-987ee63450cd")。  
  
 在畫板上，繪製任意形狀的路徑，就像使用真正的鉛筆一樣。  
  
### <a name="remove-part-of-a-path"></a>移除路徑的一部分  
 使用**直接選取**工具 ![](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f-c116-451d-8dd2-1f88b8406362")。  
  
 選取包含所要刪除線段的路徑，然後按一下 [刪除]  按鈕。  
  
### <a name="remove-a-point-in-a-path"></a>移除路徑中的點  
 使用**選取**工具 ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa")，以及**畫筆**工具 ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54")。  
  
 使用**選取**工具 ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa") 選取路徑。 然後，使用**畫筆**工具 ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") 按一下您想要移除的點。  
  
### <a name="add-a-point-to-a-path"></a>將點加入至路徑  
 使用**選取**工具 ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa")，以及**畫筆**工具 ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54")。  
  
 使用**選取**工具 ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa") 選取路徑。 使用**畫筆**工具 ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") 按一下想要新增點之路徑的任何位置。  
  
##  <a name="Convert"></a> 將圖形轉換成路徑  
 若要以修改路徑的相同方式來修改圖形，請將圖形轉換為路徑。  
  
 **觀看短片︰**![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Working with paths: Convert a shape to a path](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147) (使用路徑：將圖形轉換成路徑)。  
  
##  <a name="Combine"></a> 合併路徑  
 您可以將路徑與圖形合併為單一路徑。  
  
 ![](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png "2df17a5d-a338-4ef4-96c5-dae51cc1ca8a")  
  
|||||  
|-|-|-|-|  
|![](../designers/media/b1_1.png "B1_1")|合併前的兩個圖形|![](../designers/media/b1_4.png "B1_4")|交集|  
|![](../designers/media/b1_2.png "B1_2")|聯集|![](../designers/media/b1_5.png "B1_5")|排除重疊|  
|![](../designers/media/b1_3.png "B1_3")|分割|![](../designers/media/b1_6.png "B1_6")|差集|  
  
 **觀看短片︰**![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Working with paths: Combine paths](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195) (使用路徑：合併路徑)。  
  
##  <a name="Compound"></a> 建立複合路徑  
 當您建立複合路徑時，這些路徑的任何交集部分都會從結果中減去，而所產生的路徑會採用最底層路徑的視覺屬性。  
  
 您可以在建立複合路徑之後隨時打散這些路徑。  
  
 ![](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png "2157a8aa-d9a7-4de4-8de5-b10d28f08a84")  
  
 **觀看短片︰**![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Working with paths: Create a compound path](https://www.youtube.com/watch?v=Io5bC0-nH6Q) (使用路徑：建立複合路徑)。  
  
##  <a name="Clipping"></a> 建立裁剪路徑  
 裁剪路徑是套用至其他物件的路徑或圖形，隱藏了所遮蔽物件落於裁剪路徑外面的部分。  
  
 ![](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png "22471e98-a841-4f39-a3ef-36090cf5a625")  
  
 **觀看短片︰**![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Working with paths: Create a clipping path](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232) (使用路徑：建立裁剪路徑)。  
  
## <a name="see-also"></a>請參閱  
 [使用 Blend for Visual Studio 建立 UI](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)