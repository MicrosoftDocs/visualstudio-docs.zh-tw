---
title: "在網頁上顯示文字 (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript, write
- JavaScript, writing text
ms.assetid: 3c2455e7-2402-45f2-9545-77a2b2490527
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: a8c9ea9d0e0300a0d9b71b0b33d7c99c9ac3935c
ms.contentlocale: zh-tw
ms.lasthandoff: 08/11/2017

---
# <a name="displaying-text-in-a-webpage-javascript"></a>在網頁上顯示文字 (JavaScript)
有許多方法可在網頁上顯示文字。 各有優缺點，且支援特定用途。  
  
## <a name="displaying-text"></a>顯示文字  
  
-   建議的文字顯示方法是建立一個項目，然後寫入其 textContent 屬性。  
  
    ```JavaScript  
    <div id="textDiv"></div>  
    <script type="text/javascript">  
        var div = document.getElementById("textDiv");  
        div.textContent = "my text";  
        var text = div.textContent;  
    </script>  
    ```  
  
     在這個範例中，`text` 的值為 "my text"。 不過，透過在父節點上取得或設定 `textContent` 屬性所產生的值可能會包含節點子系的文字內容。 下面範例顯示子節點上所設定的 `textContent` 是包含在父節點的 `textContent` 值中：  
  
    ```JavaScript  
    <div id="textDiv">  
        <div id="nested"></div>  
    </div>  
    <script type="text/javascript">  
        var div = document.getElementById("textDiv");  
        var nestedDiv = document.getElementById("nested");  
        nestedDiv.textContent = "nested";  
  
        var text = "[" + div.textContent + "]";  
    </script>  
    ```  
  
     在這個範例中，`text` 的值為 "[nested]"。  
  
-   您也可以建立項目，並寫入其 [innerHTML](http://msdn.microsoft.com/library/ie/ms533897\(v=vs.85\).aspx) 或 [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) 屬性。 設定這些屬性只會影響元素本身中的文字，而不會影響其子系。 不過，這些屬性也有一些缺點：  
  
    -   [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) 屬性並不適用於所有瀏覽器，因此基於相容性的原因，您可能不想要使用它。  
  
    -   [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) 屬性會受到 CSS 樣式的影響，如果項目是隱藏狀態，則不會顯示此屬性。  
  
    -   [innerHTML](http://msdn.microsoft.com/library/ie/ms533897\(v=vs.85\).aspx) 屬性會取得和設定巢狀節點和文字。 如果未受保護，則可能被用來執行指令碼插入式攻擊。 此外，若將它設為沒有 HTML 標記的文字，則會移除所有先前設定的節點。  
  
-   您可以使用 `document.write` 方法，而不需建立元素。 不過，使用這個方法會造成整個網頁被清除，這可能不是您要的結果。  
  
     下面範例會示範使用 `document.write` 的其中一個缺點。 此指令碼原本是要每隔 5 秒鐘就顯示一次時間，但它卻只顯示兩次時間。 第二次呼叫 `document.write` 時，頁面已完成載入， `document.write` 會接著清除整個頁面 (它會呼叫 `document.open`)。 此時，`ShowTime` 函式不再存在。  
  
    ```html  
    <!DOCTYPE html>  
    <html>  
    <head>  
    <script type="text/javascript">  
        function ShowTime()  
        {  
            var dt = new Date();  
            document.write(dt.toTimeString());  
            // var elem = document.getElementById("divElem");  
            // elem.textContent = dt.toTimeString();  
            window.setTimeout("ShowTime();", 5000);  
        }  
    </script>  
    </head>  
  
    <body>  
    <script type="text/javascript">  
        ShowTime();  
    </script>  
    <div id="myDiv"></div>  
    </body>  
    </html>  
  
    ```  
  
     若要修正上述程式碼，移除包含 `document.write` 的程式碼行並取消註解後面兩行已標記註解的程式碼。  
  
-   您也可以使用 `alert``prompt` 或 `confirm` 函式，在快顯視窗中顯示訊息。 在大部分情況下，在 Web 瀏覽器中使用快顯視窗並不是很好的做法。 現今大部分瀏覽器都會設定為自動封鎖快顯視窗，因此可能看不到您的訊息。 此外，當您使用快顯視窗時，可能會進入無限迴圈，讓使用者無法以一般方式關閉網頁。
