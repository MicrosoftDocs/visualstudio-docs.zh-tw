---
title: 適合完全初學者的程式碼偵錯
description: 如果您是第一次偵錯，了解一些準則可協助您使用 Visual Studio 在偵錯模式中執行應用程式
ms.date: 02/14/2020
ms.topic: tutorial
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6202fa019aed8e6fc9eb9ff93bdb390bf22f2911
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761247"
---
# <a name="how-to-debug-for-absolute-beginners"></a>完全初學者如何偵錯

我們以軟體開發人員身分所撰寫的程式碼，不一定總是會如預期般執行。 有時候，它會執行完全不同的功能！ 如果發生此情況，下一個工作是找出原因。雖然我們很想要直接盯著程式碼好幾個小時，但使用偵錯工具會更容易且更有效率。

不幸的是，偵錯工具並無法神奇地顯示程式碼中的所有問題或 Bug。 「偵錯」表示在 Visual Studio 之類的偵錯工具中逐步執行程式碼，以找出發生程式設計錯誤的確切位置。 您可以接著了解需要在程式碼中進行哪些修正，而偵錯工具通常可讓您暫時變更，以便繼續執行程式。

有效地使用偵錯工具也是需要時間和練習才能習得的技能，但這對所有軟體開發人員而言終究是基本工作。 在本文中，我們將介紹偵錯的核心準則，並提供協助您開始進行的祕訣。

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>藉由自我詢問正確的問題來釐清問題

這有助於釐清您遇到的問題，再嘗試進行修正。 想必您已在程式碼中遇到問題，否則您不會來到這裡想了解如何進行偵錯！ 因此，在您開始偵錯之前，請確定您已識別想要解決的問題：

* 您預期的程式碼功能為何？

* 實際發生什麼情況？

    如果您在執行應用程式時遇到錯誤 (例外狀況)，可能是件好事！ 例外狀況是執行程式碼時所遇到的非預期事件，通常是某種錯誤。 偵錯工具可帶您前往程式碼中發生例外狀況的確切位置，並可協助您調查可能的修正。

    如果發生其他問題，該問題的徵兆為何？ 您是否已懷疑程式碼中出現此問題？ 例如，如果您的程式碼顯示一些文字，但該文字不正確，則您知道可能是您的資料不正確，或設定顯示文字的程式碼發生某種 Bug。 藉由在偵錯工具中逐步執行程式碼，您可以檢查變數的每一項變更，探索指派不正確值的確切時間和方式。

## <a name="examine-your-assumptions"></a>檢查您的假設

在您調查 Bug 或錯誤之前，請考慮為預期特定結果所做的假設。 隱藏或未知的假設可能會妨礙識別問題，使您在偵錯工具中看到問題的真正原因而不自覺。 您的假設清單可能會有很長！ 以下是您可以自我詢問來挑戰假設的一些問題。

* 您是否使用正確的 API (也就是正確的物件、函式、方法或屬性)？ 您使用的 API 可能不會如預期般執行 (當您在偵錯工具中檢查 API 呼叫之後，您可能需要前往協助識別正確 API 的文件進行修正)。

* 您是否正確使用 API？ 您可能使用正確的 API，但使用它的方式不正確。

* 您的程式碼是否包含任何錯字？ 有些錯字 (例如簡單的變數名稱拼字錯誤) 可能難以察覺，尤其是以不需要在使用變數前進行宣告的語言工作時。

* 您是否對程式碼進行了一項變更，並假設它與您看到的問題無關？

* 您是否預期物件或變數包含特定值 (或特定類型的值)，但與實際發生情況不同？

* 您是否知道程式碼的意圖？ 通常很難對其他人的程式碼進行偵錯。 如果這不是您的程式碼，您可能需要花時間了解程式碼的確切功能，才能有效地進行偵錯。

    > [!TIP]
    > 撰寫程式碼時，請從少量且有效的程式碼開始  (良好的範例程式碼在此很有説明。 ) 有時可以更輕鬆地修正一組大型或複雜的程式碼，方法是從示範您嘗試達成的核心工作的一小段程式碼開始。 然後，您可以累加地修改或新增程式碼，並在每個位置測試錯誤。

藉由自我詢問假設，您可以縮短在程式碼中找出問題所需的時間。 您也可以縮短修正問題所需的時間。

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>在偵錯模式中逐步執行程式碼，以找出發生問題的位置

當您正常執行應用程式時，只有在程式碼完成執行之後，您才會看到錯誤和不正確的結果。 程式也可能會無預期地終止，而不告知原因。

