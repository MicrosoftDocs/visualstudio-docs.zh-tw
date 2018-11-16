---
title: 如何：從檢測排除或包含精簡函式 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd17b5c383736f2c11977e117ee59a1a6fa9e571
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742537"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>如何：從檢測排除或包含 Short 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

根據預設，程式碼剖析工具會從檢測排除*小型函式*。 小型函式是不會進行任何函式呼叫的精簡函式。 排除這些小型函式可減少檢測負荷，並能因此改善檢測速度。 排除小型函式也能減少效能程式碼剖析資料檔 (.vsp) 大小和分析所需的時間。 如果已排除小型函式，小型函式所花費的時間會算在其父函式的專有和內含時間。 小型函式可以排除或包含在檢測中，如下列程序所述。  
  
### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>從檢測排除或包含精簡函式  
  
1.  在 [效能總管] 中，選取 [效能工作階段]，然後以滑鼠右鍵按一下並選取 [屬性]。  
  
     [屬性頁] 對話方塊隨即出現。  
  
2.  在 [屬性頁] 中，按一下 [檢測] 屬性。  
  
3.  若要從檢測排除精簡函式，請選取 [從檢測排除精簡函式]。 這是預設設定。  
  
     -或-  
  
     若要在檢測中包含精簡函式，請清除 [從檢測排除精簡函式]。  
  
4.  按一下 [確定 **Deploying Office Solutions**]。  
  
## <a name="see-also"></a>另請參閱  
 [控制資料收集](../profiling/controlling-data-collection.md)   
 [效能工作階段屬性](../profiling/performance-session-properties.md)



