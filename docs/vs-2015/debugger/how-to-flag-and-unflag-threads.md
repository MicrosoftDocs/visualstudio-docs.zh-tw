---
title: 如何： 將執行緒加上旗標和取消 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5816007476da56321e58182e636b54a5a5697994
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817486"
---
# <a name="how-to-flag-and-unflag-threads"></a>如何：將執行緒加上旗標和取消旗標
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以加上旗標的執行緒，您想要特別注意的標記中的圖示**執行緒**，**平行堆疊**，**平行監看式**，和**GPU執行緒**windows。 這個圖示可以協助您和其他人區分已加上旗標的執行緒和其他執行緒。  
  
 已標幟的執行緒也會收到中的特殊待遇**執行緒**上列出**偵錯位置**工具列。 這份清單可以顯示所有執行緒，也可以僅顯示已加上旗標的執行緒。 當執行緒，加上旗標**執行緒**清單會自動切換成只顯示已標幟的執行緒，但您也可以將它切換回到顯示所有執行緒，視需要。  
  
### <a name="to-flag-or-unflag-a-thread-by-using-the-threads-window"></a>使用執行緒視窗將執行緒加上旗標或取消旗標  
  
-   在 [**執行緒**] 視窗中，尋找您感興趣的執行緒，並按一下旗標圖示，以選取或清除旗標。  
  
### <a name="to-unflag-all-threads"></a>若要取消所有執行緒的旗標  
  
-   在 [**執行緒**] 視窗中，以滑鼠右鍵按一下任何執行緒，然後按一下**取消旗標的所有執行緒**。  
  
### <a name="to-display-only-flagged-threads"></a>若只要顯示加上旗標的執行緒  
  
-   在偵錯視窗中選擇旗標按鈕。  
  
### <a name="to-flag-just-my-code"></a>將 Just My Code 加上旗標  
  
1.  在頂端工具列上**執行緒** 視窗中，按一下旗標圖示。  
  
2.  在下拉式清單中，按一下**旗標 Just My Code**。  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>將與選取的模組關聯的執行緒加上旗標  
  
1.  工具列上的**執行緒** 視窗中，按一下旗標圖示。  
  
2.  在下拉式清單中，按一下**旗標自訂模組選取範圍**。  
  
3.  在 **選取模組**對話方塊方塊中，選取您想要的模組。  
  
4.  （選擇性）在 **搜尋**方塊中，輸入要搜尋的特定模組的字串。  
  
5.  按一下 [確定 **Deploying Office Solutions**]。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [逐步解說：偵錯多執行緒應用程式](../debugger/walkthrough-debugging-a-multithreaded-application.md)



