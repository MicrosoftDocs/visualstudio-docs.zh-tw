---
title: 在偵錯時切換到另一個執行緒
ms.custom: seodec18
ms.date: 04/27/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 163d14de4880ed1c5e2ae6a3170ec5ae1ae47485
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005185"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>HOW TO：在 Visual Studio 中偵錯時切換到另一個執行緒 (C#，Visual Basic、 c + +)
當您偵錯多執行緒應用程式時，您可以使用其中幾種方法，從您已使用另一個執行緒的執行緒切換。

> [!NOTE]
> 如果您想要控制執行緒執行所在的順序，您需要[凍結和解除凍結執行緒](../debugger/get-started-debugging-multithreaded-apps.md)。

當您檢查程式碼編輯器和不同的多執行緒偵錯視窗中的執行緒時，黃色箭號表示目前的執行緒。 具有尾端彎曲的綠色箭號表示非目前執行緒具有目前的偵錯工具內容。
  
### <a name="to-switch-to-any-thread-that-appears"></a>若要切換至出現的任何執行緒 
  
-   在 [**執行緒**或是**平行監看式**] 視窗中，按兩下執行緒。  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>若要切換至來源視窗中的執行緒  
  
-   在左側的裝訂邊上，以滑鼠右鍵按一下執行緒標記圖示![執行緒標記](../debugger/media/dbg-thread-marker.png "ThreadMarker")，指向**切換至**，然後按一下您要切換該執行緒的名稱. 捷徑功能表只會顯示該特定位置上的執行緒。  
  
     如果不出現任何執行緒標記，以滑鼠右鍵按一下**執行緒** 視窗，並確認**在來源中顯示執行緒**已選取。  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>若要切換至偵錯位置工具列中的執行緒  
  
1.  在 **偵錯位置**工具列上，按一下**執行緒**清單。  
  
2.  在清單中，按一下您要切換至哪個執行緒。  
  
## <a name="see-also"></a>請參閱  
 [對多執行緒應用程式進行偵錯](../debugger/debug-multithreaded-applications-in-visual-studio.md)
