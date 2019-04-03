---
title: 在 UWP 應用程式中偵錯 HTML 和 CSS |Microsoft Docs
ms.date: 07/17/2018
ms.topic: conceptual
f1_keywords:
- VS.WebClient.DomExplorer
dev_langs:
- JavaScript
helpviewer_keywords:
- debugging, CSS
- debugging, HTML
- debugging, JavaScript [UWP apps]
- DOM Explorer [UWP apps]
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: dbd276751d8052f21d92e38a0e337f9c133edf2c
ms.sourcegitcommit: d4bea2867a4f0c3b044fd334a54407c0fe87f9e8
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58790026"
---
# <a name="debug-html-and-css-in-uwp-apps-in-visual-studio"></a>在 Visual Studio 中的 UWP 應用程式中偵錯 HTML 和 CSS

Visual Studio 針對 JavaScript 應用程式提供完整的偵錯體驗，所包含的功能對於 Internet Explorer 和 Visual Studio 開發人員而言是很熟悉的。 支援這些功能的 UWP 應用程式以及使用 Visual Studio Tools for Apache Cordova 建立的應用程式。

使用 DOM 檢查工具所提供的互動式偵錯模型，您可以檢視和修改呈現的 HTML 和 CSS 程式碼。 您可以這麼做，而不需要停止並重新開始偵錯工具。

如需其他 JavaScript 偵錯功能，例如使用 [JavaScript 主控台] 視窗，並設定中斷點，詳細資訊，請參閱[快速入門： 偵錯 JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md)並[偵錯在 Visual Studio 中的應用程式](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps)。

## <a name="InspectingDOM"></a> 檢查 Llive DOM
DOM 總管會顯示所呈現頁面的檢視，您可以使用 DOM 總管變更值並立即查看結果。 這讓您能測試變更，而不需要停止並重新開始偵錯工具。 當您以此方法與頁面互動時，專案中的原始程式碼並不會變更，因此當您找到所需的程式碼修正時，您可以對原始程式碼進行變更。

> [!TIP]
> 若要避免在對原始程式碼進行變更時停止再重新開始偵錯工具，您可以使用 [偵錯] 工具列上的 [重新整理 Windows 應用程式]  按鈕 (或按 F4)，重新整理應用程式。 如需詳細資訊，請參閱 <<c0> [ 重新整理應用程式 (JavaScript)](../debugger/refresh-an-app-javascript.md)。

您可將 DOM 總管用於：

- 巡覽 DOM 項目樹狀子結構，並檢查呈現的 HTML、CSS 和 JavaScript 程式碼。

- 動態編輯所呈現項目的屬性和 CSS 樣式，並立即看到結果。

