---
title: 逐步解說： 擷取圖形資訊 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de553729d37bb82d1b30c6a142f7e65c983bb1c1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486695"
---
# <a name="walkthrough-capturing-graphics-information"></a>逐步解說：擷取圖形資訊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[逐步解說： 擷取圖形資訊](https://docs.microsoft.com/visualstudio/debugger/graphics/walkthrough-capturing-graphics-information)。  
  
本逐步解說示範如何使用[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]圖形診斷來手動擷取圖形資訊從 Direct3D 應用程式。  
  
 本逐步解說將說明下列工作：  
  
-   將圖形診斷連結至您的應用程式  
  
-   擷取圖形資訊  
  
## <a name="capturing-graphics-information"></a>擷取圖形資訊  
 若要使用圖形診斷工具，您需要先擷取它所依賴的圖形資訊。 若要啟用擷取，請在應用程式啟動時，使用 [開始診斷]  命令將圖形診斷連結至您的應用程式。  
  
#### <a name="to-enable-the-capture-of-graphics-information-after-a-project-or-solution-is-loaded"></a>允許在載入專案或方案後擷取圖形資訊  
  
1.  在  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，載入您想要從中擷取圖形資訊之應用程式專案或方案檔。  
  
2.  在 [圖形診斷] 工具列上，選擇 [開始診斷] 。  
  
#### <a name="to-enable-the-capture-of-graphics-information-without-loading-a-project-or-solution"></a>允許在不載入專案或方案的情況下擷取圖形資訊  
  
1.  在功能表列上，依序選擇 [檔案] 、[開啟舊檔] 及 [專案/方案] 。 [開啟專案]  對話方塊隨即出現。  
  
2.  指定您要從中擷取圖形資訊之應用程式的可執行檔 (而不是專案或方案檔)，然後選擇 [開啟] 。  
  
3.  在功能表列上，選擇 [ **偵錯**]、[ **圖形**]、[ **開始診斷**]。  
  
 在您啟動應用程式且應用程式正在轉譯畫面格之後，您可以擷取圖形資訊。  
  
#### <a name="to-capture-graphics-information"></a>擷取圖形資訊  
  
-   在 [圖形診斷] 工具列上，選擇 [擷取]  按鈕。 ![圖形擷取按鈕圖示](../debugger/media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")  
  
     -或-  
  
     當應用程式進入焦點時，按 **Print Screen**鍵。  
  
 每次您擷取畫面格的相關資訊，圖形診斷就會記錄 Direct3D 事件及相關聯的狀態，並將該資料加入圖形記錄檔中。 每一個圖形診斷工作階段都會建立新的圖形記錄檔。 如圖形記錄檔的相關資訊，請參閱 <<c0> [ 概觀](../debugger/overview-of-visual-studio-graphics-diagnostics.md)。  
  
## <a name="next-steps"></a>後續步驟  
 本逐步解說示範如何手動擷取圖形資訊。 下一步是考慮此選項：  
  
-   了解如何使用圖形診斷工具分析擷取到的圖形資訊。 請參閱[概觀](../debugger/overview-of-visual-studio-graphics-diagnostics.md)。  
  
## <a name="see-also"></a>另請參閱  
 [擷取圖形資訊](../debugger/capturing-graphics-information.md)



