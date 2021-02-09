---
title: JavaScript IntelliSense
description: 瞭解 Visual Studio 如何提供更豐富的 IntelliSense、新式 JavaScript 功能的支援，以及改善的生產力功能。
ms.custom: SEO-VS-2020
ms.date: 06/28/2017
ms.topic: conceptual
ms.technology: vs-javascript
helpviewer_keywords:
- IntelliSense [JavaScript]
- <reference> JavaScript XML tag
- JavaScript Code Editor
- XML code comments, JavaScript IntelliSense
- reference JavaScript XML tag
- JavaScript, IntelliSense
- code comments, JavaScript IntelliSense
- JavaScript, reference groups
- JavaScript Editor
- reference directives [JavaScript]
- JavaScript, XML documentation comments
- reference groups [JavaScript]
- JavaScript, reference directives
- IntelliSense [JavaScript], about
- IntelliSense extensibility [JavaScript]
- XML documentation comments [JavaScript]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5a4120a6038949f172b96bec599f2329b69abcac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903976"
---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense

Visual Studio 提供現成可用的強大 JavaScript 編輯體驗。 由 TypeScript 型語言服務提供，Visual Studio 提供更豐富的 IntelliSense、支援最新的 JavaScript 功能，並改善如移至定義、重構及更多的生產力功能。

> [!NOTE]
> 從 Visual Studio 2017 開始，JavaScript 語言服務即使用新的語言服務引擎 (稱為 "Salsa")。 本文包含詳細資料；您也可以閱讀這篇[部落格文章](https://devblogs.microsoft.com/visualstudio/previewing-salsa-javascript-language-service-visual-studio-15/)。 新的編輯經驗大部分也適用於 Visual Studio Code。 如需詳細資訊，請參閱 [JavaScript in VS Code](https://code.visualstudio.com/docs/languages/javascript) (VS 程式碼中的 JavaScript)。

如需一般 Visual Studio IntelliSense 功能的詳細資訊，請參閱[使用 IntelliSense](../ide/using-intellisense.md)。

## <a name="whats-new-in-the-javascript-language-service-in-visual-studio-2017"></a>Visual Studio 2017 中 JavaScript 語言服務的新功能

從 Visual Studio 2017 開始，JavaScript IntelliSense 會顯示更多有關參數和成員清單的資訊。 此項新資訊是由 TypeScript 語言服務提供，使用程式碼更容易了解的幕後靜態分析。

TypeScript 使用數個來源建立這項資訊：

- [以型別推斷為基礎的 IntelliSense](#TypeInference)
- [以 JSDoc 為基礎的 IntelliSense](#JsDoc)
- [以 TypeScript 宣告檔案為基礎的 IntelliSense](#TsDeclFiles)
- [自動擷取型別定義](#Auto)

<a name="TypeInference"></a>

### <a name="intellisense-based-on-type-inference"></a>以型別推斷為基礎的 IntelliSense

在 JavaScript 中，大部分的時間不提供任何明確的類型資訊。 幸運的是，只要指定周圍的程式碼內容，通常很容易就能找出類型。
此程序稱為型別推斷。

變數或屬性的類型，通常是用來初始化值的類型或最新的值指派。

```js
var nextItem = 10;
nextItem; // here we know nextItem is a number

nextItem = "box";
nextItem; // now we know nextItem is a string
```

函式的傳回型別則可從傳回的陳述式推斷。

函式參數目前沒有任何推斷，但使用 JSDoc 或 TypeScript *.d.ts* 檔案有多種方法可解決此問題 (請參閱稍後的章節)。

此外，還有下列項目的特殊推斷︰

- "ES3-style" 類別，使用建構函式和原型屬性指派所指定。
- CommonJS-style 模組模式，指定為 `exports` 物件的屬性指派或 `module.exports` 屬性的指派。

```js
function Foo(param1) {
    this.prop = param1;
}
Foo.prototype.getIt = function () { return this.prop; };
// Foo will appear as a class, and instances will have a 'prop' property and a 'getIt' method.

exports.Foo = Foo;
// This file will appear as an external module with a 'Foo' export.
// Note that assigning a value to "module.exports" is also supported.
```

<a name="JsDoc"></a>

### <a name="intellisense-based-on-jsdoc"></a>以 JSDoc 為基礎的 IntelliSense

遇到不提供所需類型資訊 (或支援文件) 的型別推斷，可能會透過 JSDoc 註解明確提供類型資訊。  例如，若要為部分宣告的物件提供特定的類型，您可以使用 `@type` 標記，如下所示︰

```js
/**
 * @type {{a: boolean, b: boolean, c: number}}
 */
var x = {a: true};
x.b = false;
x. // <- "x" is shown as having properties a, b, and c of the types specified
```

如前所述，永遠不會推斷函式參數。 不過，使用 JSDoc `@param` 標記也可以在函式參數中加入類型。

```js
/**
 * @param {string} param1 - The first argument to this function
 */
function Foo(param1) {
    this.prop = param1; // "param1" (and thus "this.prop") are now of type "string".
}
```

如需目前支援的 JsDoc 註解，請參閱 [JavaScript 中的 JSDoc 支援](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript)。

<a name="TsDeclFiles"></a>
### <a name="intellisense-based-on-typescript-declaration-files"></a>以 TypeScript 宣告檔案為基礎的 IntelliSense

因為 JavaScript 和 TypeScript 現在是以相同的語言服務為基礎，所以能夠以更豐富的方式互動。 例如，可為 *.d.ts* 檔案中宣告的值提供 JavaScript IntelliSense (請參閱 [TypeScript 文件](https://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html))，而在 TypeScript 中宣告的介面和類別等類型，可提供 JsDoc 註解當作類型使用。

以下簡單示範 TypeScript 定義檔案 (透過介面) 向同一專案中的 JavaScript 檔案 (使用 `JsDoc` 標記) 提供此類的類型資訊。

![TypeScript 定義檔](https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png)

<a name="Auto"></a>
### <a name="automatic-acquisition-of-type-definitions"></a>自動擷取型別定義

在 TypeScript 世界中，最熱門的 JavaScript 程式庫都使用 *.d.ts* 檔案描述其 API，而這類定義最常見的存放庫位於 [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped)。

根據預設，Salsa 語言服務會嘗試偵測使用中的 JavaScript 程式庫為何，並自動下載及參考對應的 *.d.ts* 檔案，以描述程式庫來提供更豐富的 IntelliSense。 這些檔案會下載到位於 *%LOCALAPPDATA%\Microsoft\TypeScript* 的使用者資料夾下的快取。

> [!NOTE]
> 如果使用 *tsconfig.json* 組態檔，這項功能預設會 [停用]，但可設定為 [啟用]，詳細資訊如下所述。

自動偵測目前處理從 npm (藉由讀取 *package.json* 檔案)、Bower (藉由讀取 *bower.json* 檔案)，以及比對前 400 多個熱門 JavaScript 程式庫清單的專案中的鬆散式檔案下載的相依性。 例如，如果您的專案中有 *jquery-1.10.min.js*，則會擷取並載入檔案 *jquery.d.ts* 以提供更好的編輯體驗。 此 *.d.ts* 檔案對您的專案沒有任何影響。

如果您不想使用自動擷取，請如下所示新增組態檔來停用這項功能。 您仍然放置定義檔案，以手動方式直接在專案中使用它。

## <a name="see-also"></a>另請參閱

- [使用 IntelliSense](../ide/using-intellisense.md)
- [JavaScript 支援 (Visual Studio for Mac)](/visualstudio/mac/javascript)