- 檢查 CSS 樣式套用到頁面項目的情形，並追蹤已套用的規則。

  偵錯應用程式時，您通常需要在 DOM 總管中選取項目。 當您選取項目時，DOM 總管右邊索引標籤上的值會自動更新，以反映 DOM 總管中選取的項目。 這些索引標籤如下：[樣式] 、[計算] 、[配置] 。 UWP 應用程式也支援**事件**並**變更**索引標籤。 如需選取項目的詳細資訊，請參閱 [Selecting elements](#SelectingElements)。

> [!TIP]
> 如果 [DOM 總管] 視窗已關閉，選擇 [偵錯] > >  即可重新開啟。 此視窗只有在指令碼偵錯工作階段期間才會顯示。

在接下來的程序中，我們將會經歷使用 DOM 總管以互動方式偵錯應用程式的過程。 我們將建立一個使用 `FlipView` 控制項的應用程式，然後對它進行偵錯。 應用程式包含幾個錯誤。

> [!WARNING]
> 下列範例應用程式是 UWP 應用程式。 針對 Cordova 支援相同的功能，但應用程式會不同。

#### <a name="to-debug-by-inspecting-the-live-dom"></a>藉由檢查 Live DOM 偵錯

1. 在 Visual Studio 中建立新的方案，選擇**檔案** > **新專案**。

2. 選擇**JavaScript** > **Windows Universal**，然後選擇**WinJS 應用程式**。

3. 輸入專案的名稱，例如 `FlipViewApp`，然後選擇 [確定]  建立應用程式。

4. 在 index.html 的本文項目，新增此程式碼：

    ```html
    <div id="flipTemplate" data-win-control="WinJS.Binding.Template"
            style="display:none">
        <div class="fixedItem" >
            <img src="#" data-win-bind="src: flipImg" />
        </div>
    </div>
    <div id="fView" style="width:100px;height:100px"
        data-win-control="WinJS.UI.FlipView" data-win-options="{
        itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">
    </div>
    ```

5. 開啟 default.css 並新增下列 CSS：

    ```css
    #fView {
        background-color:#0094ff;
        height: 100%;
        width: 100%;
        margin: 25%;
    }
    ```

6. 以此段程式碼取代 default.js 中的程式碼：

    ```javascript
    (function () {
        "use strict";

        var app = WinJS.Application;
        var activation = Windows.ApplicationModel.Activation;

        var myData = [];
        for (var x = 0; x < 4; x++) {
            myData[x] = { flipImg: "/images/logo.png" }
        };

        var pages = new WinJS.Binding.List(myData, { proxy: true });

        app.onactivated = function (args) {
            if (args.detail.kind === activation.ActivationKind.launch) {
                if (args.detail.previousExecutionState !==
                activation.ApplicationExecutionState.terminated) {
                    // TODO: . . .
                } else {
                    // TODO: . . .
                }
                args.setPromise(WinJS.UI.processAll());

                updateImages();
            }
        };

        function updateImages() {

            pages.setAt(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
            pages.setAt(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });
            pages.setAt(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });
        };

        app.oncheckpoint = function (args) {
        };

        app.start();

        var publicMembers = {
            items: pages
        };

        WinJS.Namespace.define("Data", publicMembers);

    })();
    ```

    下圖顯示我們想要查看我們執行此應用程式。 但是，要讓應用程式變成這樣，我們必須先修正一些 Bug。

    ![顯示預期的結果的 FlipView 應用程式](../debugger/media/js_dom_appfixed.png "JS_DOM_AppFixed")

7. 選擇**本機電腦**下拉式清單中下一步**開始偵錯**按鈕**偵錯**工具列：

    ![選取偵錯目標清單](../debugger/media/js_select_target.png "JS_Select_Target")

8. 選擇 [JavaScript] **Emulator 8.1 WVGA 4 英吋 512MB** > **模擬器**，或按 F5，以偵錯模式執行您的應用程式。

    執行應用程式，不過您會看到主要是空白畫面，因為樣式有幾個 bug。 第一個 `FlipView` 影像出現在螢幕中央附近的小方形中。

9. 切換至 Visual Studio 並選擇 [ **DOM 總管** ] 索引標籤。

    > [!TIP]
    > 您可以按 Alt+Tab 或 F12，在 Visual Studio 和執行中應用程式之間切換。

10. 在 [DOM 總管] 視窗中，選取識別碼為 `"fView"`之區段的 DIV 項目。 使用方向鍵來檢視和選取正確的 DIV 項目 (向右鍵可讓您檢視元素的子系。)

    ![DOM Explorer](../debugger/media/js_dom_explorer.png "JS_DOM_Explorer")

    > [!TIP]
    > 您也可以在 [JavaScript 主控台] 視窗的左下角，於 >> 輸入提示下鍵入 `select(fView)`，然後按 ENTER 來選取 DIV 項目。

    在 [DOM 總管] 視窗右邊索引標籤上的值會自動更新，以反映 DOM 總管中的目前項目。

11. 選擇右邊的 [ **計算** ] 索引標籤。

    這個索引標籤顯示所選 DOM 項目之每個屬性的計算值 (或終值)。

12. 開啟高度 CSS 規則。 請注意，有內置樣式設定為 100px，這與為 `#fView` CSS 選取器設定的高度值 100% 不一致。 `#fView` 選取器的 Strikethrough 文字指出內嵌樣式的優先順序高於此樣式。

    下圖顯示 [計算]  索引標籤。

    ![DOM 總管計算 索引標籤](../debugger/media/js_dom_explorer_computed.png "JS_DOM_Explorer_Computed")

13. 在主要 [DOM 總管] 視窗中，按兩下 `fView` DIV 元素的高度和寬度內嵌樣式。 您現在可以在這裡編輯值。 在這個案例中，我們要完全移除它們。

14. 在主視窗中，按兩下`width: 100px;height: 100px;`，按下**刪除**鍵，，然後按**Enter**。 如果要在按下 Enter 之後，會立即反映新的值在應用程式，即使尚未停止偵錯工作階段。

    > [!IMPORTANT]
    > 您可以更新 [DOM 總管] 視窗中的屬性，也可以更新 [樣式] 、[計算] 和 [配置]  索引標籤中出現的值。 如需詳細資訊，請參閱 <<c0> [ 使用 DOM 總管偵錯 CSS 樣式](../debugger/debug-css-styles-using-dom-explorer.md)並[使用 DOM 總管偵錯配置](../debugger/debug-layout-using-dom-explorer.md)。

15. 選取它，或使用 Alt + Tab，切換至應用程式。

    現在 `FlipView` 控制項看起來比 [模擬器] 或 [Phone 模擬器] 的螢幕還大。 這不是預期的結果。 若要調查，請切換回 Visual Studio。

16. 在 [DOM 總管] 中，再選取 [ **計算** ] 索引標籤並開啟高度規則。 FView 項目仍然顯示值為 100%，如預期般的 css，但計算的值會等於應用程式的螢幕高度 (例如 800px 667.67 p x 或其他值)，這是不是我們想要為此應用程式。 若要調查，在下一個步驟中我們會移除的高度和寬度`fView`DIV 項目。

17. 在 [樣式]  索引標籤中，取消核取 `#fView` CSS 選取器的高度和寬度屬性。

    [ **計算** ] 索引標籤現在會顯示 400px 高度。 資訊表示這個值來自平台 CSS 檔案 ui-dark.css 中所指定的 .win-flipview 選取器。

18. 切換回應用程式。

    狀況隨即有所改善。 不過，仍有另外一個問題待修正，邊界太大。

19. 若要調查，請切換至 Visual Studio 並選擇 [配置] 索引標籤，查看元素的方塊模型。

    在 **版面配置**索引標籤上，您會看到下列訊息：

    - 255px (Offset) 和 255px (Margin) 或類似的值，視您的裝置解析度而定。

      下圖顯示如何**版面配置** 索引標籤看起來，如果您使用模擬器搭配 100px 位移和邊界)。

      ![DOM 總管配置 索引標籤](../debugger/media/js_dom_explorer_layout.png "JS_DOM_Explorer_Layout")

      這似乎不正確。 [ **計算** ] 索引標籤也會顯示相同的邊界值。

