---
title: 圖形狀態 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics.statewindow
ms.assetid: 97e7757e-c372-4626-8149-99a81367a0e1
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f422c60d568834c585b0ea9a74332b838ee556c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49307614"
---
# <a name="graphics-state"></a>圖形狀態
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 圖形診斷中的 [狀態] 視窗可協助您了解在目前事件時作用的圖形狀態 (例如繪製呼叫)。  
  
## <a name="understanding-the-state-window"></a>了解狀態視窗  
 [狀態] 視窗會在一個位置中收集可影響轉譯並以階層方式呈現的狀態。 根據您應用程式所使用的 Direct3D 版本，[狀態] 視窗中呈現的資訊可能會有所差異。  
  
### <a name="state-views"></a>狀態檢視  
 您可以使用數種不同的方式來檢視狀態資料表：  
  
|檢視|描述|  
|----------|-----------------|  
|API 輸入狀態檢視|此檢視會以構成狀態之 Direct3D 物件的類似版面配置來顯示狀態。|  
|邏輯輸入狀態檢視|此檢視會以邏輯檢視來顯示狀態，而邏輯檢視不會鏡像構成狀態之 Direct3D 物件的版面配置。|  
|釘選的狀態檢視|釘選的狀態檢視會以具有完整名稱的一般清單來呈現釘選的狀態項目，而不是階層。 此檢視可以利用少數幾行來檢視不同狀態組合的許多狀態項目。|  
  
##### <a name="to-change-the-state-view"></a>變更狀態檢視  
  
-   在 [狀態] 視窗左上方的標題列正下方，選擇對應至您要使用之狀態檢視樣式的按鈕。  
  
    -   **顯示 API 輸入的狀態檢視**  
  
    -   **顯示邏輯狀態檢視**  
  
    -   **顯示釘選狀態檢視**  
  
> [!IMPORTANT]
>  您必須將狀態中的釘選**顯示 API 輸入狀態**或是**顯示邏輯狀態**才會顯示在檢視**顯示釘選狀態檢視**。  
  
### <a name="state-table-format"></a>狀態資料表格式  
 [狀態] 視窗會呈現數個資料行的資訊。  
  
|資料行|描述|  
|------------|-----------------|  
|名稱|狀態項目的名稱。 如果此項目代表狀態的組合，則可以展開項目予以顯示。<br /><br /> 在  **API 輸入狀態檢視**並**邏輯狀態檢視**狀態，以顯示狀態之間的階層式關聯性會縮排名稱。<br /><br /> 在 **釘選狀態檢視**狀態時，完整名稱會顯示在一般清單。|  
|值|狀態項目的值。|  
|類型|狀態項目的類型。|  
  
### <a name="changed-state"></a>已變更狀態  
 圖形狀態通常會在後續繪製呼叫之間進行遞增變更，而且不正確地變更狀態時，會導致許多種類的轉譯問題。 為了協助您找出自前一個繪製呼叫之後變更的狀態，已變更的狀態會標上星號並以紅色顯示；這不只適用於狀態本身，也適用於其父狀態項目，因此，您可以輕鬆地找出最高層級的已變更狀態，然後向下鑽研到詳細資料。  
  
### <a name="pinning-state"></a>釘選中狀態  
 因為許多應用程式都循序轉譯類似的物件 (變更一組已知的狀態)，所以有時適用於在原地釘選變更中狀態，以查看它在不同繪製呼叫之間移動時如何變更。  
  
 如果您已經因特定狀態變更而找出問題來源，則這也十分有用。  
  
##### <a name="to-pin-state-in-place"></a>就地釘選狀態  
  
1.  在 [狀態] 視窗中，找出您感興趣的狀態。 您可能需要展開高階狀態，以找出您感興趣的詳細資料。  
  
2.  將游標放在您感興趣的狀態上方。 [釘選] 圖示會出現在狀態項目左側。  
  
3.  選擇 [釘選] 圖示就地釘選狀態項目。



