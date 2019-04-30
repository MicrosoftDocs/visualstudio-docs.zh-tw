---
title: 逐步解說：使用 JavaScript 建立 SDK |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f15dc7ef3c5ab06857307081511f1c9aa2285566
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796339"
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>逐步解說：建立使用 JavaScript SDK
本逐步解說將說明如何使用 JavaScript 來建立簡單的數學 SDK 作為 Visual Studio 擴充功能 (VSIX)。  本逐步解說分為下列部分：

- [若要建立 SimpleMathVSIX 擴充功能 SDK 專案](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)

- [若要建立範例應用程式使用 SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)

  適用於 JavaScript，沒有任何類別庫專案型別。 在本逐步解說範例*arithmetic.js*直接在 VSIX 專案中建立檔案。 在實務上，我們建議您先建置和測試 Windows 市集應用程式的 JavaScript 和 CSS 檔案 — 例如，藉由使用**空白應用程式**範本 — 您將它們放在 VSIX 專案之前。

## <a name="prerequisites"></a>必要條件
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 < [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。

## <a name="createSimpleMathVSIX"></a> 若要建立 SimpleMathVSIX 擴充功能 SDK 專案

1. 在功能表列上，選擇 [檔案] > [新增] > [專案]。

2. 在範本類別清單中下**Visual C#**，選取**擴充性**，然後選取**VSIX 專案**範本。

3. 在 [**名稱**文字方塊中，指定`SimpleMathVSIX`，然後選擇 **[確定]** ] 按鈕。

4. 如果**Visual Studio 封裝精靈**出現時，請選擇**下一步**按鈕**歡迎**頁面上，然後在**第 1 頁的 7**，選擇**完成** 按鈕。

     雖然**資訊清單設計工具**隨即開啟，我們將會保留這個逐步解說簡單藉由直接修改資訊清單檔案。

5. 在 **方案總管**，開啟捷徑功能表**source.extension.vsixmanifest**檔案，然後再選擇 **檢視程式碼**。 您可以使用此程式碼取代檔案中的現有內容。

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

6. 在**方案總管**，開啟捷徑功能表**SimpleMathVSIX**專案，，然後選擇**新增** > **新項目**.

7. 在 **資料**類別目錄中，選取**XML 檔案**，將檔案命名為`SDKManifest.xml`，，然後選擇 **新增** 按鈕。

8. 在 **方案總管 中**，開啟捷徑功能表**SDKManifest.xml**檔案，然後再選擇 **開啟**顯示中的檔案**XML 編輯器**.

9. 將下列程式碼加入**SDKManifest.xml**檔案。

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

10. 在 **方案總管**的捷徑功能表上**SDKManifest.xml**檔案中，選擇 **屬性**。

11. 在 **屬性**視窗中，將**Include in VSIX**屬性設 **，則為 True**。

12. 在 **方案總管 中**的捷徑功能表上**SimpleMathVSIX**專案中，選擇 **新增** > **新資料夾**，和然後將資料夾命名為`Redist`。

13. 加入子資料夾下建立此資料夾結構的可轉散發套件：

     *\Redist\CommonConfiguration\Neutral\SimpleMath\js\\*

14. 上的捷徑功能表**\js\\** 資料夾中，選擇 **新增** > **新項目**。

15. 底下**Visual C# 項目**，選取**Web**類別，然後再選取**JavaScript 檔案**項目。 將檔案命名`arithmetic.js`，然後選擇**新增** 按鈕。

16. 插入下列程式碼插入*arithmetic.js*:

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

17. 在 **方案總管**的捷徑功能表上**arithmetic.js**檔案中，選擇 **屬性**。 這些屬性變更：

    - 設定**Include in VSIX**屬性設 **，則為 True**。

    - 設定**複製到輸出目錄**屬性設**永遠複製**。

18. 在 [**方案總管] 中**的捷徑功能表上**SimpleMathVSIX**專案，選擇**建置**。

19. 建置專案的捷徑功能表上成功完成之後，選擇**在檔案總管 中開啟資料夾**。 瀏覽至**\bin\debug\\**，然後執行`SimpleMathVSIX.vsix`進行安裝。

20. 選擇**安裝** 按鈕，讓安裝完成。

21. 重新啟動 Visual Studio。

## <a name="createSampleApp"></a> 若要建立範例應用程式使用 SDK

1. 在功能表列上，選擇 [檔案] > [新增] > [專案]。

2. 在範本類別清單中下**JavaScript**，選取**Windows 市集**，然後選取**空白應用程式**範本。

3. 在 **名稱**方塊中，指定`ArithmeticUI`。 選擇 [確定]  按鈕。

4. 在 [**方案總管] 中**，開啟捷徑功能表**ArithmeticUI**專案，，然後選擇**新增** > **參考**.

5. 底下**Windows**，選擇**擴充功能**，並注意**簡單數學**隨即出現。

6. 選取 [**簡單的數學**核取方塊，然後選擇**確定**] 按鈕。

7. 在**方案總管 中**下方**參考**，注意**簡單的數學**參考會顯示。 展開它，並請注意，有**\js\\** 資料夾，其中包含**arithmetic.js**。 您可以開啟**arithmetic.js**來確認已安裝您的原始程式碼。

8. 使用下列程式碼的內容取代*default.htm*。

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

9. 使用下列程式碼的內容取代*\js\default.js*。

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

10. 內容取代*\css\default.css*以下列程式碼：

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

11. 選擇**F5**鍵，建置並執行應用程式。

12. 在應用程式 UI 中，輸入任何兩個數字，選取作業，然後選擇**=**  按鈕。 正確的結果會出現。

## <a name="see-also"></a>另請參閱
- [建立軟體開發套件](../extensibility/creating-a-software-development-kit.md)
