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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72619540"
---
# <a name="create-xml-documentation-comments-for-javascript-intellisense"></a>建立 JavaScript IntelliSense 的 XML 文件註解
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*XML 檔批註*是您加入至腳本的 JavaScript 批註，可提供程式碼專案（例如函式、欄位和變數）的相關資訊。 在 Visual Studio 中，當您參考腳本函數時，這些文字描述會與 IntelliSense 一起顯示。

 本主題提供使用 XML 檔批註的基本教學課程。 如需使用其他元素的詳細資訊，例如[\<var >](../ide/var-javascript.md)和[\<value >](../ide/value-javascript.md)，以及其他程式碼範例，請參閱[XML 檔批註](../ide/xml-documentation-comments-javascript.md)。 如需針對非同步回呼（如 `Promise`）提供 IntelliSense 資訊的詳細資訊，請參閱[\<returns >](../ide/returns-javascript.md)。

> [!NOTE]
> XML 文件註解僅能從參考的檔案、組件和服務取得。

### <a name="to-create-xml-documentation-comments-for-a-javascript-function"></a>若要建立 JavaScript 函數的 XML 檔批註

- 在函式中，新增[\<summary >](../ide/summary-javascript.md)、 [\<param >](../ide/param-javascript.md)和[\<returns >](../ide/returns-javascript.md)專案，並在每個元素前面加上三個斜線（///）。

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

- 若要查看 XML 檔批註，請輸入以 XML 檔註解標記之函式的名稱和左括弧，如下列範例所示：

    ```javascript
    var areaVal = getArea(
    ```

     當您輸入包含 XML 檔批註之函式的左括弧時，程式碼編輯器會使用 IntelliSense 來顯示 XML 檔批註中定義的資訊。

### <a name="to-create-xml-documentation-comments-for-a-javascript-field"></a>若要建立 JavaScript 欄位的 XML 檔批註

- 在函式函數或物件定義中，加入前面加上三個斜線（///）的[\<field >](../ide/field-javascript.md)元素。

     下列範例示範如何在函式函式中使用 `<field>` 元素。 如需其他範例，請參閱[\<field >](../ide/field-javascript.md)。

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

- 在下一行中，輸入物件的名稱和句點，以顯示欄位的 IntelliSense 資訊。

    ```javascript
    eng.
    ```

### <a name="to-create-xml-documentation-comments-for-an-overloaded-function"></a>若要建立多載函式的 XML 檔批註

1. 在函式中，為每個多載新增[\<signature >](../ide/signature-javascript.md)元素。 在這些專案中，新增其他專案，例如 `<summary>`、`<param>` 和 `<returns>`，並在每個專案前面加上三個斜線（///）。

     下列範例會顯示多載的 JavaScript 函數。 在此範例中，多載會因參數類型而有所不同。

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

2. 若要查看 XML 檔批註，請輸入以 XML 檔註解標記之函式的名稱和左括弧，如下列範例所示：

    ```javascript
    calc(
    ```

### <a name="to-create-localized-intellisense"></a>若要建立當地語系化的 IntelliSense

1. 建立 XML 檔案，其中包含 OpenAjax MessageBundle 格式的檔批註。

    > [!IMPORTANT]
    > MessageBundle 是建議的格式。 Microsoft Ajax 或 winmd 檔案中不支援此格式。 如需使用替代 `VSDoc` 格式的詳細資訊，請參閱[\<loc >](../ide/loc-javascript.md)。

     下列範例會顯示側車檔案中的內容，其中包含當地語系化的 IntelliSense 資訊。 這是位於文化特性特定資料夾中的 XML 檔案，例如 JA-JP。 此資料夾必須與包含 `<loc>` 元素的 .js 檔案位於相同的位置。 XML 檔案的檔案名必須符合 `<loc>` 元素中指定的 `filename` 參數。

    ```
    <messagebundle>
      <msg name="1">A class that represents a rectangle</msg>
      <msg name="2">The length of the rectangle</msg>
      <msg name="3">The height of the rectangle</msg>
    </messagebundle>

    ```

2. 在您的 .js 檔案中，新增下列程式碼。 @No__t_0 元素必須在任何腳本之前宣告，並遵循與 `<reference>` 元素相同的使用規則。 如需詳細資訊，請參閱[JavaScript IntelliSense](../ide/javascript-intellisense.md)和[\<loc >](../ide/loc-javascript.md)。

    ```javascript
    /// <loc filename="messageFilename.xml" format="messagebundle"/>

    ```

3. 在您的 .js 檔案中，加入 XML 檔元素和預設描述。 設定 `locid` 屬性值，使其符合側車檔案中對應的 `name` 屬性值。 預設的描述會由當地語系化的 IntelliSense 資訊取代（如果有的話）。

    ```javascript
    function add(a,b)
    {
        /// <summary locid='1'>description</summary>
        /// <param name='a' locid='2'>parameter a description</param>
        /// <param name='b' locid='3'>parameter b description</param>
    }

    ```

4. 若要查看 XML 檔批註，請輸入函式的名稱和左括弧，如下列範例所示：

    ```javascript
    add(
    ```

## <a name="see-also"></a>請參閱
 [JAVAscript intellisense](../ide/javascript-intellisense.md) [XML 檔批註](../ide/xml-documentation-comments-javascript.md)[的筆尖：逐步解說： ASP.NET 中的 javascript intellisense](https://msdn.microsoft.com/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)
