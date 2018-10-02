---
title: 逐步解說： 建立使用 JavaScript SDK |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 091bd46c2fb753350fe24837ce2078ed26761b65
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487139"
---
# <a name="walkthrough-creating-an-sdk-using-javascript"></a>逐步解說：使用 JavaScript 建立 SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[逐步解說： 使用 JavaScript 建立 SDK](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-creating-an-sdk-using-javascript)。  
  
本逐步解說將說明如何使用 JavaScript 來建立簡單的數學 SDK 作為 Visual Studio 擴充功能 (VSIX)。  本逐步解說分為下列部分：  
  
-   [若要建立 SimpleMathVSIX 擴充功能 SDK 專案](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)  
  
-   [若要建立範例應用程式使用 SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)  
  
 適用於 JavaScript，沒有任何類別庫專案型別。 在本逐步解說中，直接在 VSIX 專案中建立範例 arithmetic.js 檔案。 在實務上，我們建議您先建置和測試 Windows 市集應用程式的 JavaScript 和 CSS 檔案 — 例如，藉由使用**空白應用程式**範本 — 您將它們放在 VSIX 專案之前。  
  
## <a name="prerequisites"></a>必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 < [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
##  <a name="createSimpleMathVSIX"></a> 若要建立 SimpleMathVSIX 擴充功能 SDK 專案  
  
1.  在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。  
  
2.  在範本類別清單中下**Visual C#**，選取**擴充性**，然後選取**VSIX 專案**範本。  
  
3.  在 [**名稱**文字方塊中，指定`SimpleMathVSIX`，然後選擇 **[確定]** ] 按鈕。  
  
4.  如果**Visual Studio 封裝精靈**出現時，請選擇**下一步**按鈕**歡迎**頁面上，然後在**第 1 頁的 7**，選擇**完成** 按鈕。  
  
     雖然**資訊清單設計工具**隨即開啟，我們將會保留這個逐步解說簡單藉由直接修改資訊清單檔案。  
  
5.  在 **方案總管**，開啟 source.extension.vsixmanifest 檔案中，捷徑功能表，然後選擇**檢視程式碼**。 您可以使用此程式碼取代檔案中的現有內容。  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">  
      <Metadata>  
        <Identity Id="SimpleMathVSIX" Version="1.0" Language="en-US" Publisher="myname" />  
        <DisplayName>Simple Math</DisplayName>  
        <Description>Does basic arithmetic calculations.</Description>  
      </Metadata>  
      <Installation Scope="Global" AllUsers="true">  
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />  
      </Installation>  
      <Dependencies>  
        <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />  
      </Dependencies>  
      <Assets>  
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />  
      </Assets>  
    </PackageManifest>  
    ```  
  
6.  在 **方案總管**，開啟 SimpleMathVSIX 專案的捷徑功能表，然後選擇**新增**，**新項目**。  
  
7.  在 **資料**類別目錄中，選取**XML 檔案**，將檔案命名為`SDKManifest.xml`，，然後選擇 **新增** 按鈕。  
  
8.  在 [**方案總管] 中**，開啟 SDKManifest.xml 檔案的捷徑功能表，然後選擇**開啟**顯示中的檔案**XML 編輯器**。  
  
9. SDKManifest.xml 檔案中加入下列程式碼。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <FileList  
      DisplayName="Simple Math"  
      MinVSVersion="14.0"  
      AppliesTo="JavaScript+WindowsAppContainer"  
      SupportsMultipleVersions="Error"  
      MoreInfo="http://www.msdn.microsoft.com/">  
  
      <!-- JS -->  
      <File Content="js\arithmetic.js" />  
    </FileList>  
  
    ```  
  
10. 在 **方案總管**，在 SDKManifest.xml 檔案的捷徑功能表，選擇**屬性**。  
  
11. 在 **屬性**視窗中，將**Include in VSIX**屬性設 **，則為 True**。  
  
12. 中**方案總管**，在 SimpleMathVSIX 專案的捷徑功能表，選擇 **新增**，**新資料夾**，並接著將資料夾命名`Redist`。  
  
13. 加入子資料夾下建立此資料夾結構的可轉散發套件：  
  
     \Redist\CommonConfiguration\Neutral\SimpleMath\js\  
  
14. 在 \js\ 資料夾的捷徑功能表，選擇**新增**，**新項目**。  
  
15. 底下**Visual C# 項目**，選取**Web**類別，然後再選取**JavaScript 檔案**項目。 將檔案命名`arithmetic.js`，然後選擇**新增** 按鈕。  
  
16. 您可以將下列程式碼插入 arithmetic.js:  
  
    ```  
    (function (global) {  
        "use strict";  
        global.Arithmetic = {  
            add: function (firstNumber, secondNumber) {  
                return firstNumber + secondNumber;  
            },  
  
            subtract: function (firstNumber, secondNumber) {  
                return firstNumber - secondNumber;  
            },  
  
            multiply: function (firstNumber, secondNumber) {  
                return firstNumber * secondNumber;  
            },  
  
            divide: function (firstNumber, secondNumber) {  
                return firstNumber / secondNumber;  
            }  
        };  
    })(this);  
  
    ```  
  
17. 在 **方案總管**，在 arithmetic.js 檔案的捷徑功能表，選擇**屬性**。 這些屬性變更：  
  
    -   設定**Include in VSIX**屬性設 **，則為 True**。  
  
    -   設定**複製到輸出目錄**屬性設**永遠複製**。  
  
18. 在 **方案總管**，在 SimpleMathVSIX 專案的捷徑功能表，選擇 **建置**。  
  
