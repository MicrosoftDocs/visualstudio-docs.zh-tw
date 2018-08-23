---
title: 適用於徹底初學者的偵錯程式碼
description: 如果您正在偵錯，第一次，了解幫助您使用 Visual Studio 的偵錯模式中執行您的應用程式的幾個原則
ms.custom: ''
ms.date: 07/06/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb37faa194e3c370f92f9a82c7866373dd8f26d3
ms.sourcegitcommit: a6734c4d76dae3d21b55b10f3bc618dfa6b62dea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2018
ms.locfileid: "42623711"
---
# <a name="how-to-debug-for-absolute-beginners"></a>如何偵錯適用於徹底初學者

沒有失敗，我們身為軟體開發人員撰寫的程式碼一律不是我們預期它執行。 有時它會完全不同的項目 ！ 當發生這種情況時，下一個工作是找出原因，並且雖然我們可能會想要只保留盯著我們的程式碼的時數，但更容易、 更有效率的方式使用偵錯工具，或偵錯工具。

偵錯工具中，不幸的是，不可以在我們的程式碼中神奇地顯示所有問題或是"bug"的項目。 *偵錯*方法來執行您的程式碼逐步偵錯工具在像是 Visual Studio 中，若要尋找您所做的程式設計錯誤的精確點。 然後了解您需要在您的程式碼中進行哪些修正及偵錯工具通常可讓您進行因應暫時變更，因此您可以繼續執行程式。

有效地使用偵錯工具，也是需要時間和了解的做法，但終究是重要的工作，每位軟體開發人員的技能。 在本文中，然後，我們導入的核心原則之一偵錯並提供可協助您開始的秘訣。

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>釐清問題，問問自己適當的問題

這有助於釐清您嘗試修正此問題之前，您執行到的問題。 我們預期，您已經執行的問題在您的程式碼中，否則您不會在此嘗試了解如何進行偵錯 ！ 因此，在開始偵錯之前，請確定您已經識別了您想要解決此問題：

* 預期您的程式碼？

* 發生什麼事改為？

    如果執行您的應用程式時遇到錯誤 （例外狀況），這可以是一件好事 ！ 例外情況是執行程式碼，通常是某種類型的錯誤時，發現非預期的事件。 偵錯工具可以帶您前往發生例外狀況的確切位置中您的程式碼，並可協助您調查可能的修正。

    如果發生其他狀況，問題的徵兆為何？ 您已經懷疑這個問題發生在程式碼中的位置？ 例如，如果您的程式碼會顯示一些文字，但文字不正確，您知道可能是您的資料不正確，或設定顯示文字的程式碼有某種程度的 bug。 透過逐步偵錯工具中的程式碼，您可以檢查每個變更至您要探索的確切時間，以及如何指派正確值的變數。

## <a name="examine-your-assumptions"></a>檢查您的假設

您可以調查 bug 或錯誤之前，請考慮您預期某些結果所做的假設。 隱藏或未知的假設可以妨礙識別問題，即使您正在偵錯工具中正確的問題原因。 您可能會有一長串的可能假設 ！ 以下是幾個問題要問問自己挑戰您的假設。

* 您是否使用正確的 API （也就是正確的物件、 函式、 方法或屬性）？ 您使用的 API 可能會執行您認為它。 （您檢查偵錯工具中的 API 呼叫之後，修正它可能需要某趟車程支付的說明文件，以協助找出正確的 API）。

* 您已正確地使用 API 嗎？ 或許您會使用 API 的權限，但未使用正確的方式。

* 您的程式碼是否包含任何錯字？ 有些打錯字，像是簡單的拼字錯誤的變數名稱，很難看到，尤其是當使用語言並不需要使用這些宣告的變數。

* 您未對您的程式碼進行變更並假設它是不相關，您發現的問題嗎？

* 未預期的物件或變數，以包含特定值 （或特定類型的值） 不同於真正發生的事嗎？