20. 選擇 [ **樣式** ] 索引標籤，尋找 `#fView` CSS 選取器。 您可以看到 **margin** 屬性的值為 25%。

21. 選取 25% 並將其變更為 25px，然後按 Enter。

22. 此外，在 [樣式]  索引標籤中，選擇 .win-flipview 選取器的高度規則，並將 400px 變更為 500px，然後按 Enter。

23. 切換回應用程式，您會看見項目定位已正確顯示。 若要在不停止並重新開始偵錯工具的情況下，修正原始碼並重新整理應用程式，請參閱下列程序。

#### <a name="to-refresh-your-app-while-debugging"></a>在偵錯時重新整理您的應用程式

1. 當應用程式仍在執行時，切換至 Visual Studio。

2. 開啟 default.html，將 `"fView"` DIV 元素的高度和寬度變更為 100%，修改您的原始程式碼。

3. 選擇 [偵錯] 工具列上的 [ **重新整理 Windows 應用程式** ] 按鈕 (或按 F4)。 按鈕看起來像這樣︰![重新整理 Windows 應用程式 按鈕](../debugger/media/js_refresh.png "JS_Refresh")。

    應用程式頁面會重新載入，模擬器或 Phone 模擬器會回到前景。

    如需重新整理功能的詳細資訊，請參閱[重新整理應用程式 (JavaScript)](../debugger/refresh-an-app-javascript.md)。

## <a name="SelectingElements"></a> Selecting elements
偵錯應用程式時，您可以使用三種方式選取 DOM 項目：

- 直接在 [DOM 總管] 視窗中按一下項目 (或使用方向鍵)。

- 使用 [ **選取元素** ] 按鈕 (Ctrl+B)。

- 使用  `select` 命令，此為其中一個 [JavaScript Console commands](../debugger/javascript-console-commands.md)。

  當您使用 [DOM 總管] 視窗選取項目，並將滑鼠指標放在項目上時，對應的項目會在執行的應用程式中反白顯示。 您必須在 [DOM 總管] 中按一下元素將它選取，或者也可以使用方向鍵來反白顯示及選取元素。此外，您還可以使用 [ **選取元素** ] 按鈕來選取 [DOM 總管] 中的元素。 下圖顯示 [ **選取項目** ] 按鈕。

  ![在 [DOM 總管] 中選取項目按鈕](../debugger/media/js_dom_select_element_button.png "JS_DOM_Select_Element_Button")

  按一下 [ **選取元素** ] (或按 Ctrl+B) 會變更選取模式，讓您可以在執行的應用程式中按一下元素，即可選取 [DOM 總管] 中的項目。 只要再按一下，就會回到一般選取模式。 按一下 [ **選取項目**] 時，應用程式會移至前景，而游標會改變以反映新的選取模式。 按一下加框項目時，DOM 總管會回到前景，並已選取所指定的項目。

  在您選擇 [選取項目] 之前，您可以透過切換 [針對在 DOM 樹狀目錄中選取的項目顯示網頁醒目提示方塊]  按鈕，指定是否要在執行中的應用程式內反白顯示該項目。 下圖顯示這個按鈕。 預設會顯示醒目提示。

  ![顯示網頁醒目提示按鈕](../debugger/media/js_dom_display_highlights_button.png "JS_DOM_Display_Highlights_Button")

  當您選擇要醒目提示項目時，只要在模擬器中將滑鼠停留在任何項目上方，該項目就會醒目提示。 已反白顯示之元素的色彩，會與顯示在 [DOM 總管] 之 [ **配置** ] 索引標籤中的方塊模型相符。

> [!NOTE]
> Windows Phone 模擬器僅部分支援藉由滑鼠游標停留來醒目提示示項目。

## <a name="see-also"></a>請參閱
- [在 Visual Studio 中偵錯應用程式](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps)
- [重新整理應用程式 (JavaScript)](../debugger/refresh-an-app-javascript.md)
- [偵錯 WebView 控制項](../debugger/debug-a-webview-control.md)
- [鍵盤快速鍵](../debugger/keyboard-shortcuts-html-and-javascript.md)
- [JavaScript 主控台命令](../debugger/javascript-console-commands.md)
- [偵錯 HTML、CSS 和 JavaScript 範例程式碼](../debugger/debug-html-css-and-javascript-sample-code.md)
- [產品支援和協助工具](https://msdn.microsoft.com/library/tzbxw1af(VS.120).aspx)
