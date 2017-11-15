---
title: "Visual Studio 中的 JavaScript | Microsoft Docs"
ms.custom: 
ms.date: 04/10/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 74dca14c-5071-416f-a92b-d09f95e3dfb8
caps.latest.revision: "1"
author: bowdenk7
ms.author: wilkelly
manager: ghogen
ms.openlocfilehash: d217443ed0231d71f861ed54b27f3f8d1e8d49ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="javascript-in-includevsdev15docsmiscincludesvsdev15mdmd"></a>[!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] 中的 JavaScript

JavaScript 是在 Visual Studio 中的第一級語言。 當您在 Visual Studio IDE 中撰寫 JavaScript 程式碼時，可以使用大部分或所有標準編輯輔助，包括程式碼片段、IntelliSense 等等。 您可以為許多應用程式類型和服務撰寫 JavaScript 程式碼。

## <a name="ES6"></a> ECMAScript 2015 (ES6) 和更新版本的支援
Visual Studio 現在支援 ECMAScript 語言更新的語法，例如 ECMAScript 2015/2016。

### <a name="what-is-ecmascript-2015"></a>何謂 ECMAScript 2015？

JavaScript 仍然會演變為程式設計語言，而 [TC39](http://www.ecma-international.org/memento/TC39.htm) 是負責進行更新的委員會。  
ECMAScript 2015 是帶來許多全新有用語法和功能的 JavaScript 語言更新。
若要深度剖析 ES6 功能，請參閱[這個](http://es6-features.org)參照網站。

除了 ECMAScript 2015 支援之外，Visual Studio 也會支援 ECMAScript 2016，而且將支援已發行的未來 ECMAScript 版本。 若要追蹤 TC39 和 ECMAScript 中的最新變更，請遵循其在 [github](https://github.com/tc39) 上的工作。

### <a name="transpiling-javascript"></a>轉譯 JavaScript

常見 JavaScript 問題是您想要使用最新 ES6+ 語言功能，因為它們可協助您更具生產力，但是您的執行階段環境 (通常是瀏覽器) 尚未支援這些新功能。
這表示您必須追蹤哪些瀏覽器支援哪些功能 (這可能十分乏味)，或者需要一種方法可以將 ES6+ 程式碼轉換成您目標執行階段了解的版本 (通常是 ES5)。
這一般稱為「轉譯」。

TypeScript 的其中一個功能是可將 ES6+ 程式碼轉譯為 ES5 或 ES3，以撰寫讓您最具生產力的程式碼，但仍然在任何平台上執行程式碼。  
因為 [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] 中的 JavaScript 使用與 TypeScript 相同的語言服務，所以它也可以利用 ES6+ 到 ES5 的轉譯。

您需要對設定選項有一些了解，才能進行此設定。 TypeScript 是透過 `tsconfig.json` 檔案設定。 沒有此類檔案時，會使用某些預設值。 基於相容性的理由，這些預設值在只有 JavaScript 檔案 (或 `.d.ts` 檔案) 的內容中是不同的。 若要編譯 JavaScript 檔案，必須新增 `tsconfig.json` 檔案，然後必須明確設定其中一些選項。

tsconfig 檔案的必要設定列示如下︰

 - `allowJs`︰此值必須設為 `true` 才能夠辨識 JavaScript 檔案。
當 TypeScript 編譯至 JavaScript，這預設為 `false`，這是為了避免編譯器包含它剛所編譯的檔案。
 - `outDir`︰這應該設定為不包含在專案中的位置，以不偵測到發出的 JavaScript 檔案，然後包含在專案中 (請參閱後文的 `exclude`)。
 - `module`︰如果使用模組，此設定會告知編譯器發出的程式碼應該使用哪種模組格式 (例如節點的 `commonjs` 或 Browserify 等搭配程式)。
 - `exclude`︰此設定會指出專案不包含哪些資料夾。 
 輸出位置以及 `node_modules` 或 `temp` 等非專案資料夾，應該加入此設定。
 - `enableAutoDiscovery`︰此設定會啟用自動偵測和下載定義檔案，如上文所述。
 - `compileOnSave`︰此設定會告知編譯器是否只要來源檔案儲存在 Visual Studio 中，就應該隨時重新編譯。
 - `typeAcquisition`：這組設定控制自動類型擷取的行為 (會在[本節](https://docs.microsoft.com/en-us/visualstudio/ide/javascript-intellisense#Auto)中進一步解釋)。

若要將 JavaScript 檔案轉換成 CommonJS 模組並將它們放入 `./out` 資料夾中，您可以使用下列 `tsconfig.json` 檔案。

```json
{
  "compilerOptions": {
    "module": "commonjs",
    "allowJs": true,
    "outDir": "out"
  },
  "exclude": [
    "node_modules",
    "wwwroot",
    "out"
  ],
  "compileOnSave": true,
  "typeAcquisition": {
    "enable": true
  }
}
```

如果來源檔案 (`./app.js`) 存在並包含以下數種 ECMAScript 2015 語言功能，即就地使用上述設定︰

```js
import {Subscription} from 'rxjs/Subscription';  // ES6 import

class Foo {  // ES6 Class
    sayHi(name) {
        return `Hi ${name}, welcome to Salsa!`;  // ES6 template string
    }
}

export let sqr = x => x * x;  //ES6 export, let, and arrow function
export default Subscription;  //ES6 default export
```

然後檔案會發出至 `./out/app.js`，以類似下例的 ECMAScript 5 為目標 (預設值)：

```js
"use strict";
var Subscription_1 = require('rxjs/Subscription');
var Foo = (function () {
    function Foo() {
    }
    Foo.prototype.sayHi = function (name) {
        return "Hi " + name + ", welcome to Salsa!";
    };
    return Foo;
}());
exports.sqr = function (x) { return x * x; };
Object.defineProperty(exports, "__esModule", { value: true });
exports.default = Subscription_1.Subscription;
```

## <a name="better-intellisense"></a>更佳的 IntelliSense

[!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] 中的 JavaScript IntelliSense 現在會顯示更多有關參數及成員清單的資訊。 此項新資訊是由 TypeScript 語言服務提供，使用程式碼更容易了解的幕後靜態分析。 您可以在[這裡](/visualstudio/ide/javascript-intellisense/)深入了解新的 IntelliSense 體驗和其運作方式。

## <a name="JSX"></a>JSX 語法支援

[!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] 中的 JavaScript 充分支援 JSX 語法。 JSX 是一種語法集，可讓 HTML 在 JavaScript 檔案中標記。 

下圖顯示 `comps.tsx` TypeScript 檔案中所定義的反應元件，然後從 `app.jsx` 檔案使用此元件，以 JSX 運算式內的完成及記錄來完成 IntelliSense。
這裡不需要 TypeScript，此特例只是也剛好包含一些 TypeScript 程式碼。

<img src="./media/react.png" height="500" width="640"/>

> [!NOTE]
> 將 JSX 語法轉換成回應呼叫，`"jsx": "react"` 設定必須新增至上述 `tsconfig.json` 檔案的 `compilerOptions` 中。

於建置時建立在 `./out/app.js' 的 JavaScript 檔案會包含程式碼：

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

# <a name="configuring-your-javascript-project"></a>設定 JavaScript 專案
語言服務具備靜態分析功能，這表示會分析原始程式碼但不會實際執行它，以傳回 IntelliSense 結果，並提供其他編輯功能。
因此，包含您專案內容的檔案數量和大小越大，分析期間所使用的記憶體和 CPU 就越多。
因此，有幾個關於專案圖形所做的預設假設：

- `package.json` 和 `bower.json` 列出專案所使用的相依性，並且預設會包含在自動類型擷取 (ATA) <TODO - 新增連結> 中
- 最上層 `node_modules` 資料夾包含程式庫原始程式碼，而且預設會從專案內容中排除其內容
- 每個其他 `.js`、`.jsx`、`.ts` 和 `.tsx` 檔案都可能是「您自己的」其中一個原始程式碼，而且必須包含在專案內容中

在大部分情況下，您只要開啟您的專案，就可以具有使用上述預設專案組態的絕佳體驗。
不過，如果專案具有不同的資料夾結構，或是特別大型的專案，它可能會想要進一步設定語言服務，只將焦點更恰當地放在您自己的原始程式碼。

## <a name="overriding-defaults"></a>覆寫預設值
將 `tsconfig.json` 檔案新增至您的專案根目錄，即可覆寫上述預設組態。
`tsconfig.json` 有數個不同的選項可以管理您的專案內容。
下面列出其中一部分，但如需這組完整的所有可用選項，[請參閱結構描述存放區](http://json.schemastore.org/tsconfig)。 

## <a name="important-tsconfigjson-options"></a>重要 `tsconfig.json` 選項

```json
{
  "compilerOptions": {
    "allowJs": true,          // include .js and .jsx in project context (defaults to only .ts and .tsx)
    "noEmit": true            // turns off downlevel compiler
  },
  "files": [],                // list of explicit files to include in the project context. Highest priority.
  "include": [],              // list of folders or glob patterns to include in the project context.
  "exclude": [],              // list of folders or glob patterns to exclude. Overridden by files array.
  "typeAcquisition": {
    "enable": true,           // Defaulted to "false" with a tsconfig. Enables better IntelliSense in JS.
    "include": [ "jquery" ],  // Specific libs to fetch .d.ts files that weren't picked up by ATA 
    "exclude": [ "node" ]     // Specific libs to not fetch .d.ts files for
  }
}
```

## <a name="example-project-configuration"></a>專案組態範例

如果專案具有下列設定：
- 專案的原始程式檔位在 `wwwroot/js` 中
- 專案的 lib 檔案位在 `wwwrrot/lib` 中
- `bootstrap`、`jquery`、`jquery-validation` 和 `jquery-validation-unobtrusive` 列在 `bower.json` 中
- `kendo-ui` 已手動新增至 lib 資料夾

![資料夾結構](./media/folderStructure.png)

您可以使用下列 `tsconfig.json` 確定語言服務僅分析 `js` 資料夾中的原始程式檔，但仍然擷取和使用 `lib` 資料夾中程式庫的 `.d.ts` 檔案。

```json
{
  "compilerOptions": {
    "allowJs": true,          
    "noEmit": true            
  },
  "exclude": ["wwwroot/lib"],  //ignore lib folders, we will get IntelliSense via ATA
  "typeAcquisition": {
    "enable": true,            
    "include": [ "kendo-ui" ]  //kendo-ui wasn't added via bower, so we need to list it here
  }
}
```

# <a name="notable-changes-from-vs-2015"></a>VS 2015 的重要變更 
因為 [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] 功能是全新的語言服務，所以有一些行為會與先前的體驗不同或根本不存在。
最重要的變更是將 VSDoc 取代為 JSDoc、移除自訂 `.intellisense.js` 延伸模組，以及特定程式碼模式的有限 IntelliSense。

## <a name="no-more-references-or-referencesjs"></a>不再有 `///<references/>` 或 `_references.js`
先前，在檔案落在 IntelliSense 範圍的任何給定時間，要了解它極為複雜。
有時想要包含範圍中您的所有檔案，其他時間則否，但這會導致包含手動參考管理的複雜組態。
接下來，您不再需要思考參考管理，因此不需要三個斜線參考註解或 `_references.js` 檔案。

如需 IntelliSense works 運作方式的詳細資訊，請參閱 [JavaScript IntelliSense](/visualstudio/ide/javascript-intellisense/) 頁面。

## <a name="vsdoc"></a>VSDoc
XML 文件註解有時稱為 VSDocs，先前可以用來使用其他資料來裝飾原始程式碼，而這些資料將用來強化 IntelliSense 結果。
不再支援有利於可更輕鬆寫入的 [JSDoc](http://usejsdoc.org/about-getting-started.html) 和接受的 JavaScript 標準的 VSDoc。

### <a name="intellisensejs-extensions"></a>`.intellisense.js` 延伸模組
先前，您可以編寫 [IntelliSense 延伸模組](https://msdn.microsoft.com/en-us/library/hh874692.aspx)，以讓您新增協力廠商程式庫的自訂完成結果。
這些延伸模組的撰寫相當困難，而且安裝和參考它們十分麻煩，因此新語言服務往後將不支援這些檔案。
撰寫 TypeScript 定義檔來提供與舊 `.intellisense.js` 延伸模組相同的 IntelliSense 優點，是較簡單的替代方法。
您可以在[這裡](http://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)深入了解宣告 (`.d.ts`) 檔案編寫。

### <a name="unsupported-patterns"></a>不支援的模式
因為新語言服務具有靜態分析功能，而不是執行引擎 (如需差異的資訊，請閱讀[本問題](https://github.com/Microsoft/TypeScript/issues/4789))，所以無法再偵測到一些 JavaScript 模式。
最常見的模式是 "expando" 模式。 語言服務目前無法在宣告之後附加屬性的物件上提供 IntelliSense。
例如: 

```js
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense won't show properties a or b
```

在建立物件期間宣告屬性，即可解決這個問題：
```js
var obj = {
    "a": 10,
    "b": "hello world"
}
obj. // IntelliSense shows properties a and b
```

您也可以新增 JSDoc 註解，如上所示：
```js
/**
 * @type {{a: number, b: string}}
 */
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense shows properties a and b
```