在偵錯工具 (也稱為「偵錯模式」) 中執行應用程式，表示偵錯工具會在程式執行時主動監視發生的所有情況。 它也可讓您在任何位置暫停應用程式以檢查其狀態，然後逐行執行程式碼，以監看發生的所有詳細資料。

在 Visual Studio 中，您可以使用 **F5** (或 [偵錯工具  >  **開始調試** 程式] 命令，或在偵錯工具列) 中 **啟動調試** 程式按鈕 ![開始調試](../debugger/media/dbg-tour-start-debugging.png "[偵錯]")程式，進入偵錯工具模式。 如果發生任何例外狀況，Visual Studio 的例外狀況協助程式會帶您前往發生例外狀況的確切位置，並提供其他實用的資訊。 如需如何在程式碼中處理例外狀況的詳細資訊，請參閱[偵錯技術和工具](../debugger/write-better-code-with-visual-studio.md)。

如果您未收到例外狀況，您可能知道要到程式碼中的何處尋找問題。 這是您搭配偵錯工具使用「中斷點」的位置，讓您有機會更仔細地檢查程式碼。 中斷點是可靠偵錯最基本也最重要的功能。 中斷點會指出 Visual Studio 應暫停程式碼執行的地方，如此一來您可以查看變數的值、記憶體的行為，或程式碼執行的順序。

在 Visual Studio 中，您可以按一下程式碼行旁的左邊界，快速設定中斷點。 或是將游標放在該行，然後按 **F9** 鍵。

為了協助說明這些概念，我們將引導您進行已含數個 Bug 的一些範例程式碼。 我們將使用 C#，但這些偵錯工能也適用於 Visual Basic、C++、JavaScript、Python 及其他支援的語言。

### <a name="create-a-sample-app-with-some-bugs"></a>建立範例應用程式 (內含一些 Bug)

接下來，我們將建立內含一些 Bug 的應用程式。

1. 您必須安裝 Visual Studio，以及安裝 **.net 桌面開發** 工作負載或 **.net Core 跨平臺開發** 工作負載（視您想要建立的應用程式類型而定）。

    如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)頁面免費進行安裝。

    如果您需要安裝工作負載，但已有 Visual Studio，請按一下 [**工具**  >  **取得工具及功能**]。 Visual Studio 安裝程式即會啟動。 選擇 [ **.net 桌面開發** (] 或 [ **.net Core 跨平臺開發** ]) 工作負載，然後選擇 [ **修改**]。