* 您知道程式碼的意圖嗎？ 它通常會較難偵錯其他人的程式碼。 如果不是您的程式碼，很可能您可能需要花時間學習完全哪些程式碼執行之前，您可以偵錯它有效。

    > [!TIP]
    > 在撰寫程式碼，以小規模開始，並開始運作的程式碼 ！ （好的範例程式碼是很有幫助這裡）。有時候，很容易修正的大型或複雜集合的程式碼開始一小段的程式碼，示範您嘗試達成的核心工作。 然後，您可以修改或加入程式碼以累加的方式，測試在每個點的錯誤。

您可能會被您的假設，來減少程式碼中發現的問題所花費的時間。 您也可以減少修正的問題所花費的時間。

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>逐步執行程式碼在偵錯模式，來尋找發生問題

當您通常會執行應用程式時，您看到錯誤和不正確的結果程式碼都執行之後，才。 程式也可能會無預警地終止不告訴您原因。

執行應用程式中偵錯工具，也稱為*偵錯模式*，表示，偵錯工具主動監視發生在程式執行的所有項目。 它也可讓您暫停在任何時間點檢查其狀態，，然後逐步執行您的程式碼行以觀看每個詳細資料，當它發生於應用程式。

您可以在 Visual Studio 中，輸入偵錯模式來使用**F5** (或**偵錯** > **開始偵錯**功能表命令或**開始偵錯**  按鈕![啟動偵錯](../debugger/media/dbg-tour-start-debugging.png "開始偵錯")) 在偵錯 工具列中。 如果發生任何例外狀況，則 Visual Studio 的例外狀況協助程式會帶您前往例外狀況發生的地方，並提供其他實用資訊的精確點。

如果您未收到例外狀況，您可能有個不錯的主意哪裡尋找您的程式碼中的問題。 這其中使用的位置*中斷點*偵錯工具，讓您有機會更仔細檢查您的程式碼。 中斷點是可靠偵錯最基本也最重要的功能。 中斷點會指出，Visual Studio 應暫停程式碼執行讓您可以看看變數的值，或記憶體的行為或程式碼會執行的順序。

在 Visual Studio 中，您可以快速地在程式碼行旁邊的左邊界中按一下 設定中斷點。 或將游標放在線條，然後按**F9**。

為了協助說明這些概念，我們引導您已經有數個 bug 一些範例程式碼。 我們使用 C# 中，但偵錯功能適用於 Visual Basic、 c + +、 JavaScript、 Python 和其他支援的語言。

### <a name="create-a-sample-app-with-some-bugs"></a>建立範例應用程式 （具有一些 bug)

接下來，我們將建立具有幾個 bug 的應用程式。

1. 您必須安裝 Visual Studio 和其中一個。**NET 桌面開發**工作負載或。**.NET Core 跨平台開發**安裝工作負載，取決於哪一個應用程式，輸入您想要建立。

    如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)頁面免費進行安裝。

    如果您要安裝工作負載，但已經有 Visual Studio 中，按一下**工具** > **取得工具和功能**。 Visual Studio 安裝程式即會啟動。 選擇。**NET 桌面開發**(或。**.NET Core 跨平台開發**) 的工作負載，然後選擇**修改**。

1. 開啟 Visual Studio 中，並選擇**檔案** > **新增** > **專案**。

1. 選擇您的應用程式程式碼的範本。

    適用於.NET Framework 中**新的專案**對話方塊方塊中，選擇**Visual C#**， **Windows Desktop**從已安裝的範本 區段中，然後在中間窗格中選取**主控台應用程式 (.NET Framework)**。

    適用於.NET Core 中**新專案**對話方塊方塊中，選擇**Visual C#**， **.NET Core**從已安裝的範本 區段中，然後在中間窗格中選取**主控台應用程式 (.NET Core)**。

    如果您沒有看到這些範本，您必須安裝適當的工作負載 （請參閱先前的步驟）。

