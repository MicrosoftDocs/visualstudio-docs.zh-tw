---
title: 建立 JavaScript IntelliSense 的 XML 文件註解 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code comments, JavaScript IntelliSense
- XML documentation comments, JavaScript IntelliSense
- documentation comments [JavaScript]
- IntelliSense [JavaScript], XML documentation comments
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3801fb58f09ac70c26e21304957e31f7b3ec4ddc
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2018
ms.locfileid: "48881016"
---
# <a name="create-xml-documentation-comments-for-javascript-intellisense"></a>建立 JavaScript IntelliSense 的 XML 文件註解
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[Visual Studio 2017 文件](/visualstudio/)。  
  
*XML 文件註解*是 JavaScript 的註解，您將新增至指令碼，以提供程式碼項目，例如函式、 欄位和變數的相關資訊。 在 Visual Studio 中，這些文字描述會顯示與 IntelliSense，當您參考指令碼函式。  
  
 本主題提供基本教學課程中使用 XML 文件註解。 如需使用其他項目，例如[ \<var >](../ide/var-javascript.md)並[\<值 >](../ide/value-javascript.md)，和其他程式碼範例，請參閱[XML 文件註解](../ide/xml-documentation-comments-javascript.md). 如需這類提供 IntelliSense 資訊的非同步回呼`Promise`，請參閱 < [\<傳回 >](../ide/returns-javascript.md)。  
  
> [!NOTE]
>  XML 文件註解僅能從參考的檔案、組件和服務取得。  
  
### <a name="to-create-xml-documentation-comments-for-a-javascript-function"></a>若要建立 XML 文件註解，JavaScript 函式  
  
-   在函數中，新增[\<摘要 >](../ide/summary-javascript.md)， [ \<param >](../ide/param-javascript.md)，並[\<傳回 >](../ide/returns-javascript.md)項目，並在與每個項目之前三個斜線 （/ /）。  
  
    > [!NOTE]
    >  每個項目必須是單一行。  
  
     下列範例顯示的 JavaScript 函式。  
  
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
  
-   若要檢視 XML 文件註解，請輸入名稱和標記使用 XML 文件註解，如下列範例所示的函式的左括號：  
  
    ```javascript  
    var areaVal = getArea(  
    ```  
  
     當您輸入包含 XML 文件註解的函式的左括號時，程式碼編輯器會使用 IntelliSense 來顯示 XML 文件註解中所定義的資訊。  
  
### <a name="to-create-xml-documentation-comments-for-a-javascript-field"></a>若要建立 JavaScript 欄位的 XML 文件註解  
  
-   在建構函式函式或物件定義中，新增[\<欄位 >](../ide/field-javascript.md)項目加上三個斜線 （/ /）。  
  
     下列範例示範使用`<field>`建構函式中的項目。 如需其他範例，請參閱 < [\<欄位 >](../ide/field-javascript.md)。  
  
    ```javascript  
    function Engine() {  
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
        this.HorsePower = 150;  
    }  
    ```  
  
-   若要檢視 XML 文件註解，請使用 XML 文件註解，如下列範例所示使用標示的函式建構函式建立物件。  
  
    ```javascript  
    var eng = new Engine();  
    ```  
  
-   在下一行中，輸入名稱的物件和句點，以顯示欄位的 IntelliSense 資訊。  
  
    ```javascript  
    eng.  
    ```  
  
### <a name="to-create-xml-documentation-comments-for-an-overloaded-function"></a>若要建立的多載的函式的 XML 文件註解  
  
1.  在函數中，新增[\<簽章 >](../ide/signature-javascript.md)每個多載的項目。 在這些項目中，加入其他項目，例如`<summary>`， `<param>`，和`<returns>`，上述每個項目使用三個斜線 （/ /）。  
  
     下列範例會示範多載的 JavaScript 函式。 在此範例中，多載參數類型不同。  
  
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
  
2.  若要檢視 XML 文件註解，請輸入名稱和標記使用 XML 文件註解，如下列範例所示的函式的左括號：  
  
    ```javascript  
    calc(  
    ```  
  
### <a name="to-create-localized-intellisense"></a>若要建立當地語系化的 IntelliSense  
  
1.  建立具有 OpenAjax MessageBundle 格式文件註解的 XML 檔案。  
  
    > [!IMPORTANT]
    >  MessageBundle 是建議的格式。 在 Microsoft Ajax 或.winmd 檔案中不支援這種格式。 如需使用替代方法`VSDoc`格式，請參閱 < [ \<loc >](../ide/loc-javascript.md)。  
  
     下列範例示範內容，其中包含當地語系化的 IntelliSense 資訊側車檔案中。 這是一個 XML 檔案，它位於特定文化特性資料夾中，例如日本。 此資料夾必須位於相同的位置，以包含.js 檔案`<loc>`項目。 XML 檔案的檔案名稱必須符合`filename`參數中指定`<loc>`項目。  
  
    ```  
    <messagebundle>  
      <msg name="1">A class that represents a rectangle</msg>  
      <msg name="2">The length of the rectangle</msg>  
      <msg name="3">The height of the rectangle</msg>  
    </messagebundle>  
  
    ```  
  
2.  在.js 檔案中，新增下列程式碼。 `<loc>`項目之前的任何指令碼，必須先宣告，並遵循相同的使用方式規則`<reference>`項目。 如需詳細資訊，請參閱 < [JavaScript IntelliSense](../ide/javascript-intellisense.md)並[ \<loc >](../ide/loc-javascript.md)。  
  
    ```javascript  
    /// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
    ```  
  
3.  在.js 檔案中，新增的 XML 文件項目及預設描述。 設定`locid`屬性值，以符合對應`name`側車檔案中的屬性值。 當地語系化的 IntelliSense 資訊，請將取代預設的描述，如果有的話。  
  
    ```javascript  
    function add(a,b)   
    {  
        /// <summary locid='1'>description</summary>  
        /// <param name='a' locid='2'>parameter a description</param>  
        /// <param name='b' locid='3'>parameter b description</param>  
    }  
  
    ```  
  
4.  若要檢視 XML 文件註解，請輸入名稱和左括號的函式，如下列範例所示：  
  
    ```javascript  
    add(  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)   
 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)   
 [NIB： 逐步解說： 在 ASP.NET 中的 JavaScript IntelliSense](http://msdn.microsoft.com/en-us/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)



