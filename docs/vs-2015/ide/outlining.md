---
title: 大綱 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
ms.assetid: d1476758-9d35-4d74-b63c-310661932ecd
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 82b0339bde0ffbfff77165f1626ec83767d45211
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54767575"
---
# <a name="outlining"></a>大綱
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以選擇隱藏部分程式碼不進行檢視，方法是摺疊程式碼區域，使其出現在加號 (+) 下方。 您可以按一下加號來展開已摺疊的區域 (或者，您可以按 CTRL+M+M 摺疊區域，然後按 CTRL+M+M 再次展開區域)。您也可以摺疊大綱區域，方法是按兩下大綱邊界之區域中的任一行，而大綱邊界出現在程式碼左邊。 當您將滑鼠停留在已摺疊的區域上方時，已摺疊區域的內容會成為工具提示。  
  
 當您將滑鼠停留在邊界上方時，也會反白顯示大綱邊界中的區域。 在某些色彩組態中，預設反白顯示色彩似乎太過模糊。 您可以在 [工具]/[選項]/[環境]/[字型和色彩]/[可摺疊區域] 中進行變更。  
  
 當您使用大綱程式碼時，可以展開您想要處理的區段，並在完成時予以摺疊，然後移至其他區段。 當您不想要顯示大綱時，可以使用 [取消大綱] 命令以移除大綱資訊，而不干擾基礎程式碼。  
  
 [編輯] 功能表上的 [復原] 和 [重做] 命令會影響這些動作。 [複製]、[剪下]、[貼上] 和拖放作業都會保留大綱資訊，而不是可摺疊區域的狀態。 例如，當您複製已摺疊的區域時，[貼上] 作業會將複製的文字貼為已展開的區域。  
  
> [!CAUTION]
>  當您變更大綱區域時，可能會遺失大綱。 例如，刪除或 [尋找] 和 [取代] 作業可能會清除區域的結尾。  
  
 [編輯/大綱] 子功能表上可以找到下列命令。  
  
|||  
|-|-|  
|隱藏選取範圍|(CTRL+M、CTRL+H) - 摺疊選取的程式碼區塊，其通常無法可供製作大綱，例如 `if` 區塊。 若要移除自訂區域，請使用 [取消隱藏目前大綱] (或 CTRL+M、CTRL+U)。 在 Visual Basic 中無法使用。|  
|切換大綱展開|- 在游標落在巢狀摺疊區段時，反轉最內層大綱區段的目前隱藏或展開狀態。|  
|切換所有大綱|(CTRL+M、CTRL+L) - 將所有區域設定為相同摺疊或展開狀態。 如果有些區域展開，有些區域摺疊，則會展開摺疊區域。|  
|取消大綱|(CTRL+M、CTRL+P) - 移除整份文件的所有大綱資訊。|  
|取消隱藏目前的|(CTRL+M、CTRL+U) - 移除目前所選取使用者定義區域的大綱資訊。 在 Visual Basic 中無法使用。|  
|摺疊至定義|(CTRL+M、CTRL+O) - 摺疊所有類型的成員。|  
|摺疊區塊︰\<邏輯界限>|(Visual C++) 摺疊包含插入點之函式中的區域。 例如，如果插入點落在迴圈內，則會隱藏迴圈。|  
|\<邏輯結構> 中的全部摺疊|(Visual C++) 摺疊函式內的所有結構。|  
  
 您也可以使用 Visual Studio SDK 來定義您想要展開或摺疊的文字區域。 請參閱[逐步解說：大綱](../extensibility/walkthrough-outlining.md)。
