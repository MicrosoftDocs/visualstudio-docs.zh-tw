---
title: 視圖 DOM 事件接聽程式 |Microsoft Docs
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
- DOM events, viewing [Windows Store apps]
- event listeners, viewing [Windows Store apps]
ms.assetid: d5b679e7-87dd-4cec-9176-883db6ff0781
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 64d4892080aaf0cf04e4b208b1a0bdb7a7a4480d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65693579"
---
# <a name="view-dom-event-listeners"></a>檢視 DOM 事件接聽程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

適用于 Windows 和 Windows Phone] (。/Image/windows_and_phone_content.png "windows_and_phone_content" ) 

 DOM 總管的 [ **事件** ] 索引標籤會顯示與 DOM 元素相關聯的事件。 [ **事件** ] 索引標籤中的每個最上層節點都代表具有作用中訂閱者的事件。 這個最上層節點包含表示特定事件之已登錄事件接聽程式的子節點。 除了檢視事件接聽程式，您還可以使用這個索引標籤巡覽至 JavaScript 程式碼中事件接聽程式的位置。 本主題中的資訊適用於使用 HTML 和 JavaScript 的市集應用程式。

 [ **事件** ] 索引標籤上的清單是動態的。 如果您在應用程式執行時加入事件接聽程式，則新事件接聽程式會在該處顯示。 如需新增和移除事件接聽程式的詳細資訊，請參閱本主題中 [解決事件接聽程式問題的秘訣](#Tips) 。

> [!NOTE]
> 不是 DOM 專案的程式碼專案（例如）的事件接聽程式 `xhr` 不會出現在 [ **事件** ] 索引標籤上。

## <a name="view-event-listeners-for-dom-elements"></a>檢視 DOM 項目的事件接聽程式
 此範例顯示 Windows Phone 市集應用程式。 Windows 市集應用程式也支援這裡說明的 [DOM 總管] 功能。

#### <a name="to-view-event-listeners"></a>檢視事件接聽程式

1. 在 Visual Studio 中，建立使用 Windows Phone 樞紐分析應用程式專案範本的 JavaScript 應用程式。

2. 在 Visual Studio 中開啟範本時，請在偵錯工具的 [偵錯工具] 工具列的下拉式清單中選取 [ **模擬器 8.1 WVGA 4 英吋 512mb** ]：

     ![選取偵錯目標](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")

3. 請按 F5 以偵錯模式執行應用程式。

4. 在正在執行的應用程式中，移至 **第3節** 的資料透視專案。

5. 切換至 Visual Studio (Alt+Tab 或 F12)。

6. 在 [DOM 總管] 中，選擇右上角的 `Find`。

7. 輸入 `ListView`，然後按 Enter。

8. 如有必要，請選擇 [ **下一步]** 按鈕尋找 `DIV` 代表 `ListView` 控制項的元素 (此專案的 `data-win-control` 值為 `WinJS.UI.ListView`) 。

     現在 [DOM 總管] 中的 `DIV` 項目應處於已選取的狀態。

9. 在 DOM 總管右邊的窗格中，選擇 [ **事件** ] 索引標籤。

     您現在可以在這裡看到具有 `DIV` 項目有效訂閱者的事件。

     ![[DOM 總管] 的 [事件] 索引標籤](../debugger/media/js-dom-events.png "JS_DOM_Events")

10. 若要尋找這些事件的事件接聽程式，請選擇相關聯的 JavaScript 檔案連結。

11. 若要快速識別 DOM 階層中父項目的事件接聽程式，請在 [DOM 總管] 底端的階層清單中選擇父項目。

     ![選取 DOM 階層中的父元素](../debugger/media/js-dom-breadcrumbs.png "JS_DOM_Breadcrumbs")

     [ **事件** ] 索引標籤會顯示您在 [階層] 清單中所選擇之任何元素的事件接聽程式。

### <a name="tips-for-resolving-issues-with-event-listeners"></a><a name="Tips"></a> 解決事件接聽程式問題的秘訣
 在某些應用程式案例中，必須使用 [removeEventListener](https://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx)來明確移除事件接聽程式。 使用 DOM 總管中的 [ **事件** ] 索引標籤，測試是否已在執行程式碼時從 DOM 元素移除事件接聽程式。 以下是一些協助解決這些類型之問題的秘訣：

- 針對使用在 Visual Studio [專案範本](https://msdn.microsoft.com/library/windows/apps/hh758331.aspx)中執行的單頁流覽模型的應用程式，通常不需要移除為物件所註冊的事件接聽程式，例如屬於頁面一部分的 DOM 元素。 在此情況下，DOM 項目和其相關聯的事件接聽程式會有相同的存留期，而且可以對其進行記憶體回收。

- 如果 DOM 項目或物件的存留期與相關聯的事件接聽程式不同，則可能需要呼叫 `removeEventListener` 方法。 例如，如果您使用 `window.onresize` 事件，則在離開您已處理該事件的頁面時，可能需要移除事件接聽程式。

- 如果 `removeEventListener` 無法移除指定的接聽程式，可能是在物件的不同執行個體上進行呼叫。 當您新增接聽程式時，可以使用 [Bind 方法 (](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) 函式) 方法來解決此問題。

- 若要移除使用 [Bind 方法 (](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) 函式) 或使用匿名函式加入的事件接聽程式，請在新增接聽程式時儲存函式的實例。 以下是安全使用此模式的一種方式：

    ```javascript
    // You could use the following code within the constructor function of an object, or
    // in the ready function of a PageControl object (Store app).
    this.storedHandler = this._handlerFunc.bind(this);
    elem.addEventListener('mouseup', this.storedHandler);

    // In this example, add the following code in the PageControl object's unload function.
    elem.removeEventListener('mouseup', this.storedHandler);

    ```

     如果您使用下列程式碼，而不是儲存繫結函式的參考，則無法明確地移除事件接聽程式：

    ```javascript
    // Avoid this pattern. No reference to the bound function is available.
    elem.addEventListener('mouseup', this._handlerFunc.bind(this));
    ```

- 如果使用 `removeEventListener` 屬性 (例如 `obj.on<eventname>`) 加入事件接聽程式，則無法使用 `window.onresize = handlerFunc` 移除事件接聽程式。

- 使用 JavaScript 記憶體分析器，在您的應用程式中使用 [JAVAscript 記憶體](../profiling/javascript-memory.md) 。 必須明確移除的事件接聽程式可能會顯示為記憶體流失。

## <a name="see-also"></a>另請參閱

- [快速入門：偵錯 HTML 和 CSS](../debugger/quickstart-debug-html-and-css.md)
- [使用 DOM 總管偵錯 CSS 樣式](../debugger/debug-css-styles-using-dom-explorer.md)
- [使用 DOM 總管偵錯配置](../debugger/debug-layout-using-dom-explorer.md)