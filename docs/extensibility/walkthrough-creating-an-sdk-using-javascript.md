---
title: 演練:使用 JAVAScript 創建 SDK |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3a3fa110bd6521443521449898474299dd267d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697497"
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>演練:使用 JavaScript 建立 SDK
本演練介紹如何使用 JAvaScript 創建簡單的數學 SDK 作為可視化工作室擴展 (VSIX)。  演練分為以下幾部分:

- [建立 SimpleMathVSIX 延伸 SDK 專案](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)

- [建立 SDK 的範例應用程式](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)

  對於 JAVAScript,沒有類庫項目類型。 在本演練中,範例*算術.js*檔直接在 VSIX 專案中創建。 實際上,我們建議您先將 JavaScript 和 CSS 檔建構並測試為 Windows 應用商店應用(例如,使用**空白應用**樣本)然後再將它們放入 VSIX 專案中。

## <a name="prerequisites"></a>Prerequisites
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 有關詳細資訊,請參閱[可視化工作室 SDK](../extensibility/visual-studio-sdk.md)。

## <a name="to-create-the-simplemathvsix-extension-sdk-project"></a><a name="createSimpleMathVSIX"></a>建立 SimpleMathVSIX 延伸 SDK 專案

1. 在選單列上,選擇 **「檔** > **新專案** > **」。。**

2. 在樣本類別清單中,在**Visual C#** 下,選擇 **「可擴充性**」,然後選擇**VSIX 專案**樣本。

3. 在 **「名稱**」 文字框`SimpleMathVSIX`中, 指定並選擇 **「 確定**」 按鈕。

4. 如果出現 **「視覺工作室包精靈」** 請選擇 **「歡迎**」頁上的 **「下一步**」按鈕,然後在**7 頁的第 1 頁**中選擇「**完成」** 按鈕。

     儘管**清單設計器**打開,但我們將通過直接修改清單檔來保持本演練簡單。

5. 在**解決方案資源管理員中**,打開**源.擴展.vsixmanifest**檔案的快捷功能表,然後選擇 **「查看代碼**」 。 使用此代碼可以替換檔中的現有內容。

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

6. 在**解決方案資源管理器**中,打開**SimpleMathVSIX**專案的快捷選單,**Add** > 然後選擇「**添加新項**」。

7. 在 **「資料」** 類別中,選擇**XML 檔**,`SDKManifest.xml`命名檔案,然後選擇「**新增**」 按鈕。

8. 在**解決方案資源管理員中**,打開**SDKManifest.xml**檔案的快捷選單,然後選擇**Open**以在 XML**編輯器**中顯示該檔。

9. 將以下代碼添加到**SDKManifest.xml**檔中。

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

10. 在**解決方案資源管理員**中,在**SDKManifest.xml**檔的快捷選單中,選擇**屬性**。

11. 在 **「屬性」** 視窗中,將**VSIX 屬性中的「包括」** 設定為 **「True」**。

12. 在 **「解決方案資源管理員**」 中, 在**SimpleMathVSIX**專案的捷徑選單上,選擇 **'新增新** > **資料夾**",然後命名`Redist`資料夾 。

13. 在 Redist 下新增子資料夾以建立此資料夾結構:

     *[紅色]通用配置\中性_簡單數學\js\\*

14. 在**\js\\**資料夾的快捷功能表上,選擇 **「添加新** > **專案**」。

15. 在**Visual C# 項**下,選擇**Web**類別,然後選擇**JavaScript 檔**項。 命名檔案`arithmetic.js`,然後選擇「**新增**」 按鈕。

16. 將以下代碼插入*到算術.js 中*:

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

17. 在**解決方案資源管理員**中,在**算術.js**檔案的快捷選單上,選擇**屬性**。 進行以下屬性變更:

    - 將**VSIX 屬性中的「包括」** 設定為 **「True」。**

    - 將 **「複製到輸出目錄」** 屬性設定為 **「始終複製**」。

18. 在**解決方案資源管理器**中,在**SimpleMathVSIX**專案的快捷功能表上,選擇 **"生成**"。

19. 生成成功完成後,在專案的快捷菜單上,在**檔案資源管理器中選擇"打開資料夾**"。 導覽到**\bin\debug,\\**`SimpleMathVSIX.vsix`然後執行以安裝它。

20. 選擇 **「安裝**」按鈕,讓安裝完成。

21. 重新啟動 Visual Studio。

## <a name="to-create-a-sample-app-that-uses-the-sdk"></a><a name="createSampleApp"></a>建立 SDK 的範例應用程式

1. 在選單列上,選擇 **「檔** > **新專案** > **」。。**

2. 在範本類別清單中,在**JAVAScript**下 ,選擇**Windows 應用商店**,然後選擇 **「空白應用」** 樣本。

3. 在 **「名稱」** 方`ArithmeticUI`塊中, 指定 。 選擇 [確定] **** 按鈕。

4. 在**解決方案資源管理器**中,打開**算術UI**專案的快捷功能表,然後選擇 **「添加** > **參考**」。。

5. 在**Windows**下,選擇**延伸**,並注意顯示**簡單數學**。

6. 選擇 **「簡單數學」** 複選框,然後選擇「**確定**」 按鈕。

7. 在**解決方案資源管理員**中 ,在**參考引用**下 ,請注意將顯示**簡單數學**引用。 展開它,並注意到有一個包含**算術.js**的**\\\js**資料夾。 您可以打開**算術.js**來確認已安裝原始碼。

8. 使用以下代碼替換*default.htm*的內容。

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

9. 使用以下代碼取代*\js_default.js 的內容*。

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

10. 將*\css_default.css*的內容取代為以下代碼:

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

11. 選擇要生成和運行應用的**F5**鍵。

12. 在應用 UI 中,輸入任意兩個數位,選擇操作,**=** 然後選擇 該按鈕。 將顯示正確的結果。

## <a name="see-also"></a>另請參閱
- [建立軟體開發套件](../extensibility/creating-a-software-development-kit.md)
