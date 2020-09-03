---
title: 如何：將執行緒加上旗標和解除標記 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: b6d6a49dd9b90172686a90d92e6b630dd70b5cf0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189431"
---
# <a name="how-to-flag-and-unflag-threads"></a>如何：將執行緒加上旗標和取消旗標
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 [ **執行緒**]、[ **平行堆疊**]、[ **平行監看式]** 及 [ **GPU 執行緒** ] 視窗中的圖示，將您想要特別注意的執行緒加上旗標。 這個圖示可以協助您和其他人區分已加上旗標的執行緒和其他執行緒。  
  
 標記的執行緒也會在 [**調試位置**] 工具列上的 [**執行緒**] 清單中收到特殊處理。 這份清單可以顯示所有執行緒，也可以僅顯示已加上旗標的執行緒。 當您為執行緒加上旗標時， **執行緒** 清單會自動切換成隻顯示已加上旗標的執行緒，但您可以將它切換回以顯示所有線程。  
  
### <a name="to-flag-or-unflag-a-thread-by-using-the-threads-window"></a>使用執行緒視窗將執行緒加上旗標或取消旗標  
  
- 在 [ **執行緒** ] 視窗中，尋找您感興趣的執行緒，然後按一下旗標圖示來選取或清除旗標。  
  
### <a name="to-unflag-all-threads"></a>若要取消所有執行緒的旗標  
  
- 在 [執行緒]**** 視窗中，以滑鼠右鍵按一下任一執行緒，然後按一下 [將所有執行緒取消旗標]****。  
  
### <a name="to-display-only-flagged-threads"></a>若只要顯示加上旗標的執行緒  
  
- 在偵錯視窗中選擇旗標按鈕。  
  
### <a name="to-flag-just-my-code"></a>將 Just My Code 加上旗標  
  
1. 在 [執行緒]**** 視窗頂端的工具列上，按一下旗標圖示。  
  
2. 在下拉式清單中，按一下 [將 Just My Code 加上旗標]****。  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>將與選取的模組關聯的執行緒加上旗標  
  
1. 在 [執行緒]**** 視窗的工具列上，按一下旗標圖示。  
  
2. 在下拉式清單中，按一下 [將自訂模組選取範圍加上旗標]****。  
  
3. 在 [選取模組]**** 對話方塊中，選取您要的模組。  
  
4. (選擇性) 在 [搜尋]**** 方塊中，鍵入用於搜尋特定模組的字串。  
  
5. 按一下 [確定]  。  
  
## <a name="see-also"></a>另請參閱  
 [Debug 多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [逐步解說：偵錯多執行緒應用程式](../debugger/walkthrough-debugging-a-multithreaded-application.md)
