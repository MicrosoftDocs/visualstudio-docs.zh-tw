---
title: "如何：建立 JavaScript XML 文件註解 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式碼註解, JavaScript IntelliSense"
  - "文件註解 [JavaScript]"
  - "IntelliSense [JavaScript], XML 文件註解"
  - "XML 文件註解, JavaScript IntelliSense"
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：建立 JavaScript XML 文件註解
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*XML 文件註解*是 JavaScript 註解加入指令碼，以提供程式碼項目，例如函式、 欄位和變數的相關資訊。  當您參考指令碼函式時 Visual Studio，這些文字說明會和 IntelliSense 一起顯示。  
  
 本主題提供基本教學課程，說明使用 XML 文件註解。  如需使用其他項目，如[\<var\>](../ide/var-javascript.md)和[\<value\>](../ide/value-javascript.md)，並獲得額外的程式碼範例，請參閱[XML 文件註解](../ide/xml-documentation-comments-javascript.md)。  如需提供一種非同步回呼的 IntelliSense 資訊，例如`Promise`，請參閱[\<returns\>](../ide/returns-javascript.md)。  
  
> [!NOTE]
>  XML 文件註解都只會從參考的檔案、 組件和服務。  
  
### 若要建立的 JavaScript 函式的 XML 文件註解  
  
-   在函式，加入[\<summary\>](../ide/summary-javascript.md)， [\<param\>](../ide/param-javascript.md)，以及[\<returns\>](../ide/returns-javascript.md)項目，且在完成三個斜線 \(\/ \/\) 與每個項目。  
  
    > [!NOTE]
    >  每個項目必須是在同一行。  
  
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
  
-   若要檢視 XML 文件註解，請鍵入的名稱和左括號標記有 XML 文件註解，如下例所示的函式：  
  
    ```javascript  
    var areaVal = getArea(  
    ```  
  
     當您鍵入左括號包含 XML 文件註解的函式時，程式碼編輯器會使用 IntelliSense 來顯示 XML 文件註解中所定義的資訊。  
  
### 若要建立 XML 文件註解，JavaScript 欄位  
  
-   在建構函式函式或物件定義中，加入[\<field\>](../ide/field-javascript.md)項目加上三個斜線 \(\/ \/\)。  
  
     下列範例顯示使用`<field>`在建構函式中的項目。  如需其他範例，請參閱 [\<field\>](../ide/field-javascript.md)。  
  
    ```javascript  
    function Engine() {  
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
        this.HorsePower = 150;  
    }  
    ```  
  
-   若要檢視 XML 文件註解，請使用與 XML 文件註解，如下例所示的函式建構函式裡有標記建立物件。  
  
    ```javascript  
    var eng = new Engine();  
    ```  
  
-   在下一行中，輸入物件和一個句點，以顯示欄位的 IntelliSense 資訊的名稱。  
  
    ```javascript  
    eng.  
    ```  
  
### 若要建立的多載的函式的 XML 文件註解  
  
1.  在函式，加入[\<signature\>](../ide/signature-javascript.md)每一個多載的項目。  在上述項目，加入其他項目，例如`<summary>`， `<param>`，以及`<returns>`前三個斜線 \(\/ \/\) 與每個項目。  
  
     下列範例示範多載的 JavaScript 函式。  在這個範例中，多載參數型別不同。  
  
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
  
2.  若要檢視 XML 文件註解，請輸入名稱及左括弧的函式標記有 XML 文件註解，如下例所示：  
  
    ```javascript  
    calc(  
    ```  
  
### 若要建立當地語系化的 IntelliSense  
  
1.  建立 XML 檔案具有 OpenAjax MessageBundle 格式的文件註解。  
  
    > [!IMPORTANT]
    >  MessageBundle 是建議的格式。  在 Microsoft Ajax 或.winmd 檔案中不支援這種格式。  如需使用另一個方法`VSDoc`格式，請參閱[\<loc\>](../ide/loc-javascript.md)。  
  
     下列範例顯示在 sidecar 檔案，其中包含當地語系化的 IntelliSense 資訊內容。  這是一個 XML 檔案，位於特定文化特性的資料夾，例如 JA。  資料夾必須在相同的位置所在的.js 檔案`<loc>`項目。  XML 檔案的檔名必須符合`filename`中所指定的參數`<loc>`項目。  
  
    ```  
    <messagebundle>  
      <msg name="1">A class that represents a rectangle</msg>  
      <msg name="2">The length of the rectangle</msg>  
      <msg name="3">The height of the rectangle</msg>  
    </messagebundle>  
  
    ```  
  
2.  在.js 檔案中，加入下列程式碼。  `<loc>`項目之前的任何指令碼，必須先宣告，並遵循與相同的使用方式規則`<reference>`項目。  如需詳細資訊，請參閱 [JavaScript IntelliSense](../ide/javascript-intellisense.md)和 [\<loc\>](../ide/loc-javascript.md)。  
  
    ```javascript  
    /// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
    ```  
  
3.  在.js 檔案中，加入 XML 文件項目和預設描述。  設定`locid`屬性值，使其符合對應的`name` sidecar 檔中屬性值。  如果有的話，將當地語系化的 IntelliSense 資訊來取代預設描述。  
  
    ```javascript  
    function add(a,b)   
    {  
        /// <summary locid='1'>description</summary>  
        /// <param name='a' locid='2'>parameter a description</param>  
        /// <param name='b' locid='3'>parameter b description</param>  
    }  
  
    ```  
  
4.  若要檢視 XML 文件註解，請輸入名稱及左括弧的函式，如下例所示：  
  
    ```javascript  
    add(  
    ```  
  
## 請參閱  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)   
 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)   
 [NIB: Walkthrough: JavaScript IntelliSense in ASP.NET](http://msdn.microsoft.com/zh-tw/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)