1. 在 **名稱**欄位中，輸入**ConsoleApp FirstApp** ，按一下 **確定**。

    Visual Studio 建立主控台專案，就會出現在 [方案總管] 中，在右窗格中。

1. 在  *Program.cs*，取代為下列程式碼中的所有預設程式碼：

    ```csharp
    using System;
    using System.Collections.Generic;
    
    namespace ConsoleApp_FirstApp
    {
        class Program
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Welcome to Galaxy News!");
                IterateThroughList();
                Console.ReadKey();
            }
    
            private static void IterateThroughList()
            {
                var theGalaxies = new List<Galaxy>
            {
                new Galaxy() { Name="Tadpole", MegaLightYears=400, GalaxyType=new GType('S')},
                new Galaxy() { Name="Pinwheel", MegaLightYears=25, GalaxyType=new GType('S')},
                new Galaxy() { Name="Cartwheel", MegaLightYears=500, GalaxyType=new GType('L')},
                new Galaxy() { Name="Small Magellanic Cloud", MegaLightYears=.2, GalaxyType=new GType('I')},
                new Galaxy() { Name="Andromeda", MegaLightYears=3, GalaxyType=new GType('S')},
                new Galaxy() { Name="Maffei 1", MegaLightYears=11, GalaxyType=new GType('E')}
            };
    
                foreach (Galaxy theGalaxy in theGalaxies)
                {
                    Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
                }
    
                // Expected Output:  
                //  Tadpole  400,  Spiral 
                //  Pinwheel  25,  Spiral 
                //  Cartwheel, 500,  Lenticular
                //  Small Magellanic Cloud .2,  Irregular
                //  Andromeda  3,  Spiral
                //  Maffei 1,  11,  Elliptical
            }
        }
    
        public class Galaxy
        {
            public string Name { get; set; }
    
            public double MegaLightYears { get; set; }
            public object GalaxyType { get; set; }
    
        }
    
        public class GType
        { 
            public GType(char type)
            {
                switch(type)
                {
                    case 'S':
                        MyGType = Type.Spiral;
                        break;
                    case 'E':
                        MyGType = Type.Elliptical;
                        break;
                    case 'l':
                        MyGType = Type.Irregular;
                        break;
                    case 'L':
                        MyGType = Type.Lenticular;
                        break;
                    default:
                        break;
                }
            }
            public object MyGType { get; set; }
            private enum Type { Spiral, Elliptical, Irregular, Lenticular}
        }
    }
    ```

    全都放在清單中顯示 galaxy 名稱，到 galaxy，以及銀河系類型之間的距離為我們的目的，此程式碼。 偵錯，請務必了解程式碼的意圖。 以下是一行從清單中，我們想要在輸出中顯示的格式：

    *galaxy 名稱*，*距離*， *galaxy 類型*。

### <a name="run-the-app"></a>執行應用程式

1. 按下**F5**或**開始偵錯** 按鈕![開始偵錯](../debugger/media/dbg-tour-start-debugging.png "開始偵錯")偵錯 工具列中，在位於程式碼編輯器。

    應用程式會啟動並沒有任何偵錯工具向我們顯示的例外狀況。 不過，您會看到在主控台視窗中的輸出是不如預期。 以下是預期的輸出：

    ```
    Tadpole  400,  Spiral 
    Pinwheel  25,  Spiral 
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    但是，我們會改為看到：

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType 
    Pinwheel  25,  ConsoleApp_FirstApp.GType 
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    尋找輸出，而是在我們的程式碼，我們知道`GType`儲存 galaxy 類型的類別名稱。 我們想要顯示實際 galaxy 類型 （例如 「 什麼 」），而不是類別名稱 ！

### <a name="debug-the-app"></a>偵錯應用程式

1. 在應用程式仍在執行時，設定中斷點旁邊按一下左邊界`Console.WriteLine`這行程式碼中的方法呼叫。

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }    
    ```

    當您設定中斷點時，會出現一個紅點的左邊界。

    因為我們所見的輸出中的問題，我們將開始查看上述設定輸出偵錯工具中的程式碼偵錯。

