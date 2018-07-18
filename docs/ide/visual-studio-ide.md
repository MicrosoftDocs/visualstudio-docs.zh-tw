---
title: Visual Studio 2017 的概觀
ms.date: 06/01/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- MSDNSTART
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a7667cac2a26a3e98d2e92dfeb13cee36d870e9
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34691156"
---
# <a name="visual-studio-ide-overview"></a>Visual Studio IDE 概觀

Visual Studio 是一個互動式開發環境 (IDE)；這是一個有創意的啟動控制板，可供您用來檢視和編輯程式碼，然後偵錯、建置及發佈應用程式。

Visual Studio 適用於 Windows 和 Mac。 [Visual Studio for Mac](/visualstudio/mac/) 有許多與 Visual Studio 2017 相同的功能，並已針對開發跨平台和行動應用程式最佳化。

本文著重在 Visual Studio 2017 for Windows。 文中將為您介紹 IDE 的基本功能。 我們將逐步解說您可以運用 Visual Studio 來進行的一些操作，包括建立簡單的專案、使用 IntelliSense 作為程式碼撰寫輔助工具，以及偵錯應用程式來查看程式執行期間的變數值。 我們也將介紹各種工具視窗。

## <a name="install-the-visual-studio-ide"></a>安裝 Visual Studio IDE

若要開始，請[下載 Visual Studio 2017](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) 並將它安裝在您的系統上。

