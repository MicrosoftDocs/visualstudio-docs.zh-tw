---
title: 如何： 偵錯時切換至另一個執行緒 |Microsoft 文件
ms.custom: ''
ms.date: 04/27/2017
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e7e5e3b127dd397a32b54915f95827ebe5649f5f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31475676"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio"></a>如何： 在 Visual Studio 中偵錯時切換至另一個執行緒
當您偵錯多執行緒應用程式時，您可以使用數種方法的任何一個可從您已使用的其他執行緒的執行緒切換。

> [!NOTE]
> 如果您想要控制執行執行緒的順序，您需要[凍結和解除凍結執行緒](../debugger/get-started-debugging-multithreaded-apps.md)。

當您檢查程式碼編輯器和不同的多執行緒偵錯視窗中的執行緒時，黃色箭號表示目前的執行緒。 尾端彎曲的綠色箭號表示非目前執行緒的目前偵錯工具內容。
  
### <a name="to-switch-to-any-thread-that-appears"></a>若要切換至出現的任何執行緒 
  
-   在**執行緒**或**平行監看式**視窗中，按兩下執行緒。  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>若要切換至來源視窗中的執行緒  
  
-   在左側裝訂邊上，以滑鼠右鍵按一下執行緒標記圖示![執行緒標記](../debugger/media/dbg-thread-marker.png "ThreadMarker")，指向 **切換至**，然後按一下您要切換該執行緒的名稱. 捷徑功能表只會顯示該特定位置上的執行緒。  
  
     如果沒有執行緒標記顯示，以滑鼠右鍵按一下**執行緒**視窗，並確認**在來源中顯示執行緒**已選取。  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>若要切換至偵錯位置工具列中的執行緒  
  
1.  在**偵錯位置**工具列上，按一下 **執行緒**清單。  
  
2.  在清單中，按一下您要切換至哪個執行緒。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)
