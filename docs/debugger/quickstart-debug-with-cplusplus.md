---
title: 偵錯 C++
description: 使用 Visual Studio 偵錯工具來偵錯機器碼
ms.custom: mvc
ms.date: 08/06/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: 639e430b-6d2d-46bd-b738-8c60dfb384f1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 8735ecd409eca2801b42b11bd3928a00e5191bf8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840895"
---
# <a name="quickstart-debug-with-c-using-the-visual-studio-debugger"></a>快速入門：使用 Visual Studio 偵錯工具來偵錯 C++

Visual Studio 偵錯工具提供許多強大的功能，可協助您偵錯應用程式。 本主題提供了解一些基本功能的快速方法。

## <a name="create-a-new-project"></a>建立新專案

1. 開啟 Visual Studio 並建立專案。

    ::: moniker range=">=vs-2019"
    按 **Esc** 關閉開始視窗。 鍵入 **Ctrl + Q** 來開啟搜尋方塊，鍵入 **c++**，選擇 [範本]，然後選擇 [建立新的主控台應用程式專案]。 在出現的對話方塊中選擇 [建立]。
    ::: moniker-end
    ::: moniker range="vs-2017"
    從頂端功能表列中 **，選擇 [** 檔案  >  **新增**  >  **專案**]。 在 [新專案] 對話方塊的左窗格中，於 [Visual C++] 下選擇 [Windows Desktop]，然後在中間的窗格中選擇 [Windows 主控台應用程式]。 接著，輸入 **MyDbgApp** 之類的名稱，然後按一下 [確定]。
    ::: moniker-end

    如果您看不到 [Windows 主控台應用程式] 專案範本，請移至 [工具] > [取得工具與功能...]，以開啟 Visual Studio 安裝程式。 Visual Studio 安裝程式即會啟動。 選擇 [使用 C++ 的桌面開發] 工作負載，然後選擇 [修改] 按鈕。

    Visual Studio 會建立專案。

1. 在 MyDbgApp.cpp 中，將下列程式碼

    ```c++
    int main()
    {
        return 0;
    }
    ```

    取代為此程式碼 (請不要移除 `#include "stdafx.h"`)：

    ```c++
    #include <list>
    #include <iostream>

    using namespace std;

    void doWork()
    {
        list <int> c1;

        c1.push_back(10);
        c1.push_back(20);

        const list <int> c2 = c1;
        const int &i = c2.front();
        const int &j = c2.front();
        cout << "The first element is " << i << endl;
        cout << "The second element is " << j << endl;

    }

    int main()
    {
        doWork();
    }
    ```

## <a name="set-a-breakpoint"></a>設定中斷點

「中斷點」是一種標記，會指出 Visual Studio 應暫停程式碼執行的地方，如此一來您可以查看變數值或記憶體行為，或查看程式碼分支是否正在執行。 它是偵錯中最基本的功能。

1. 若要設定中斷點，請按一下 `doWork` 函式呼叫左側的裝訂邊 (或選取該行程式碼並按 **F9** 鍵)。

    ![設定中斷點](../debugger/media/dbg-qs-set-breakpoint.png "設定中斷點")

2. 現在按下 **F5** 鍵 (或選擇 [偵錯] > [開始偵錯])。

    ![叫用中斷點](../debugger/media/dbg-qs-hit-breakpoint.png "叫用中斷點")

    偵錯工具會在您設定中斷點的地方暫停。 暫停偵錯工具和應用程式執行所在的陳述式會以黃色箭號指示。 具有 `doWork` 函式呼叫的該行尚未執行。

    > [!TIP]
    > 如果在迴圈或遞迴中有中斷點，或是您有很多經常逐步執行的中斷點，請使用[條件中斷點](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)，以確保程式碼只在符合特定條件時暫停。 條件中斷點可節省時間，也可以讓您更輕鬆地偵錯難以重現的問題。

    當您嘗試偵錯 C++ 中的記憶體相關失敗時，也可以使用中斷點來檢查位址值 (尋找 NULL) 和參考計數。

## <a name="navigate-code"></a>巡覽程式碼

您可以透過不同的命令來指示偵錯工具繼續。 我們會示出 Visual Studio 2017 開始可用的實用程式碼導覽命令。

在中斷點處暫停時，將滑鼠游標移至陳述式 `c1.push_back(20)` 上方，直到出現綠色的 [執行至點選處] 按鈕 ![執行至點選處](../debugger/media/dbg-tour-run-to-click.png ">runtoclick")，然後按 [執行至點選處] 按鈕。

![執行以按一下](../debugger/media/dbg-qs-run-to-click.png "執行至點選處")

應用程式會繼續執行，並呼叫 `doWork`，然後在您按下按鈕所在的程式碼行暫停。

用來逐步執行程式碼的常用鍵盤命令包括 **F10** 和 **F11**。 如需詳細指示，請參閱[偵錯工具簡介](../debugger/debugger-feature-tour.md)。

## <a name="inspect-variables-in-a-datatip"></a>在資料提示中檢查變數

1. 在目前這一行程式碼中 (以黃色執行指標標示)，使用滑鼠將滑鼠游標移至 `c1` 物件上方以顯示資料提示。

    ![檢視資料提示](../debugger/media/dbg-qs-data-tip.png "檢視資料提示")

    資料提示顯示 `c1` 變數的目前值，並可讓您檢查其屬性。 偵錯時，如果您看到非預期的值，則前面的數行程式碼或呼叫的數行程式碼可能有 Bug。

2. 展開資料提示以查看 `c1` 物件的目前屬性值。

3. 如果您想要釘選資料提示，以便在執行程式碼時繼續查看 `c1` 的值，請按一下釘選小圖示 (您可以將所釘選資料提示移至方便存取的位置)。

## <a name="edit-code-and-continue-debugging"></a>編輯程式碼並繼續偵錯

如果您在偵錯工作階段期間，於程式碼中找到要測試的變更，您也可以這麼做。

1. 按一下 `c2.front()` 的第二個執行個體，並將 `c2.front()` 變更為 `c2.back()`。

2. 按幾下 **F10** 鍵 (或 [偵錯] > [不進入函式]) ，以繼續進行偵錯工具並執行編輯的程式碼。

    ![編輯後繼續](../debugger/media/dbg-qs-edit-and-continue.gif "編輯後繼續")

    **F10** 鍵可讓偵錯工具一次前進一個陳述式，但不進入函式，藉此取代逐步執行 (您略過的程式碼仍會執行)。

如需使用編輯後繼續和功能限制的詳細資訊，請參閱[編輯後繼續](../debugger/edit-and-continue.md)。

## <a name="next-steps"></a>下一步

在本教學課程中，您已了解如何啟動偵錯工具、逐步執行程式碼，以及檢查變數。 建議您進一步查看偵錯工具功能，以及詳細資訊的連結。

> [!div class="nextstepaction"]
> [偵錯工具簡介](../debugger/debugger-feature-tour.md)
