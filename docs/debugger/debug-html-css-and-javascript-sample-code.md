---
title: Debug HTML 和 CSS 範例程式碼 |Microsoft Docs
description: 尋找搭配快速入門偵錯工具使用的 HTML 和 CSS 範例程式碼。 本文章中已修正設計快速入門中出現的錯誤。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 51893967-98c8-4141-ba40-03646f221760
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 14d071d4ab47efd60aa31ecbffe1d7cb873ac6fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865601"
---
# <a name="debug-html-and-css-sample-code"></a>對 HTML 和 CSS 範例程式碼進行偵錯

本主題中的程式碼是 [快速入門： DEBUG HTML 和 CSS](../debugger/quickstart-debug-html-and-css.md)的範例檔案。 快速入門在設計上出現的錯誤，會在此版本的程式碼中修正。

## <a name="sample-code"></a>範例程式碼
下列 HTML 程式碼用於 \<body> 快速入門的標記中。

```html
<div id="flipTemplate" data-win-control="WinJS.Binding.Template"
         style="display:none">
    <div class="fixedItem" >
        <img src="#" data-win-bind="src: flipImg" />
    </div>
</div>
<div id="fView" data-win-control="WinJS.UI.FlipView" data-win-options="{
    itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">
</div>
```

下列 CSS 顯示 default.css 的新增內容。

```css
#fView {
    background-color:#0094ff;
    height: 500px;
    margin: 25px;
}
```

下列程式碼範例會顯示 default.js 中的完整 JavaScript 程式碼。 此程式碼對 WinJS 命名空間的參考位於範本的 default.html 檔案中。

```javascript
(function () {
    "use strict";

    var app = WinJS.Application;
    var activation = Windows.ApplicationModel.Activation;

    var myData = [];
    for (var x = 0; x < 3; x++) {
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

## <a name="see-also"></a>另請參閱
- [快速入門：偵錯 HTML 和 CSS](../debugger/quickstart-debug-html-and-css.md)
