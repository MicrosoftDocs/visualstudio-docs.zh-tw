---
title: 旗標和解除標記執行緒 |Microsoft Docs
description: 瞭解如何在 Visual Studio 中將執行緒加上旗標或解除標記。 將執行緒、數個執行緒或所有線程加上旗標或解除標記。 只對您的程式碼或與模組相關聯的程式碼加上旗標。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9b7ce5db863987d530fe9e68d026a94474fc13c
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149491"
---
# <a name="how-to-flag-and-unflag-threads-c-visual-basic-c"></a>如何：將執行緒加上旗標和解除標記 (c #、Visual Basic、c + +) 

您可以使用 [ **執行緒**]、[ **平行堆疊** ] (執行緒視圖) 、 **[平行監看式]** 及 [ **GPU 執行緒** ] 視窗中的圖示，將您想要特別注意的執行緒加上旗標。 這個圖示可以協助您和其他人區分已加上旗標的執行緒和其他執行緒。

加上旗標的執行緒也會在 [**調試位置**] 工具列上的 [**執行緒**] 清單以及其他多執行緒的調試時間內收到特殊處理。 您可以在 **執行緒** 清單或其他視窗中顯示所有線程或僅顯示已加上旗標的執行緒。

### <a name="to-flag-or-unflag-a-thread"></a>若要將執行緒加上旗標或取消旗標

- 在 [ **執行緒** ] 或 [ **平行監看** 式] 視窗中，尋找您感興趣的執行緒，然後按一下旗標圖示來選取或清除旗標。
- 在 [**平行堆疊**] 視窗中，以滑鼠右鍵按一下執行緒或執行緒群組，然後選取 [**旗標 \<thread> /** ] 或 [取消 **標記/ \<thread>**]。

### <a name="to-unflag-all-threads"></a>若要取消所有執行緒的旗標

- 在 [執行緒] 視窗中，以滑鼠右鍵按一下任一執行緒，然後按一下 [將所有執行緒取消旗標]。
- 在 [ **平行監看** 式] 視窗中，選取所有標示的執行緒，然後以滑鼠右鍵按一下並選取 [取消 **標記**]。

### <a name="to-display-only-flagged-threads"></a>若只要顯示加上旗標的執行緒

- 選擇其中一個多執行緒偵錯工具視窗中的 [ **只顯示標示為執行緒** ] 按鈕。

### <a name="to-flag-just-my-code"></a>將 Just My Code 加上旗標

1. 在 [執行緒] 視窗頂端的工具列上，按一下旗標圖示。

2. 在下拉式清單中，按一下 [將 Just My Code 加上旗標]。

### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>將與選取的模組關聯的執行緒加上旗標

1. 在 [執行緒] 視窗的工具列上，按一下旗標圖示。

2. 在下拉式清單中，按一下 [將自訂模組選取範圍加上旗標]。

3. 在 [選取模組] 對話方塊中，選取您要的模組。

4. (選擇性) 在 [搜尋] 方塊中，鍵入用於搜尋特定模組的字串。

5. 按一下 [確定]。

## <a name="see-also"></a>另請參閱
- [Debug 多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [開始對多執行緒應用程式進行偵錯](../debugger/get-started-debugging-multithreaded-apps.md)
- [逐步解說：使用執行緒視窗來 Debug 多執行緒應用程式](../debugger/how-to-use-the-threads-window.md)