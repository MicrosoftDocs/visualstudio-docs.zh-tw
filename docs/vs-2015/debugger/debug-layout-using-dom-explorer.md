---
title: 使用 DOM 總管偵錯配置 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- box model [Windows Store apps], viewing
- debugging layout [Windows Store apps]
- layout, debugging [Windows Store apps]
ms.assetid: ded6566d-fc29-49a7-8029-dee8e50fe733
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8b9d0d2a3250785e5ff60d65a6bf1264892c6f98
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434124"
---
# <a name="debug-layout-using-dom-explorer"></a>使用 DOM 總管偵錯配置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

適用於 Windows 和 Windows Phone] (../Image/windows_and_phone_content.png"windows_and_phone_content")  
  
 **版面配置** 索引標籤的 [DOM 總管] 中顯示[CSS 方塊模型](http://go.microsoft.com/fwlink/?LinkID=238778)中選取的項目[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]應用程式、 Windows Phone 市集應用程式或使用 Visual Studio Tools for Apache Cordova 建立應用程式。 您可以使用此方塊模型的視覺表示方式，辨識和修改可影響項目外觀且與配置有關的值。  
  
> [!TIP]
> 您在 [配置]  索引標籤中所做的變更並非永久變更。 您可以對原始程式碼進行永久變更，然後使用 [偵錯] 工具列上的 [重新整理 Windows App]  按鈕 (僅限 Windows 市集和 Windows Phone 市集 App) 重新整理 App。 如此一來，就不必重新啟動偵錯工具。  
  
 若要使用 DOM 總管 中修改的配置不會顯示在方塊模型的部分，請參閱[快速入門：偵錯 HTML 和 CSS](../debugger/quickstart-debug-html-and-css.md)並[使用 DOM 總管偵錯 CSS 樣式](../debugger/debug-css-styles-using-dom-explorer.md)。  
  
## <a name="example-of-fixing-a-layout-issue"></a>配置問題修正範例  
 此範例顯示如何選取中樞/樞紐分析範本中的清單項目，並解譯在 [配置]  索引標籤上的方塊模型值，然後變更其中一個屬性值來修正配置問題。  
  
#### <a name="to-fix-the-layout-issue"></a>修正配置問題  
  
1. 在 Visual Studio 中，建立使用中樞/樞紐分析專案範本的新市集 App。  
  
2. 在 shared pages\hub 資料夾中，開啟 hub.css。  
  
3. 將下列 CSS 程式碼：  
  
    ```css  
    .hubpage .hub .section4 .sub-image-row img {  
        height: 95px;  
        width: 130px;  
    }  
    ```  
  
     取代為下列 CSS 程式碼：  
  
    ```css  
    .hubpage .hub .section4 .sub-image-row img {  
        height: 95px;  
        width: 130px;  
        margin-left: 5em;  
    }  
    ```  
  
4. 在 [方案總管] 中選取 appName.WindowsPhone 專案或 appName.Windows 專案，然後從專案的捷徑功能表中選擇 [設定為啟始專案]  。  
  
5. 根據您的啟始專案，在 [偵錯] 工具列的下拉式清單中選擇 [Emulator 8.1 WVGA 4 英吋 512MB]  或 [模擬器]  ([本機電腦] 是預設值)。  
  
     ![選取偵錯目標](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")  
  
6. 請按 F5 以偵錯模式執行應用程式。  
  
7. 透過捲動或撥動開啟區段 4。  
  
    > [!TIP]
    > 將 Phone 模擬器放在 Visual Studio 視窗旁邊，以便立即查看您選取的結果，以及對 CSS 樣式所做的變更。  
  
     載入區段 4 時，您可以看到較低的影像看起來不太對。 每個項目影像像是切成兩個半 (而且左半邊不見了)。  
  
8. 切換至 Visual Studio，並選擇 [DOM 總管] 中的 [選取項目]  (或按 Ctrl+B)。 這樣會變更選取模式，讓您按一下就能選取項目，並且將 App 放置到前景。 按一下，這個模式就會還原。  
  
    > [!TIP]
    > 您也可以使用方向鍵或其他方法，直接在 [DOM 總管] 中選取 HTML 項目。 如需選取項目的詳細資訊，請參閱[快速入門：偵錯 HTML 和 CSS](../debugger/quickstart-debug-html-and-css.md)。  
  
9. 在 Phone 模擬器中，選取被剪掉一半的其中一個影像的灰色右半部。 反白顯示選取的項目 (在 Windows Phone 模擬器中，如下所示)：  
  
     ![選取 DOM 項目](../debugger/media/js-css-layout-select.png "JS_CSS_Layout_Select")  
  
    > [!TIP]
    > 模擬器支援將滑鼠游標停留在項目上方，以在選取 DOM 項目之前反白顯示 DOM 項目周圍的方塊。 Windows Phone 模擬器不支援這項作業。  
  
     當您選取 DOM 項目時，[DOM 總管] 會自動在 Visual Studio 中選取對應的 IMG 項目。 在 [DOM 總管] 中選取的項目如下所示：  
  
    ```html  
    <img src="ms-appx://guid/images/gray.png>   
    </img>  
    ```  
  
10. 按一下 [配置]  索引標籤。此索引標籤會顯示所選項目的方塊模型 (在 Windows Phone 模擬器中，如下所示)。  
  
     ![DOM 總管 的 [配置] 索引標籤](../debugger/media/js-css-layout.png "JS_CSS_Layout")  
  
     此檢視提供關於項目的一些有用資訊：  
  
    - 色彩會對應至滑鼠游標停留在模擬器中項目上方時出現的反白顯示外框。 藍色表示\<i m g > 項目維度。 黃褐色表示邊界值。  
  
    - 左邊界 (margin-left) 已設定，這提示了問題的原因，因為這個情況符合徵兆 (影像左側呈現黑色)。  
  
    - 顯示 0 像素值的方塊 (例如 [框線] 和 [與邊框距離])，表示可能未正確設定對應的 CSS 屬性。  
  
11. 若要得知如何套用 margin-left 規則，請選擇 [計算]  索引標籤，然後查看 margin-left 規則底下的內容。 您可以看到此規則已設定 5em 值，但是計算值為 66.66px 或 146.66px (視您的目標裝置而定)。  
  
    > [!TIP]
    > **計算**索引標籤會顯示 margin-left 規則設定`..hubpage .hub. section4 .sub-image-row img`CSS 選取器中 hub.css。 在本示範應用程式中，這就是您需要修正的位置。  
  
     您也可以使用 [配置]  索引標籤來測試修改配置值的結果。  
  
12. 在 [配置]  索引標籤中，選擇 [邊界]  方塊左側的 [66.66] 或 [146.66]  。  
  
13. 輸入 `0` ，然後按 Enter (您也可以使用向上和向下鍵來變更值)。  
  
14. 選取 其他\<i m g > 項目，在 DOM 總管 並變更其 margin-left 值為 0。  
  
15. 切換至 Phone 模擬器 (Emulator) 或模擬器 (Simulator)。 更新過的 margin-left 值已套用至區段 4 影像。 margin-left 規則下 [計算]  索引標籤的這些值也會一併更新。  
  
## <a name="see-also"></a>另請參閱  
 [快速入門：對 HTML 和 CSS 進行偵錯](../debugger/quickstart-debug-html-and-css.md)   
 [偵錯使用 DOM 總管 中的 CSS 樣式](../debugger/debug-css-styles-using-dom-explorer.md)   
 [檢視 DOM 事件接聽程式](../debugger/view-dom-event-listeners.md)
