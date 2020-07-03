---
title: 逐步解說：使用 JavaScript 建立 SDK |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 29dac6cca7936dde8be2ebc57366f6370b8bcbc6
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904949"
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>逐步解說：使用 JavaScript 建立 SDK
本逐步解說將教您如何使用 JavaScript 來建立簡單的數學 SDK，做為 Visual Studio 擴充功能（VSIX）。  本逐步解說分成下列幾個部分：

- [若要建立 SimpleMathVSIX 擴充功能 SDK 專案](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)

- [建立使用 SDK 的範例應用程式](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)

  針對 JavaScript，沒有類別庫專案類型。 在此逐步解說中，範例*arithmetic.js*檔案是直接在 VSIX 專案中建立的。 在實務上，建議您先建立並測試 JavaScript 和 CSS 檔案作為 Windows Store 應用程式（例如，使用**空白應用程式**範本），然後再將它們放在 VSIX 專案中。

## <a name="prerequisites"></a>必要條件
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[VISUAL STUDIO SDK](../extensibility/visual-studio-sdk.md)。

## <a name="to-create-the-simplemathvsix-extension-sdk-project"></a><a name="createSimpleMathVSIX"></a>若要建立 SimpleMathVSIX 擴充功能 SDK 專案

1. 在功能表列上 **，選擇 [** 檔案] [新增] [  >  **New**  >  **專案**]。

2. 在範本類別清單的 [ **Visual c #**] 底下，**選取 [** 擴充性]，然後選取 [ **VSIX 專案**] 範本。

3. 在 [**名稱**] 文字方塊中，指定 `SimpleMathVSIX` 並選擇 [**確定]** 按鈕。

4. 如果 [ **Visual Studio 套件嚮導]** 出現，請選擇 [**歡迎使用**] 頁面上的 [**下一步]** 按鈕，然後在**第1頁**，選擇 [**完成]** 按鈕。

     雖然**資訊清單設計**工具會開啟，但我們會藉由直接修改資訊清單檔，讓此逐步解說保持簡單。

5. 在**方案總管**中，開啟**extension.vsixmanifest**檔案的快捷方式功能表，然後選擇 [ **View Code**]。 使用此程式碼來取代檔案中的現有內容。

    ```xml
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

6. 在**方案總管**中，開啟**SimpleMathVSIX**專案的快捷方式功能表，然後選擇 [**加入**  >  **新專案**]。

7. 在 [**資料**] 類別中，選取 [ **XML**檔案]，將檔案命名為 `SDKManifest.xml` ，然後選擇 [**新增**] 按鈕。

8. 在**方案總管**中，開啟**SDKManifest.xml**檔案的快捷方式功能表，然後選擇 [**開啟**]，在**XML 編輯器**中顯示該檔案。

9. 將下列程式碼新增至**SDKManifest.xml**檔案。

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <FileList
      DisplayName="Simple Math"
      MinVSVersion="14.0"
      AppliesTo="JavaScript+WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">

      <!-- JS -->
      <File Content="js\arithmetic.js" />
    </FileList>

    ```

10. 在**方案總管**中，于**SDKManifest.xml**檔案的快捷方式功能表上，選擇 [**屬性**]。

11. 在 [**屬性**] 視窗中，將 [**在 VSIX 中包含**] 屬性設定為 [ **True**]。

12. 在**方案總管**中，在**SimpleMathVSIX**專案的快捷方式功能表上，選擇 [**加入**  >  **新資料夾**]，然後將資料夾命名為 `Redist` 。

13. 在可轉散發套件下新增子資料夾，以建立此資料夾結構：

     *\Redist\CommonConfiguration\Neutral\SimpleMath\js\\*

14. 在 [ **\js \\ ** ] 資料夾的快捷方式功能表上，選擇 [**加入**  >  **新專案**]。

15. 在 [ **Visual c # 專案**] 底下，選取 [ **Web** ] 類別，然後選取 [ **JavaScript**檔案] 專案。 將檔案命名為 `arithmetic.js` ，然後選擇 [**新增**] 按鈕。

16. 將下列程式碼插入*arithmetic.js*：

    ```csharp
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

17. 在**方案總管**中，于**arithmetic.js**檔案的快捷方式功能表上，選擇 [**屬性**]。 進行這些屬性變更：

    - 將 [**在 VSIX 中包含**] 屬性設定為 [ **True**]。

    - 將 [**複製到輸出目錄**] 屬性設定為 [**永遠複製**]。

18. 在**方案總管**中，在**SimpleMathVSIX**專案的快捷方式功能表上，選擇 [**建立**]。

19. 成功完成組建之後，在專案的快捷方式功能表上，選擇 [**在檔案瀏覽器中開啟資料夾**]。 流覽至**\bin\debug \\ **，然後執行 `SimpleMathVSIX.vsix` 以安裝它。

20. 選擇 [**安裝**] 按鈕，並讓安裝完成。

21. 重新啟動 Visual Studio。

## <a name="to-create-a-sample-app-that-uses-the-sdk"></a><a name="createSampleApp"></a>建立使用 SDK 的範例應用程式

1. 在功能表列上 **，選擇 [** 檔案] [新增] [  >  **New**  >  **專案**]。

2. 在範本類別清單的 [ **JavaScript**] 底下，選取 [ **Windows Store**]，然後選取 [**空白應用程式**] 範本。

3. 在 [**名稱**] 方塊中，指定 `ArithmeticUI` 。 選擇 [確定] **** 按鈕。

4. 在**方案總管**中，開啟**ArithmeticUI**專案的快捷方式功能表，然後選擇 [**加入**  >  **參考**]。

5. 在 [ **Windows**] 底下選擇 [**擴充**功能]，並注意顯示**簡單的數學運算**。

6. 選取 [**簡單數學運算**] 核取方塊，然後選擇 [**確定]** 按鈕。

7. 在**方案總管**的 [**參考**] 底下，請注意會顯示**簡單的數學**參考。 將它展開，並注意有一個包含**arithmetic.js**的 [ **\js \\ ** ] 資料夾。 您可以開啟**arithmetic.js** ，確認已安裝您的原始程式碼。

8. 使用下列程式碼來取代*default.htm*的內容。

   ```html
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

9. 使用下列程式碼來取代*\js\default.js*的內容。

    ```csharp
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

10. 使用下列程式碼取代*\css\default.css*的內容：

    ```xml
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

11. 選擇**F5**鍵以建立並執行應用程式。

12. 在應用程式 UI 中，輸入任兩個數字，選取一項作業，然後選擇 **=** 按鈕。 正確的結果隨即出現。

## <a name="see-also"></a>另請參閱
- [建立軟體開發套件](../extensibility/creating-a-software-development-kit.md)