1. 按一下 [**重新啟動**![重新啟動應用程式](../debugger/media/dbg-tour-restart.png "RestartApp")中偵錯] 工具列按鈕 (**Ctrl** + **Shift**  +  **F5**)。

    應用程式會在您設定的中斷點暫停。 黃色反白顯示表示偵錯工具已暫停的地方 （黃色的一行程式碼尚未執行）。

1. 將滑鼠停留`GalaxyType`變數以扳手圖示左邊，右邊，然後展開`theGalaxy.GalaxyType`。 您會看到`GalaxyType`包含的屬性`MyGType`，且屬性值設定為`Spiral`。

    ![檢查變數](../debugger/media/beginners-inspect-variable.png)

    「 什麼 」 是實際上您想要列印至主控台的正確值 ！ 所以，您可以存取這個值，這個程式碼中的執行應用程式時一個不錯的起點。 在此案例中，我們會使用不正確的 API。 我們會看到是否我們可以修正此問題的偵錯工具中執行程式碼時。

1. 在相同的程式碼，仍偵錯時，將游標放在結尾`theGalaxy.GalaxyType`並將它變更為`theGalaxy.GalaxyType.MyGType`。 雖然您可以進行這項變更，程式碼編輯器會顯示錯誤，指出它無法編譯此程式碼。

    ![語法錯誤](../debugger/media/beginners-edit.png)

1. 按一下 **編輯**中**編輯後繼續**訊息方塊。 您會看到的錯誤訊息現在**錯誤清單**視窗。 此錯誤指出`'object'`未包含的定義`MyGType`。

    ![語法錯誤](../debugger/media/beginners-no-definition.png)

    即使我們設定每個類型的物件與 galaxy `GType` (其中包含`MGType`屬性)，偵錯工具無法辨識`theGalaxy`物件做為型別的物件`GType`。 發生什麼情況？ 您想要瀏覽設定 galaxy 類型的任何程式碼。 當您這樣做時，您會看到`GType`類別一定會有的屬性`MyGType`，但項目不正確。 相關的錯誤訊息`object`原來是線索; 語言解譯器的類型會顯示為類型的物件`object`而不是型別的物件`GType`。

1. 仔細檢查相關設定 galaxy 類型程式碼，您會發現`GalaxyType`的屬性`Galaxy`類別指定為`object`而不是`GType`。

    ```csharp
    public object GalaxyType { get; set; }     
    ```

1. 將上述程式碼變更如下：

    ```csharp
    public GType GalaxyType { get; set; }     
    ```

1. 按一下 [**重新啟動**![重新啟動應用程式](../debugger/media/dbg-tour-restart.png "RestartApp")中偵錯] 工具列按鈕 (**Ctrl** + **Shift**  +  **F5**) 重新編譯程式碼，並重新啟動。

    現在，當偵錯工具暫停上`Console.WriteLine`，您可以將滑鼠停留`theGalaxy.GalaxyType.MyGType`，並適當地設定值，請參閱。

