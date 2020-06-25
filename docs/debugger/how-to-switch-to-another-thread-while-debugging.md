---
title: 在偵錯時切換到另一個執行緒
ms.custom: seodec18
ms.date: 04/27/2017
ms.topic: how-to
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
ms.openlocfilehash: 9306e68c7d8906c6956eb5e3810327898bc56567
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348908"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>如何：在 Visual Studio 中進行調試時切換至另一個執行緒（c #、Visual Basic、c + +）
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

## <a name="see-also"></a>另請參閱
- [偵錯多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)