19. 建置專案的捷徑功能表上成功完成之後，選擇**在檔案總管 中開啟資料夾**。 瀏覽至 \bin\debug\\，並執行`SimpleMathVSIX.vsix`進行安裝。  
  
20. 選擇**安裝** 按鈕，讓安裝完成。  
  
21. 重新啟動 Visual Studio。  
  
##  <a name="createSampleApp"></a> 若要建立範例應用程式使用 SDK  
  
1.  在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。  
  
2.  在範本類別清單中下**JavaScript**，選取**Windows 市集**，然後選取**空白應用程式**範本。  
  
3.  在 **名稱**方塊中，指定`ArithmeticUI`。 選擇 [確定]  按鈕。  
  
4.  在 **方案總管**，開啟 ArithmeticUI 專案的捷徑功能表，然後選擇**新增**，**參考**。  
  
5.  底下**Windows**，選擇**擴充功能**，並注意**簡單數學**隨即出現。  
  
6.  選取 [**簡單的數學**核取方塊，然後選擇**確定**] 按鈕。  
  
7.  在**方案總管 中**下方**參考**，注意**簡單的數學**參考會顯示。 展開它，並請注意，有包含 arithmetic.js \js\ 資料夾。 您可以開啟 arithmetic.js 來確認已安裝您的原始程式碼。  
  
8.  您可以使用下列程式碼來取代 default.htm 的內容。  
  
    ```  
    <!DOCTYPE html>  
    <html>  
    <head>  
        <meta charset="utf-8" />  
        <title>ArithmeticUI</title>  
  
        <!-- WinJS references -->  
        <link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" />  
        <script src="//Microsoft.WinJS.1.0/js/base.js"></script>  
        <script src="//Microsoft.WinJS.1.0/js/ui.js"></script>  
  
        <!-- ArithmeticUI references -->  
        <link href="/css/default.css" rel="stylesheet" />  
        <script src="/js/default.js"></script>  
        <script src="/SimpleMath/js/arithmetic.js"></script>  
    </head>  
    <body>  
        <form>  
        <div id="calculator" class="ms-grid">  
            <input name="firstNumber" id="firstNumber" type="number" step="any">  
            <div id="operators">  
                <button class="operator" type="button">+</button>  
                <button class="operator" type="button">-</button>  
                <button class="operator" type="button">*</button>  
                <button class="operator" type="button">/</button>  
            </div>  
            <input id="secondNumber" type="number">  
            <button class="calculate" type="button">=</button>  
            <input id="result" type="number" name="result" disabled="" readonly="">  
        </div>  
        </form>  
    </body>  
    </html>  
    ```  
  
9. 您可以使用下一個程式碼來取代 \js\default.js 的內容。  
  
    ```  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var operation = null;  
  
        function calculateResult() {  
            var firstNumber = parseFloat(document.querySelector("#firstNumber").value),  
                secondNumber = parseFloat(document.querySelector("#secondNumber").value),  
                result = 0;  
  
            if (isNaN(firstNumber) || isNaN(secondNumber)) {  
                result = 0;  
            }  
            else {  
                switch (operation) {  
                    case "+":  
                        result = Arithmetic.add(firstNumber, secondNumber);  
                        break;  
                    case "-":  
                        result = Arithmetic.subtract(firstNumber, secondNumber);  
                        break;  
                    case "*":  
                        result = Arithmetic.multiply(firstNumber, secondNumber);  
                        break;  
                    case "/":  
                        result = Arithmetic.divide(firstNumber, secondNumber);  
                        break;  
                    default:  
                }  
            }  
            document.querySelector("#result").value = result.toString();  
        }  
  
        app.onactivated = function (args) {  
            document.querySelector("#calculator").addEventListener("click", function (event) {  
                if (event.target.tagName.toLowerCase() === "button") {  
                    switch (event.target.className) {  
                        case "operator":  
                            operation = event.target.innerText;  
                            break;  
                        case "calculate":  
                            calculateResult();  
                            break;  
                        default:  
                            break;  
                    }  
                }  
            });  
        };  
  
        app.start();  
    })();  
    ```  
  
10. 取代此程式碼的 \css\default.css 內容：  
  
    ```  
    form {  
        display: -ms-grid;  
        -ms-grid-rows: 1fr auto 1fr;  
        -ms-grid-columns: 1fr auto 1fr;  
        height: 100%;  
        width: 100%;  
    }  
  
    button, input[type=number] {  
        margin-right: 5px;  
        -ms-grid-row-align: center;  
    }  
  
    #calculator {  
        -ms-grid-column: 2;  
        -ms-grid-row: 2;  
        display: -ms-grid;  
        -ms-grid-rows: 1fr;  
        -ms-grid-columns: auto min-content auto auto auto;  
    }  
  
    .ms-grid input {  
        width: 5em;  
    }  
  
    #firstNumber {  
        -ms-grid-column: 1;  
        -ms-grid-row-align: center;  
    }  
  
    #operators {  
        -ms-grid-column: 2;  
        -ms-grid-row-align: center;  
    }  
  
        #operators button.operator {  
            margin-bottom: 5px;  
            height: 40px;  
        }  
  
    #secondNumber {  
        -ms-grid-column: 3;  
    }  
  
    button.calculate {  
        -ms-grid-column: 4;  
        -ms-grid-row-align: center;  
        height: 40px;  
    }  
  
    #result {  
        -ms-grid-column: 5;  
    }  
  
    ```  
  
11. 選擇 F5 鍵以建置並執行應用程式。  
  
12. 在應用程式 UI 中，輸入任何兩個數字，選取作業，然後選擇**=**  按鈕。 正確的結果會出現。  
  
## <a name="see-also"></a>另請參閱  
 [建立軟體開發套件](../extensibility/creating-a-software-development-kit.md)