模組安裝程式可讓您選擇並安裝「工作負載」，這些通常是您慣用的程式設計語言或平台所需的幾組功能。 若要遵循[建立程式](#create-a-program)的步驟，請務必在安裝期間選取 **.NET Core 跨平台開發**工作負載。 快速入門主題 (例如 [Visual Studio 中的 C++ 使用者入門](getting-started-with-cpp-in-visual-studio.md)) 包含安裝其他工作負載的指示。

![Visual Studio 安裝程式](../ide/media/overview-net-core-workload.png)

當您第一次啟動 Visual Studio 時，可以視需要使用您的 Microsoft 帳戶或是工作或學校帳戶來登入。

## <a name="tour-of-the-ide"></a>IDE 導覽

為了提供您一個概要的 Visual Studio 視覺總覽，下圖顯示已開啟一個專案及數個您最可能使用之重要工具視窗的 Visual Studio：

![Visual Studio IDE](../ide/media/visualstudioide.png)

- [方案總管](../ide/solutions-and-projects-in-visual-studio.md)可讓您檢視、瀏覽及管理您的程式碼檔案。 方案總管透過將程式碼的檔案分組到方案和專案，以協助組織程式碼。

- [編輯器](../ide/writing-code-in-the-code-and-text-editor.md)視窗 (您可能大多數時間都花費在這裡) 會顯示程式碼，並可讓您編輯原始程式碼及設計 UI。

- [[輸出] 視窗](../ide/reference/output-window.md)是 Visual Studio 傳送其通知的位置，例如偵錯和錯誤訊息、編譯器警告、發佈狀態訊息等。 每個訊息來源都有自己的索引標籤。

- [Team Explorer (VSTS)](/vsts/user-guide/work-team-explorer) 可讓您追蹤工作項目，並使用版本控制技術 (例如 [Git](https://git-scm.com/) 和 [Team Foundation 版本控制 (TFVC)](/vsts/tfvc/overview)) 與其他人共用程式碼。

以下是 Visual Studio 中一些其他熱門的生產力功能：

- [重構](../ide/refactoring-in-visual-studio.md)包含一些作業，例如智慧型的變數重新命名、將選取的多行程式碼移動到個別函式、將程式碼移到其他位置、重新排序函式參數等等。

   ![重構](../ide/media/VSIDE_refactor.png)

- [IntelliSense](../ide/using-intellisense.md) 為一種涵蓋一組常用功能的概括性詞彙，會直接在編輯器中顯示有關您程式碼的類型資訊，而在某些情況下會為您撰寫一些程式碼。 就像內嵌在編輯器中的基本文件，讓您無需在個別的 [說明] 視窗中查閱類型資訊。 IntelliSense 功能會因語言而異。 如需詳細資訊，請參閱 [C# IntelliSense](../ide/visual-csharp-intellisense.md)、[Visual C++ IntelliSense](../ide/visual-cpp-intellisense.md)、[JavaScript IntelliSense](../ide/javascript-intellisense.md) 和 [Visual Basic IntelliSense](../ide/visual-basic-specific-intellisense.md)。 下圖顯示一些可用的 IntelliSense 功能：

   ![Visual Studio 成員清單](../ide/media/vs2017_Intellisense.png)

- [快速啟動](../ide/reference/quick-launch-environment-options-dialog-box.md)搜尋方塊是一個可讓您在 Visual Studio 中快速找到所需項目的絕佳方式。 只要開始鍵入您要尋找之任何項目的名稱，Visual Studio 會列出結果將您引導至您確實想要去的地方。 [快速啟動] 也會顯示連結，這些連結可啟動任何工作負載或個別元件的 **Visual Studio 安裝程式**。

   ![[快速啟動] 搜尋方塊](../ide/media/VSIDE_Tour_QuickLaunch.png)

- **波浪線**是波浪底線，可在您鍵入程式碼時，針對錯誤或潛在的問題即時提出警示。 這可讓您立即修正它們，而不需等到編譯或執行階段才發現錯誤。 如果您將滑鼠停留在波浪線，則您會看到有關此錯誤的其他資訊。 左邊界也可能會出現燈泡與修正錯誤的動作。 如需詳細資訊，請參閱[快速動作](../ide/quick-actions.md)。

   ![波浪線](../ide/media/vs2017_squiggle.png)

- 您可以在文字編輯器操作功能表上開啟[呼叫階層](../ide/reference/call-hierarchy.md)視窗，以顯示呼叫插入點 (caret) 底下方法及被該方法呼叫的方法。

   ![呼叫階層視窗](../ide/media/VSIDE_call_hierarchy.png)

- [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) 可讓您尋找程式碼、已連結的 Bug、工作項目、程式碼檢閱和單元測試的參考和變更，而不需離開編輯器。

   ![CodeLens](../ide/media/codelensoverview.png)

- [[查看定義]](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) 視窗會顯示方法或類型的定義內嵌，而不用離開您目前的內容。

   ![查看定義](../ide/media/VSIDE_peek_definition.png)

- [[移至定義]](../ide/go-to-and-peek-definition.md) 內容功能表選項會讓您直接進入定義函式或物件的位置。 以滑鼠右鍵在編輯器中按一下，還有其他巡覽命令可供使用。

   ![移至定義](../ide/media/VSIDE_go_to_definition.png)

## <a name="create-a-program"></a>建立程式

讓我們來深入探討並建立一個新的簡單程式。

1. 開啟 Visual Studio。 在功能表上，選擇 [檔案] > [新增] > [專案]。

  ![功能表列上的 [檔案] > [新增專案]](../ide/media/VSIDE_Tour_NewProject1.png)

1. [新增專案] 對話方塊會顯示數個專案「範本」。 範本包含指定專案類型所需的基本檔案和設定。 選擇 [Visual C#] 下的 [.NET Core] 類別，然後選擇 [主控台應用程式 (.NET Core)] 範本。 在 [名稱] 文字方塊中，鍵入 **HelloWorld**，然後選取 [確定] 按鈕。

  ![.NET Core 應用程式範本](../ide/media/overview-new-project-dialog.png)

   Visual Studio 會建立專案。 其為簡單的 "Hello World" 應用程式，會呼叫 <xref:System.Console.WriteLine?displayProperty=nameWithType> 方法來顯示常值字串 "Hello World!" 。

  > [!NOTE]
  > 如果您未看到 [.NET Core] 類別，則需要安裝 [.NET Core 跨平台開發] 工作負載。 若要安裝，請選擇 [新增專案] 對話方塊左下角的 [開啟 Visual Studio 安裝程式] 連結。 在 [Visual Studio 安裝程式] 開啟後，請向下捲動並選取 [.NET Core 跨平台開發] 工作負載，然後選取 [修改]。

   您應該會立即看到類似下列的畫面：

   ![Visual Studio IDE](../ide/media/overview-ide-console-app.png)

   您應用程式的 C# 程式碼會顯示在編輯器視窗中，其占據了大部分的空間。 請注意，系統會將文字自動標示色彩，以表示不同層面的程式碼，例如關鍵字和類型。 此外，程式碼中的垂直小虛線會指出那些大括號彼此成對，而行號則可協助您稍後找出程式碼。 您可以選擇帶方框的小負號來摺疊或展開程式碼。 此程式碼大綱功能可讓您隱藏您不需要的程式碼，有助於讓畫面變得較為簡潔。

   專案檔會列在右邊稱作 [方案總管] 的視窗中。

  ![具有紅色方塊的 Visual Studio IDE](../ide/media/overview-ide-console-app-red-boxes.png)

  還有其他可用的功能表和工具視窗，但讓我們目前先繼續進行操作。

1. 現在，啟動應用程式。 您可以藉由從功能表列上的 [偵錯] 功能表選擇 [啟動但不偵錯]，來執行此動作。 您也可以按 **Ctrl**+**F5**。

  ![[偵錯] > [啟動但不偵錯] 功能表](../ide/media/overview-start-without-debugging.png)

  Visual Studio 會建置應用程式，然後主控台視窗會開啟並顯示訊息 **Hello World!**。 您現在已有一個執行中的應用程式！

  ![主控台視窗](../ide/media/overview-console-window.png)

1. 若要關閉主控台視窗，請在鍵盤上按下任意鍵。

1. 讓我們將一些其他程式碼新增至應用程式。 在 `Console.WriteLine("Hello World!");` 行前新增下列 C# 程式碼：

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   此程式碼會在主控台視窗中顯示 **What is your name?**，然後等待使用者輸入某些文字並按下 **Enter** 鍵。

1. 將 `Console.WriteLine("Hello World!");` 行變更為下列程式碼：

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. 選取 偵錯 > 啟動但不偵錯 或按 **Ctrl**+**F5**，再次執行應用程式。

   Visual Studio 會重建應用程式，然後主控台視窗會開啟並提示您輸入您的名稱。

1. 請在主控台視窗中輸入您的名稱，並按下 **ENTER**。

   ![主控台視窗輸入](media/overview-console-input.png)

1. 按任意鍵以關閉主控台視窗並停止執行程式。

## <a name="use-refactoring-and-intellisense"></a>使用重構和 IntelliSense

讓我們看看[重構](refactoring-in-visual-studio.md)和 [IntelliSense](using-intellisense.md) 這兩種方式如何協助您更有效率地撰寫程式碼。

首先，請重新命名 `name` 變數：

1. 按兩下 `name` 變數來選取它。

1. 鍵入變數的新名稱 `username`。

   請注意，變數周圍會出現一個灰色方塊，而邊界會出現一個燈泡。

1. 選取燈泡圖示以顯示可用的[快速動作](quick-actions.md)。 選取 [將 'name' 重新命名為 'username']。

   ![重新命名 Visual Studio 中的動作](media/rename-quick-action.png)

   此變數會在專案中重新命名，在我們的案例中只有兩個位置。

   ![顯示 Visual Studio 中重新命名重構的動畫 GIF](media/rename-refactoring.gif)

1. 現在，讓我們看看 IntelliSense。 在 `Console.WriteLine($"\nHello {username}!");` 行下方，鍵入 **DateTime now = DateTime.**。

   一個方塊會顯示 <xref:System.DateTime> 類別的成員。 此外，目前選取成員的描述會顯示在另一個方塊中。

   ![Visual Studio 中的 IntelliSense 清單成員](media/intellisense-list-members.png)

1. 按兩下名為 **Now** 的成員或按下**定位鍵**來選取此成員，這是類別的屬性。新增分號 **;** 以完成程式碼行。

1. 在下方鍵入或複製下列程式碼行：

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> 與 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> 稍有不同，它不會在列印之後新增行結束字元。 這表示傳送至輸出的下一段文字會列印在同一行。 您可以將滑鼠移至程式碼中每個方法上方來查看其描述。

1. 接下來，我們將再使用一次重構，讓程式碼更精簡。 按一下 `DateTime now = DateTime.Now;` 行中的變數 `now`。

   請注意，該行的邊界會出現一個小螺絲起子圖示。

1. 按一下螺絲起子圖示，以查看 Visual Studio 所提供的建議。 在本例中，它會顯示[內嵌暫存變數](reference/inline-temporary-variable.md)重構移除程式碼行，而未變更整體行為：

   ![Visual Studio 中的內嵌暫存變數重構](media/inline-temporary-variable-refactoring.png)

1. 按一下 [內嵌暫存變數] 以重構程式碼。

1. 按下 **Ctrl**+**F5**，再執行一次程式。 輸出會與下列內容類似：

   ![含有程式輸出的主控台視窗](../ide/media/overview-console-final.png)

## <a name="debug-code"></a>偵錯程式碼

當您撰寫程式碼時，必須執行並測試它，以找出 Bug。 Visual Studio 偵錯系統可讓您以一次一個陳述式的方式逐步偵錯程式碼，並一邊檢查變數。 您可以將中斷點設定成只在指定的條件為 true 時才叫用。 您可以在程式碼執行時，監視變數的值等等。

讓我們來設定中斷點，以查看程式「進行」期間的 `username` 變數值。

1. 尋找程式碼行 `Console.WriteLine($"\nHello {username}!");`。 若要設定這行程式碼的中斷點，讓程式在這行暫停執行，請按一下編輯器的左邊界。 您也可以按一下該行程式碼的任何位置，然後按下 **F9** 鍵。

   左邊界會出現一個紅色圓圈，並以紅色醒目顯示程式碼。

   ![Visual Studio 中程式碼行的中斷點](media/breakpoint.png)

1. 選取 [偵錯] > [開始偵錯] 或按 **F5** 鍵以開始偵錯。

1. 在主控台視窗出現並要求您的名稱時，鍵入名稱並按 **Enter** 鍵。

   請注意，焦點會返回 Visual Studio 程式碼編輯器，並以黃色醒目提示具有中斷點的程式碼行。 這表示程式要執行的下一行程式碼。

1. 將滑鼠移至 `username` 變數上方以查看其值。 或者，您可以在 `username` 上按一下滑鼠右鍵，然後選取 [新增監看式] 將變數新增至 [監看式] 視窗，您也可以在此查看其值。

   ![Visual Studio 偵錯期間的變數值](media/debugging-variable-value.png)

1. 若要讓程式執行到完成，請再按一次 **F5** 鍵。

如需有關 Visual Studio 中之 偵錯的更多詳細資料，請參閱[偵錯工具功能導覽](../debugger/debugger-feature-tour.md)。

## <a name="customize-visual-studio"></a>自訂 Visual Studio

您可以個人化 IDE，包括變更預設色彩佈景主題。 若要變更為 [深色] 佈景主題：

1. 在功能表列上，選擇 [工具] > [選項] 來開啟 [選項] 對話方塊。

1. 在 [環境] > [一般] 選項頁面上，將 [色彩佈景主題] 選項變更為 [深色]，然後選擇 [確定]。

   整個 IDE 的色彩佈景主題會變更為 [深色]。

   ![深色佈景主題的 VS](media/quickstart-personalize-dark-theme.png)

若要了解您可以個人化 IDE 的其他方式，請參閱[個人化 Visual Studio](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="learn-more"></a>進一步了解

您是否想要建立適用於 Android 或 iOS 手機的應用程式？ 或想要建立 3D 遊戲或具備雲端功能的應用程式？ 若要了解 Visual Studio 的這些及其他功能，請參閱 [Visual Studio 2017 的功能](../ide/advanced-feature-overview.md)。

如果您現在才要開始撰寫程式碼，請從目錄選擇其中一個快速入門主題，例如[建立您的第一個 ASP.NET Core Web 應用程式](quickstart-aspnet-core.md)。

您也可以查看 [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!index=2&lang=1033)上可用的免費 Visual Studio 課程。

## <a name="see-also"></a>另請參閱

* [更多 Visual Studio 功能](../ide/advanced-feature-overview.md)
* [www.visualstudio.com](https://www.visualstudio.com/vs/)
* [Visual Studio 部落格](https://blogs.msdn.microsoft.com/visualstudio/)
* [Visual Studio 下載](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)