1. 開啟 Visual Studio。

    ::: moniker range=">=vs-2019"
    在 [開始] 視窗中，選擇 [ **建立新專案**]。 在搜尋方塊中輸入 **主控台** ，然後選擇 **主控台應用程式 ( .net Core)** 或 **主控台應用程式 ( .NET Framework)**。 選擇 [下一步]。 鍵入例如 **ConsoleApp-FirstApp** 的專案名稱，然後按一下 [建立]。
    ::: moniker-end
    ::: moniker range="vs-2017"
    從頂端功能表列中 **，選擇 [** 檔案  >  **新增**  >  **專案**]。 在 [新專案] 對話方塊的左窗格中，於 [Visual C#] 下選擇 [主控台應用程式]，然後在中間的窗格中選擇 [主控台應用程式 (.NET Framework)] 或 [主控台應用程式 (.NET Core)]。 鍵入像 **ConsoleApp-FirstApp** 的名稱，並按一下 [確定]。
    ::: moniker-end

    如未看到 **主控台應用程式 (.NET Framework)** 或 **主控台應用程式 (.NET Core)** 專案範本，請前往 [工具] > [取得工具與功能] 來開啟 Visual Studio 安裝程式。 選擇 **.Net Core 跨平臺開發** 或 **.net 桌面開發** 工作負載，然後選擇 [ **修改**]。

    Visual Studio 隨即建立主控台專案，並出現在右窗格的 [方案總管] 中。

1. 在 *Program.cs* 中，將所有預設程式碼取代為下列程式碼：

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

    此程式碼的意圖為銀河名稱、與銀河的距離及銀河類型，全部都顯示在一份清單中。 為了進行偵錯，請務必了解程式碼的意圖。 以下是下列輸出所要顯示之清單中的單行格式：

    *銀河名稱*, *距離*, *銀河類型*。

### <a name="run-the-app"></a>執行應用程式

1. 在 [程式碼編輯器] 上方的偵錯工具工具列中，按下 **F5** 或 [ **開始調試** 程式] 按鈕 ![開始調試](../debugger/media/dbg-tour-start-debugging.png "[偵錯]") 程式。

    應用程式隨即啟動，而且偵錯工具不會顯示任何例外狀況。 不過，您在主控台視窗中看到的輸出不符合預期。 以下是預期的輸出：

    ```
    Tadpole  400,  Spiral
    Pinwheel  25,  Spiral
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    但輸出如下：

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType
    Pinwheel  25,  ConsoleApp_FirstApp.GType
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    查看輸出及我們的程式碼，我們知道 `GType` 是儲存銀河類型的類別名稱。 我們想要顯示實際的銀河類型 (例如 "Spiral")，而不是類別名稱！

### <a name="debug-the-app"></a>偵錯應用程式

1. 在應用程式仍在執行時，按一下此程式碼行中 `Console.WriteLine` 方法呼叫旁的左邊界來設定中斷點。

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }
    ```

    當您設定中斷點時，左邊界會出現紅點。

    由於我們在輸出中看到問題，因此我們將在偵錯工具中查看設定輸出的上述程式碼來開始偵錯。

1. 按一下偵錯工具列中的 [**重新** 啟動 ![重新開機應用程式](../debugger/media/dbg-tour-restart.png ">restartapp")] 按鈕， (**Ctrl**  +  **Shift**  +  **F5**) 。

    應用程式會在您設定的中斷點處暫停。 黃色醒目提示指出偵錯工具的暫停位置 (黃色程式碼行尚未執行)。

1. 將滑鼠游標移至右邊的 `GalaxyType` 變數上方，然後移至左邊的扳手圖示上方，展開 `theGalaxy.GalaxyType`。 您會看到 `GalaxyType` 包含 `MyGType` 屬性，且該屬性值已設定為 `Spiral`。

    ![Visual Studio 偵錯工具的螢幕擷取畫面，其中包含黃色的程式碼，以及在行尾的 theGalaxy. GalaxyType 屬性下方展開的功能表。](../debugger/media/beginners-inspect-variable.png)

    "Spiral" 實際上是您預期列印至主控台的正確值！ 因此，這是一個不錯的起點，您可以在執行應用程式時存取這段程式碼中的這個值。 在此案例中，我們將使用不正確的 API。 我們將了解是否可以在偵錯工具中執行程式碼時修正此問題。

1. 當您仍在偵錯時，將游標放在相同程式碼中的 `theGalaxy.GalaxyType` 結尾處，然後將它變更為 `theGalaxy.GalaxyType.MyGType`。 雖然您可以進行這項變更，但程式碼編輯器會顯示錯誤，指出無法編譯此程式碼。

    ![Visual Studio 偵錯工具的螢幕擷取畫面，其中包含以紅色醒目提示的程式程式碼，以及已選取 [編輯] 按鈕的 [編輯後繼續] 訊息方塊。](../debugger/media/beginners-edit.png)

1. 在 [編輯後繼續] 訊息方塊中，按一下 [編輯]。 您現在會在 [錯誤清單] 視窗中看到錯誤訊息。 錯誤指出 `'object'` 不包含 `MyGType` 的定義。

    ![Visual Studio 偵錯工具的螢幕擷取畫面，其中包含以紅色醒目提示的程式程式碼，以及列出兩個錯誤的 [錯誤清單] 視窗。](../debugger/media/beginners-no-definition.png)

    雖然我們使用 `GType` 類型物件 (具有 `MyGType` 屬性) 設定每個銀河，但偵錯工具不會將 `theGalaxy` 物件視為 `GType` 類型物件。 這是怎麼一回事？ 您想要仔細檢查設定銀河類型的任何程式碼。 當您這樣做時，您會看到 `GType` 類別確實具有 `MyGType` 屬性，但有些不對勁。 `object` 的相關錯誤訊息是條線索；對於語言解譯器，類型會顯示為 `object` 類型物件，而不是 `GType` 類型物件。

1. 仔細檢查與設定銀河類型相關的程式碼，您會發現 `Galaxy` 類別的 `GalaxyType` 屬性已指定為 `object`，而不是 `GType`。

    ```csharp
    public object GalaxyType { get; set; }
    ```

1. 將上述程式碼變更為：

    ```csharp
    public GType GalaxyType { get; set; }
    ```

1. 按一下偵錯工具列中的 [**重新** 啟動 ![重新開機應用程式](../debugger/media/dbg-tour-restart.png ">restartapp")] 按鈕 (**Ctrl**  +  **Shift**  +  **F5**) 重新編譯程式碼並重新啟動。

    現在，當偵錯工具在 `Console.WriteLine` 上暫停時，您可以將滑鼠游標移至 `theGalaxy.GalaxyType.MyGType` 上方，並看到值已正確設定。

1. 若要移除中斷點，請按一下左邊界中的中斷點圓圈 (或按一下滑鼠右鍵並選擇 [**中斷點**  >  **刪除中斷點**) ]，然後按 **F5** 鍵繼續。

    應用程式隨即執行並顯示輸出。 現在看起來相當不錯，但您注意到一點：您預期小麥哲倫星系在主控台輸出中顯示為不規則銀河，但卻完全顯示為沒有銀河類型。

    ```
    Tadpole  400,  Spiral
    Pinwheel  25,  Spiral
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

1. 在此程式碼行上設定中斷點。

    ```csharp
    public GType(char type)
    ```

    此程式碼是設定銀河類型的位置，因此我們想要進一步查看。

1. 按一下偵錯工具列中的 [**重新** 啟動 ![重新開機應用程式](../debugger/media/dbg-tour-restart.png ">restartapp")] 按鈕 (**Ctrl**  +  **Shift**  +  **F5**) 重新開機。

    偵錯工具會在您設定中斷點的程式碼行上暫停。

1. 將滑鼠游標移至 `type` 變數上方。 您會看到 `S` 值 (後面接著字元碼)。 您對 `I` 值感興趣，因為您知道這是不規則的銀河類型。

1. 按 **F5** 鍵，並再次將滑鼠游標移至 `type` 變數上方。 重複此步驟，直到您在 `type` 變數中看到 `I` 值。

    ![Visual Studio 偵錯工具的螢幕擷取畫面，其中包含以黃色顯示的程式程式碼，以及一個小視窗，其中顯示類型變數的值為 73 ' I '。](../debugger/media/beginners-inspecting-data.png)

1. 現在，按 **F11** 鍵 ([偵錯] > [逐步執行] 或偵錯工具列中的 [逐步執行] 按鈕)。

    **F11** 鍵會將偵錯工具一次往前推進一個陳述式 (並執行程式碼)。 **F10** (**不進入函式**) 是類似的命令，這兩者對於了解如何使用偵錯工具都非常有用。

1. 按 **F11** 鍵，直到停在 `switch` 陳述式中值為 'I' 的程式碼行。 在這裡，您會看到問題很明顯是由於錯字所造成。 您預期程式碼往前推進到 `MyGType` 設定為不規則銀河類型的位置，但偵錯工具卻完全略過此程式碼，並於 `switch` 陳述式的 `default` 區段上暫停。

    ![尋找錯字](../debugger/media/beginners-typo.png)

    看一下程式碼，您會在 `case 'l'` 陳述式中看到錯字。 此屬性應該是 `case 'I'`。

1. 按一下程式碼中的 `case 'l'`，然後以 `case 'I'` 取代。

1. 移除您的中斷點，然後按一下 [重新啟動] 按鈕以重新啟動應用程式。

    現在已修正 Bug，您會看到預期的輸出！

    按任意鍵完成應用程式。

## <a name="summary"></a>總結

當您看到問題時，請使用偵錯工具和 [步驟命令](../debugger/navigating-through-code-with-the-debugger.md) (例如 **F10** 和 **F11**)，以找出有問題的程式碼區域。

> [!NOTE]
> 如果很難識別發生問題的程式碼區域，請在所執行程式碼中設定發生問題前的中斷點，然後使用步驟命令，直到您看到問題資訊清單。 您也可以使用[追蹤點](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)將訊息記錄至 [輸出] 視窗。 藉由查看記錄的訊息 (及注意哪些訊息尚未記錄)，您通常可以隔離有問題的程式碼區域。 您可能必須重複此程序幾次，以縮小範圍。

當您發現有問題的程式碼區域時，請使用偵錯工具進行調查。 若要找出問題的原因，請在偵錯工具中執行您的應用程式時檢查問題程式碼：

* [檢查變數](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)，並檢查其是否包含應包含的值類型。 如果您發現不正確的值，請找出設定不正確值的位置 (若要尋找設定值的位置，您可能需要重新啟動偵錯工具及/或查看[呼叫堆疊](../debugger/how-to-use-the-call-stack-window.md))。

* 檢查您的應用程式是否正在執行您所預期程式碼。 (例如，在範例應用程式中，我們預期 switch 陳述式的程式碼將銀河類型設定為不規則，但由於錯字，應用程式已略過該程式碼。)

> [!TIP]
> 您可以使用偵錯工具協助找出 Bug。 偵錯工具只有在知道您程式碼的意圖時，才可「為您」找出 Bug。 您身為開發人員必須表示程式碼的意圖，工具才能知道該意圖。 您可以撰寫[單元測試](../test/improve-code-quality.md)來執行這項作業。

## <a name="next-steps"></a>後續步驟

在本文中，您已了解幾個一般偵錯概念。 接下來，您可以開始深入了解偵錯工具。

> [!div class="nextstepaction"]
> [偵錯工具簡介](../debugger/debugger-feature-tour.md)
