---
title: 檢視 DOM 事件接聽程式 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9d6f5c913cb2868df1af25470eb69f84575ffab
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223297"
---
# <a name="view-dom-event-listeners"></a>檢視 DOM 事件接聽程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

適用於 Windows 和 Windows Phone] (../Image/windows_and_phone_content.png"windows_and_phone_content")  
  
 **事件**DOM 總管 索引標籤會顯示與 DOM 項目相關聯的事件。 中的每個最上層節點**事件**索引標籤各代表具有有效訂閱者的事件。 這個最上層節點包含表示特定事件之已登錄事件接聽程式的子節點。 除了檢視事件接聽程式，您還可以使用這個索引標籤巡覽至 JavaScript 程式碼中事件接聽程式的位置。 本主題中的資訊適用於使用 HTML 和 JavaScript 的市集應用程式。  
  
 上的清單**事件** 索引標籤上是動態的。 如果您在應用程式執行時加入事件接聽程式，則新事件接聽程式會在該處顯示。 如需加入及移除事件接聽程式的資訊，請參閱 <<c0> [ 解決問題的事件接聽程式的秘訣](#Tips)本主題中。  
  
> [!NOTE]
>  事件接聽程式的程式碼項目不是 DOM 項目，例如`xhr`，不會出現在**事件** 索引標籤。  
  
## <a name="view-event-listeners-for-dom-elements"></a>檢視 DOM 項目的事件接聽程式  
 此範例顯示 Windows Phone 市集應用程式。 Windows 市集應用程式也支援這裡說明的 [DOM 總管] 功能。  
  
#### <a name="to-view-event-listeners"></a>檢視事件接聽程式  
  
1.  在 Visual Studio 中，建立使用 Windows Phone 樞紐分析應用程式專案範本的 JavaScript 應用程式。  
  
2.  在 Visual Studio 中開啟範本中，選取**Emulator 8.1 WVGA 4 英吋 512MB**偵錯工具中的 [偵錯] 工具列的下拉式清單中：  
  
     ![選取偵錯目標](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")  
  
3.  請按 F5 以偵錯模式執行應用程式。  
  
4.  在執行中應用程式，移至**第 3 節**樞紐分析項目。  
  
5.  切換至 Visual Studio (Alt+Tab 或 F12)。  
  
6.  在 [DOM 總管] 中，選擇右上角的 `Find`。  
  
7.  輸入 `ListView`，然後按 Enter。  
  
8.  如果有必要，請選擇**下一步**按鈕來尋找`DIV`項目，表示`ListView`控制項 (這個項目具有`data-win-control`的值`WinJS.UI.ListView`)。  
  
     現在 [DOM 總管] 中的 `DIV` 項目應處於已選取的狀態。  
  
9. 選擇**事件**在 DOM 總管 右邊的窗格中的索引標籤。  
  
     您現在可以在這裡看到具有 `DIV` 項目有效訂閱者的事件。  
  
     ![[DOM 總管] 的 [事件] 索引標籤](../debugger/media/js-dom-events.png "JS_DOM_Events")  
  
10. 若要尋找這些事件的事件接聽程式，請選擇相關聯的 JavaScript 檔案連結。  
  
11. 若要快速識別 DOM 階層中父項目的事件接聽程式，請在 [DOM 總管] 底端的階層清單中選擇父項目。  
  
     ![選取 DOM 階層中的父項目](../debugger/media/js-dom-breadcrumbs.png "JS_DOM_Breadcrumbs")  
  
     **事件**索引標籤會顯示您的階層清單中選擇任何項目的事件接聽程式。  
  
###  <a name="Tips"></a> 解決問題的事件接聽程式的秘訣  
 在某些應用程式案例中，事件接聽程式必須明確地移除使用[removeEventListener](http://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx)。 使用**事件**在 DOM 總管 中，若要測試是否事件接聽程式已從 DOM 項目中執行程式碼時的索引標籤。 以下是一些協助解決這些類型之問題的秘訣：  
  
-   使用單頁瀏覽模型的應用程式，顯示在 Visual Studio 中實作。[專案範本](http://msdn.microsoft.com/library/windows/apps/hh758331.aspx)，不是通常需要移除註冊的 DOM 項目，屬於頁面等物件的事件接聽程式。 在此情況下，DOM 項目和其相關聯的事件接聽程式會有相同的存留期，而且可以對其進行記憶體回收。  
  
-   如果 DOM 項目或物件的存留期與相關聯的事件接聽程式不同，則可能需要呼叫 `removeEventListener` 方法。 例如，如果您使用 `window.onresize` 事件，則在離開您已處理該事件的頁面時，可能需要移除事件接聽程式。  
  
-   如果 `removeEventListener` 無法移除指定的接聽程式，可能是在物件的不同執行個體上進行呼叫。 您可以使用[bind 方法 （函式）](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/bind-method-function-javascript.md)方法來解決此問題，當您將新增接聽程式。  
  
-   若要移除事件接聽程式已加入使用其中一種[bind 方法 （函式）](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/bind-method-function-javascript.md)或藉由使用匿名函式，儲存加入接聽程式時的函式的執行個體。 以下是安全使用此模式的一種方式：  
  
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
  
-   如果使用 `removeEventListener` 屬性 (例如 `obj.on<eventname>`) 加入事件接聽程式，則無法使用 `window.onresize = handlerFunc` 移除事件接聽程式。  
  
-   使用 JavaScript 記憶體分析器[JavaScript 記憶體](../profiling/javascript-memory.md)應用程式中。 必須明確移除的事件接聽程式可能會顯示為記憶體流失。  
  
## <a name="see-also"></a>另請參閱  
 [快速入門： 偵錯 HTML 和 CSS](../debugger/quickstart-debug-html-and-css.md)   
 [偵錯使用 DOM 總管 中的 CSS 樣式](../debugger/debug-css-styles-using-dom-explorer.md)   
 [使用 DOM 總管偵錯配置](../debugger/debug-layout-using-dom-explorer.md)



