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
ms.openlocfilehash: 11ad6280ad1213008bbb8ca8f6311ca34231d308
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732435"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>如何：在 Visual Studio 中進行調試時切換至另一個C#執行緒（， C++Visual Basic，）
當您進行多執行緒應用程式的調試時，您可以使用數種方法中的任何一種，從您已使用的執行緒切換至另一個執行緒。

> [!NOTE]
> 如果您想要控制執行緒執行的順序，您必須[凍結和解除凍結執行緒](../debugger/get-started-debugging-multithreaded-apps.md)。

當您檢查程式碼編輯器和不同多執行緒偵錯工具視窗中的執行緒時，黃色箭號表示目前的執行緒。 具有大尾的綠色箭號表示非目前的執行緒具有目前的偵錯工具內容。

### <a name="to-switch-to-any-thread-that-appears"></a>切換至任何出現的執行緒

- 在 [**執行緒**] 或 [**平行監看**式] 視窗中，按兩下執行緒。

### <a name="to-switch-to-a-thread-in-a-source-window"></a>若要切換至來源視窗中的執行緒

- 在左側裝訂邊中，以滑鼠右鍵按一下執行緒標記圖示 [![執行緒標記](../debugger/media/dbg-thread-marker.png "ThreadMarker")]，指向 [**切換至**]，然後按一下您要切換的執行緒名稱。 捷徑功能表只會顯示該特定位置上的執行緒。

     如果沒有出現任何執行緒標記，請在 [**執行緒**] 視窗中按一下滑鼠右鍵，並確認已選取 [**在來源中顯示執行緒**]。

### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>若要切換至偵錯位置工具列中的執行緒

1. 在 [**調試位置**] 工具列上，按一下 [**執行緒**] 清單。

2. 在清單中，按一下您要切換至哪個執行緒。

## <a name="see-also"></a>請參閱
- [對多執行緒應用程式進行偵錯](../debugger/debug-multithreaded-applications-in-visual-studio.md)
