---
title: 如何： 將執行緒加上旗標和取消 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09d26c87867e071b7dafce80d95e4bc46cb88bb8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891371"
---
# <a name="how-to-flag-and-unflag-threads"></a>如何：將執行緒加上旗標和取消旗標
您可以加上旗標的執行緒，您想要特別注意的標記中的圖示**執行緒**，**平行堆疊**（執行緒檢視），**平行監看式**，和**GPU 執行緒**windows。 這個圖示可以協助您和其他人區分已加上旗標的執行緒和其他執行緒。  
  
已標幟的執行緒也會收到中的特殊待遇**執行緒**清單**偵錯位置**工具列和其他多執行緒偵錯視窗中。 您可以顯示所有執行緒，也只有已標幟的執行緒中**執行緒**清單或在其他視窗。
  
### <a name="to-flag-or-unflag-a-thread"></a>若要將執行緒加上旗標或取消旗標 
  
- 在 [**執行緒**或是**平行監看式**] 視窗中，尋找您感興趣的執行緒，並按一下旗標圖示，以選取或清除旗標。 
- 在 [**平行堆疊**] 視窗中，以滑鼠右鍵按一下執行緒或執行緒與選取的群組**旗標 / <thread>** 或是**取消旗標 / <thread>** 。
  
### <a name="to-unflag-all-threads"></a>若要取消所有執行緒的旗標  
  
-   在 [**執行緒**] 視窗中，以滑鼠右鍵按一下任何執行緒，然後按一下**取消旗標的所有執行緒**。
-   在 **平行監看式**所有已標幟的執行緒視窗中，選取，然後以滑鼠右鍵按一下並選取**取消旗標**。  
  
### <a name="to-display-only-flagged-threads"></a>若只要顯示加上旗標的執行緒  
  
-   選擇**僅顯示已標幟執行緒**其中一個多執行緒偵錯視窗中的按鈕。  
  
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
 [開始偵錯多執行緒應用程式](../debugger/get-started-debugging-multithreaded-apps.md)  
 [逐步解說： 偵錯多執行緒應用程式，使用 [執行緒] 視窗](../debugger/how-to-use-the-threads-window.md)