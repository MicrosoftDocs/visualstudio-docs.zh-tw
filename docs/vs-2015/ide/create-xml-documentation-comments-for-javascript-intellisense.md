---
title: 建立 JavaScript IntelliSense 的 XML 檔批註 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code comments, JavaScript IntelliSense
- XML documentation comments, JavaScript IntelliSense
- documentation comments [JavaScript]
- IntelliSense [JavaScript], XML documentation comments
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 21fdc15b161b7d1cef30effe82e518a174bc9666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619540"
---
# <a name="create-xml-documentation-comments-for-javascript-intellisense"></a>建立 JavaScript IntelliSense 的 XML 文件註解
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*XML 檔批註* 是您新增至腳本的 JavaScript 批註，可提供程式碼專案的相關資訊，例如函數、欄位和變數。 在 Visual Studio 中，當您參考腳本函式時，就會使用 IntelliSense 來顯示這些文字描述。

 本主題提供使用 XML 檔批註的基本教學課程。 如需使用其他專案（例如 [\<var>](../ide/var-javascript.md) 和 [\<value>](../ide/value-javascript.md) ）和其他程式碼範例的相關資訊，請參閱 [XML 檔批註](../ide/xml-documentation-comments-javascript.md)。 如需提供非同步回呼的 IntelliSense 資訊（例如）的詳細資訊 `Promise` ，請參閱 [\<returns>](../ide/returns-javascript.md) 。

> [!NOTE]
> XML 文件註解僅能從參考的檔案、組件和服務取得。

### <a name="to-create-xml-documentation-comments-for-a-javascript-function"></a>建立 JavaScript 函數的 XML 檔批註

- 在函式中，加入 [\<summary>](../ide/summary-javascript.md) 、 [\<param>](../ide/param-javascript.md) 和專案 [\<returns>](../ide/returns-javascript.md) ，並在每個元素前面加上三個斜線 (///) 。

    > [!NOTE]
    > 每個元素都必須在同一行上。

     下列範例顯示 JavaScript 函數。

    ```javascript
    function getArea(radius)
    {
        /// <summary>Determines the area of a circle that has the specified radius parameter.</summary>
        /// <param name="radius" type="Number">The radius of the circle.</param>
        /// <returns type="Number">The area.</returns>
        var areaVal;
        areaVal = Math.PI * radius * radius;
        return areaVal;
    }
    ```

- 若要查看 XML 檔批註，請輸入標示有 XML 檔批註的函式名稱和左括弧，如下列範例所示：

    ```javascript
    var areaVal = getArea(
    ```

     當您輸入包含 XML 檔批註的函式的左括弧時，程式碼編輯器會使用 IntelliSense 來顯示 XML 檔批註中定義的資訊。

### <a name="to-create-xml-documentation-comments-for-a-javascript-field"></a>若要建立 JavaScript 欄位的 XML 檔批註

- 在函式函數或物件定義中，將 [\<field>](../ide/field-javascript.md) 前面加上三個斜線的元素加入 (///) 。

     下列範例示範如何在函式 `<field>` 函數中使用元素。 如需其他範例，請參閱 [\<field>](../ide/field-javascript.md) 。

    ```javascript
    function Engine() {
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>
        this.HorsePower = 150;
    }
    ```

- 若要查看 XML 檔批註，請使用以 XML 檔註解標記的函式函式來建立物件，如下列範例所示。

    ```javascript
    var eng = new Engine();
    ```

- 在下一行中，輸入物件的名稱和句點來顯示該欄位的 IntelliSense 資訊。

    ```javascript
    eng.
    ```

### <a name="to-create-xml-documentation-comments-for-an-overloaded-function"></a>建立多載函式的 XML 檔批註

1. 在函式中，加入 [\<signature>](../ide/signature-javascript.md) 每個多載的元素。 在這些專案中，新增其他專案（例如 `<summary>` 、 `<param>` 和 `<returns>` ），並在每個元素前面加上三個斜線 (///) 。

     下列範例顯示多載的 JavaScript 函數。 在此範例中，多載會依參數類型而有所不同。

    ```javascript
    function calc(a) {
        /// <signature>
        /// <summary>Function summary 1.</summary>
        /// <param name="a" type="Number">A number.</param>
        /// <returns type="Number" />
        /// </signature>
        /// <signature>
        /// <summary>Function summary 2.</summary>
        /// <param name="a" type="String">A string.</param>
        /// <returns type="Number" />
        /// </signature>
        return a;
    }
    ```

2. 若要查看 XML 檔批註，請輸入標示有 XML 檔批註的函式名稱和左括弧，如下列範例所示：

    ```javascript
    calc(
    ```

### <a name="to-create-localized-intellisense"></a>若要建立當地語系化的 IntelliSense

1. 建立具有 OpenAjax MessageBundle 格式檔批註的 XML 檔案。

    > [!IMPORTANT]
    > MessageBundle 是建議的格式。 Microsoft Ajax 或 winmd 檔案中不支援此格式。 如需使用替代格式的詳細資訊 `VSDoc` ，請參閱 [\<loc>](../ide/loc-javascript.md) 。

     下列範例會顯示側車檔案中的內容，其中包含當地語系化的 IntelliSense 資訊。 這是位於文化特性特定資料夾中的 XML 檔案，例如 JA-JP。 資料夾必須與包含元素的 .js 檔案位於相同的位置。 `<loc>` XML 檔案的檔案名必須與 `filename` 元素中指定的參數相符 `<loc>` 。

    ```
    <messagebundle>
      <msg name="1">A class that represents a rectangle</msg>
      <msg name="2">The length of the rectangle</msg>
      <msg name="3">The height of the rectangle</msg>
    </messagebundle>

    ```

2. 在您的 .js 檔案中，加入下列程式碼。 您 `<loc>` 必須在任何腳本之前宣告元素，並遵循與元素相同的使用規則 `<reference>` 。 如需詳細資訊，請參閱 [JavaScript IntelliSense](../ide/javascript-intellisense.md) 和 [\<loc>](../ide/loc-javascript.md) 。

    ```javascript
    /// <loc filename="messageFilename.xml" format="messagebundle"/>

    ```

3. 在 .js 檔案中，加入 XML 檔元素和預設描述。 設定 `locid` 屬性值，以符合側車檔案 `name` 中對應的屬性值。 如果有的話，將會以當地語系化的 IntelliSense 資訊取代預設描述。

    ```javascript
    function add(a,b)
    {
        /// <summary locid='1'>description</summary>
        /// <param name='a' locid='2'>parameter a description</param>
        /// <param name='b' locid='3'>parameter b description</param>
    }

    ```

4. 若要查看 XML 檔批註，請輸入函數的名稱和左括弧，如下列範例所示：

    ```javascript
    add(
    ```

## <a name="see-also"></a>另請參閱
 [JAVAscript intellisense](../ide/javascript-intellisense.md) [XML 檔批註](../ide/xml-documentation-comments-javascript.md)[筆尖：逐步解說： ASP.NET 中的 javascript intellisense](https://msdn.microsoft.com/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)
