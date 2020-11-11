---
title: 使用 Visual Studio for Mac 進行調試
description: 偵錯是程式設計當中常見且必要的一部分。 作為成熟的 IDE，Visual Studio for Mac 包含整個套件的功能，可讓偵錯變容易。 從安全偵錯到資料視覺效果，本文將說明如何使用在 Visual Studio for Mac 偵錯的完整潛力。
author: therealjohn
ms.author: johmil
ms.date: 5/13/2020
ms.technology: vs-ide-debug
ms.assetid: BB7A084D-9AC2-48B5-8076-6C8518796BBA
ms.topic: overview
ms.openlocfilehash: 04fae5874a4fefcb51bdef8b00c8cb3b7171057e
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493253"
---
# <a name="debugging-with-visual-studio-for-mac"></a>使用 Visual Studio for Mac 進行調試

Visual Studio for Mac 具有可支援 .NET Core、.NET Framework、Unity 和 Xamarin 應用程式的偵錯工具。

Visual Studio for Mac 使用 [*Mono Soft Debugger*](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger/)，它實作到 Mono 執行階段之中，讓 Visual Studio for Mac 能跨所有平台進行 Managed 程式碼的偵錯。

## <a name="the-debugger"></a>偵錯工具

Visual Studio for Mac 使用 Mono Soft Debugger 針對所有 Xamarin 應用程式進行 Managed (C# 或 F#) 程式碼的偵錯。 Mono 軟偵錯工具與一般偵錯工具不同，因為它是內建于 Mono 執行時間的合作式偵錯工具。產生的程式碼和 Mono 執行時間會與 IDE 合作，以提供偵錯工具體驗。 Mono 執行階段會透過網路通訊協定公開偵錯功能，您可以在 [Mono 文件](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger-wire-format/)中深入了解。

硬式偵錯工具，例如 [LLDB]( http://lldb.llvm.org/index.html) 或 [GDB]( https://www.gnu.org/software/gdb/)，會控制程式，而被偵錯的程式不必知情或合作，但在您需要偵錯原生 iOS 或 Android 程式碼，偵錯 Xamarin 應用程式時仍然十分有用。

若是 .NET Core 和 ASP.NET Core 應用程式，Visual Studio for Mac 使用 .NET Core 偵錯工具。 此偵錯工具也是合作的偵錯工具，可搭配 .NET 執行時間使用。

## <a name="using-the-debugger"></a>使用偵錯工具

若要開始進行任何應用程式的偵錯，請務必確定組態已設為 [偵錯]。 偵錯組態會提供有用的一組工具來支援偵錯，例如中斷點、使用資料的視覺化檢視，以及檢視呼叫堆疊：

![偵錯組態](media/debugging-image_0.png)

## <a name="setting-a-breakpoint"></a>設定中斷點

若要在您的 IDE 中設定中斷點，請在編輯器按一下您要中斷之程式碼行號旁邊的邊界區域：

![在邊界設定中斷點](media/debugging-image0.png)

您可以前往 [  **中斷點] 視窗** 來查看程式碼中已設定的所有中斷點：

![中斷點的清單](media/debugging-image0a.png)

## <a name="start-debugging"></a>開始偵錯

若要啟動偵錯工具，請選取目標瀏覽器、裝置或模擬器/模擬器：

![Debug configuration ](media/debugging-image_0.png)
 ![ 選取目標裝置](media/debugging-image1.png)

然後按 [播放] 按鈕，或 **Cmd + return** 部署您的應用程式。 當您到達中斷點時，程式碼反白顯示為黃色：

![反白顯示已到達中斷點](media/debugging-image2.png)

偵錯工具，例如用來檢查物件值的工具，可在此時用來取得程式碼中發生情況的詳細資訊：

![視覺效果偵錯](media/debugging-image3.png)

## <a name="conditional-breakpoints"></a>條件式中斷點

您也可以設定規則，指出應該發生中斷點的情況，這就是新增「條件中斷點」。 若要設定條件中斷點，請存取 [中斷點屬性] 視窗，這可以透過兩種方式進行：

* 若要新增條件中斷點，請在您想要設定中斷點的程式碼行號左邊，以滑鼠右鍵按一下編輯器邊界，然後選取 [新增中斷點]：

 ![[中斷點] 操作功能表](media/debugging-image4.png)

* 若要將條件加入至現有的中斷點，請以滑鼠右鍵按一下中斷點，然後選取 [  **中斷點屬性** ]，或在 [  **中斷點] 視窗** 中，選取 [編輯中斷點] 按鈕，如下所示：

 ![在中斷點視窗中編輯現有的中斷點](media/debugging-image5.png)

然後，您可以輸入想要中斷點發生的條件：

 ![編輯中斷點條件](media/debugging-image6.png)

## <a name="stepping-through-code"></a>逐步執行程式碼

當已到達中斷點時，偵錯工具可讓您控制程式的執行。 Visual Studio for Mac 會顯示四個按鈕，可讓您執行與逐步執行程式碼。 在 Visual Studio for Mac 中，它們看起來如下所示：

 ![逐步執行程式碼的按鈕](media/debugging-image7.png)

下面是四個按鈕：

* **播放** - 這會開始執行程式碼，直到下一個中斷點。
* 不進入一 **步** -這會執行下一行程式碼。 如果下一行是函式呼叫，不進入函式會執行該函式，並在函式「之後」的下一行程式碼停止。
* **逐步執行** - 這也會執行下一行程式碼。 如果下一行是函式呼叫，逐步執行會停止在函式的第一行，讓您繼續一行一行地進行函式的偵錯。 如果下一行不是函式，它的行為與「不進入函式」相同。
* **跳出** -這會回到呼叫目前函式的行。

## <a name="change-which-statement-is-executed-next"></a>變更接下來要執行的語句

當偵錯工具暫停時，邊界上的箭號會指出接下來所要執行的程式碼行。 您可以按一下該箭號，將其拖曳至不同的程式碼行來變更所要執行的陳述式。 您也可以在程式程式碼上按一下滑鼠右鍵，然後從操作功能表選取 **[設定下一個語句]** ，來達到相同的目的。

![拖放箭號以設定下一個語句](media/debugger-drag-setnextstatement.gif)

> [!CAUTION]
> 變更目前的執行行可能會導致應用程式發生未預期的行為。 此外，也有一些條件是無法變更下一個要執行的語句。 例如，將箭號從某個方法拖曳到另一個方法將無法運作。 在這些不受支援的情況下，Visual Studio for Mac 將會顯示一個對話方塊，讓您知道不可能變更目前執行的行。 

## <a name="debugging-monos-class-libraries"></a>Mono 類別庫偵錯

Xamarin 產品隨附 Mono 類別庫的原始程式碼，您可以使用它從偵錯工具逐步檢查一切背後運作的情況。

因為這項功能會在偵錯期間消耗較多的記憶體，所以它預設會關閉。

若要啟用這項功能，請流覽至  **Visual Studio for Mac > 喜好設定 > 偵錯工具** ，並確認已選取 [ **逐步執行外部程式碼** ] 選項，如下 **所** 示：

![逐步執行外部程式碼選項](media/debugging-image8.png)

## <a name="see-also"></a>請參閱

- [在 Visual Studio (Windows) 中偵錯](/visualstudio/debugger/)