1. 按一下左邊界中的中斷點圓圈，以移除中斷點 (或以滑鼠右鍵按一下並選擇 **中斷點** > **刪除中斷點**)，然後按下**F5**以繼續。

    應用程式執行，並顯示輸出。 它看起來很不錯，但您會發現一件事;您必須是顯示在主控台輸出中，異常 galaxy 為小型 Magellanic 雲端 galaxy，但它完全顯示沒有 galaxy 型別。

    ```
    Tadpole  400,  Spiral 
    Pinwheel  25,  Spiral 
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

1. 在這行程式碼中設定中斷點。

    ```csharp
    public GType(char type)
    ```

    此程式碼是其中設定 galaxy 型別，因此我們要仔細看看它。

1. 按一下 [**重新啟動**![重新啟動應用程式](../debugger/media/dbg-tour-restart.png "RestartApp")中偵錯] 工具列按鈕 (**Ctrl** + **Shift**  +  **F5**) 重新啟動。

    偵錯工具會暫停，您在其中設定中斷點的程式碼行上。  

1. 將滑鼠停留`type`變數。 您會看到值為`S`（依照字元碼）。 您感興趣的值`I`，因為您知道這是異常 galaxy 型別。

1. 按下**F5**並將滑鼠停留`type`變數一次。 重複此步驟，直到您看到的值`I`在`type`變數。

    ![檢查變數](../debugger/media/beginners-inspecting-data.png)

1. 現在，按下**F11** (**偵錯** > **逐步執行**或**逐步執行**中偵錯 工具列按鈕)。

    **F11**往前推進偵錯工具 （和執行程式碼） 一次一個陳述式。 **F10** (**不進入函式**) 是類似的命令，並學習如何使用偵錯工具時都非常有用。

1. 按下**F11**直到您停止中的程式碼行上`switch`'I' 的值的陳述式。 在這裡，您會看到清除問題所產生的錯字。 您所預期，前進到它的設定位置的程式碼`MyGType`為異常 galaxy 型別，但偵錯工具完全略過此程式碼而上暫停`default`一節`switch`陳述式。

    ![尋找打錯字](../debugger/media/beginners-typo.png)

    您查看程式碼，請參閱中的錯字`case 'l'`陳述式。 它應該是`case 'I'`。

1. 按一下 程式碼中`case 'l'`並將它取代為`case 'I'`。

1. 移除您的中斷點，然後按一下**重新啟動**按鈕以重新啟動應用程式。

    現在已修正的 bug，您會看到您預期的輸出 ！

    按任何鍵以完成應用程式。

## <a name="summary"></a>總結

當您看到問題時，使用 偵錯工具和[步驟命令](../debugger/navigating-through-code-with-the-debugger.md)這類**F10**和**F11**若要尋找與問題的程式碼區域。

> [!NOTE]
> 如果很難識別發生問題的程式碼區域前發生問題時，, 所執行的程式碼中設定中斷點，然後使用逐步執行命令，直到您看到此問題資訊清單。 您也可以使用[追蹤點](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)記錄訊息**輸出**視窗。 藉由查看記錄的訊息 （及注意哪些訊息還不會記錄 ！），您通常可以隔離的問題的程式碼區域。 您可能必須多次重複此程序，以縮小它。

當您發現的問題的程式碼區域時，請使用偵錯工具來調查。 若要尋找問題的原因，檢查問題的程式碼偵錯工具中執行您的應用程式時：

* [檢查變數](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)並檢查它們是否包含應該包含的值型別。 如果您發現不正確的值，找出不正確的值已設定的位置 (若要尋找的值設定的位置，您可能需要重新啟動偵錯工具，，看看[呼叫堆疊](../debugger/how-to-use-the-call-stack-window.md)，或兩者)。

* 請檢查您的應用程式是否正在執行您預期的程式碼。 （例如，在範例應用程式中，我們預期將 galaxy 類型為異常，switch 陳述式的程式碼但應用程式略過的程式碼，因為錯字）。

> [!TIP]
> 您可以使用偵錯工具可協助您找出 bug。 偵錯工具可以找出 bug*為您*只有當它知道您的程式碼的意圖。 如果您的開發人員，該意圖，工具可以只會知道您的程式碼的意圖。 撰寫[單元測試](../test/improve-code-quality.md)是做法。

## <a name="next-steps"></a>後續步驟

在本文中，您已了解幾個一般的偵錯概念。 接下來，您可以開始了解如何使用 Visual Studio 進行偵錯。

> [!div class="nextstepaction"]
> [偵錯工具功能導覽](../debugger/debugger-feature-tour.md)
