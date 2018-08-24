---
title: 偵錯 c + +
description: 使用 Visual Studio 偵錯工具的原生程式碼進行偵錯
ms.custom: mvc
ms.date: 08/06/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: 639e430b-6d2d-46bd-b738-8c60dfb384f1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 036774134f705d95fbc526a9e6a336ac43005820
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639772"
---
# <a name="quickstart-debug-with-c-using-the-visual-studio-debugger"></a>使用 c + + 使用 Visual Studio 偵錯工具的快速入門： 偵錯

Visual Studio 偵錯工具提供許多功能強大的功能，可協助您偵錯您的應用程式。 本主題提供了解一些基本功能的快速方法。

## <a name="create-a-new-project"></a>建立新專案 

1. 在 Visual Studio 中，選擇 [檔案] > [新增專案]。

2. 在 [Visual C++] 下方，選擇 [Windows 桌面]，然後在中間窗格中選擇 [Windows 主控台應用程式]。

    如果您沒有看到**Windows 主控台應用程式**專案範本，請按一下 [**開啟 Visual Studio 安裝程式**的左窗格中的連結**新專案**] 對話方塊。 Visual Studio 安裝程式即會啟動。 選擇**使用 c + + 的桌面開發**工作負載，然後選擇**修改**。

3. 輸入名稱，例如**MyDbgApp**然後按一下**確定**。

    Visual Studio 會建立專案。

4. 在 MyDbgApp.cpp 中，將下列程式碼

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

A*中斷點*會指示 Visual Studio 應暫止您的執行中的標記程式碼，使您可以看看變數的值或記憶體，或正在執行的程式碼分支是否的行為。 這是在偵錯最基本的功能。

1. 若要設定中斷點，按一下左邊的裝訂邊`doWork`函式呼叫 (或選取一行程式碼，然後按**F9**)。

    ![設定中斷點](../debugger/media/dbg-qs-set-breakpoint.png "設定中斷點")

2. 現在，按下**F5** (或選擇**偵錯 > 啟動偵錯**)。

    ![叫用中斷點](../debugger/media/dbg-qs-hit-breakpoint.png "叫用中斷點")

    您用來設定中斷點的偵錯工具暫停。 暫停偵錯工具和應用程式執行所在的陳述式會以黃色箭號。 該程式行使用`doWork`函式呼叫尚未執行。

    > [!TIP]
    > 如果您有以迴圈或遞迴時，中斷點，或如果您有許多的中斷點，您經常逐步執行，使用[條件式中斷點](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)藉此確定只在符合特定條件時，會暫停您的程式碼。 條件式中斷點省時又還能夠更輕鬆地偵錯難以重現的問題。

    當您嘗試偵錯記憶體相關的失敗，c + + 中，您也可以使用中斷點來檢查位址值 （尋找 NULL） 和參考計數。 

## <a name="navigate-code"></a>巡覽程式碼

有不同的命令，以指示以繼續偵錯工具。 我們會示範 Visual Studio 2017 的新實用的程式碼巡覽命令。

當在中斷點暫停時，將滑鼠移至陳述式`c1.push_back(20)`直到綠色**執行至點選** 按鈕![執行至點選處](../debugger/media/dbg-tour-run-to-click.png "RunToClick")隨即出現，並再按下**執行至點選** 按鈕。

![按一下 執行](../debugger/media/dbg-qs-run-to-click.png "執行 按一下")

在應用程式繼續執行，呼叫`doWork`，並在您所按按鈕的程式碼行上暫停。

通用的鍵盤命令，可用來逐步執行程式碼包含**F10**並**F11**。 如需詳細的深入指示，請參閱[初級開發人員指南](../debugger/getting-started-with-the-debugger.md)。

## <a name="inspect-variables-in-a-datatip"></a>檢查資料提示方塊中的變數

1. 在目前這一行程式碼 （黃色執行指標為標記），滑鼠停留`c1`物件，使用滑鼠來顯示資料提示方塊。

    ![檢視資料提示方塊](../debugger/media/dbg-qs-data-tip.png "檢視資料提示方塊")

    資料提示方塊會顯示目前的值`c1`變數，並可讓您檢查其屬性。 偵錯時，如果您看到未預期的值，您可能有 bug 前面或呼叫行程式碼。 

2. 展開以查看目前的屬性值的資料提示方塊`c1`物件。

3. 如果您想要固定 datatip，讓您可以繼續以查看值`c1`時執行程式碼時，按一下 小釘選圖示。 （您可以移動固定資料提示方塊到方便存取的位置）。

## <a name="edit-code-and-continue-debugging"></a>編輯程式碼並繼續偵錯

如果您找出您想要測試您的程式碼，在 偵錯工作階段中的變更，您可以這麼做，太。

1. 按一下第二個執行個體`c2.front()`並變更`c2.front()`至`c2.back()`。

2. 按下**F10** (或**偵錯 > 不進入函式**) 數次才能進入偵錯工具，並執行已編輯的程式碼。

    ![編輯後繼續](../debugger/media/dbg-qs-edit-and-continue.gif "編輯後繼續")

    **F10**前進一次，但步驟的偵錯工具的其中一個陳述式而不函式，而不是逐步執行它們 （您略過的程式碼仍會執行）。

如需使用 編輯後繼續以及功能限制的詳細資訊，請參閱 <<c0> [ 編輯後繼續](../debugger/edit-and-continue.md)。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已了解如何啟動偵錯工具，逐步執行程式碼，並檢查變數。 若要高階查看偵錯工具功能，以及其他更多資訊的連結。

> [!div class="nextstepaction"]
> [偵錯工具功能導覽](../debugger/debugger-feature-tour.md)
