---
title: 在 Visual Studio 中使用 IntelliTest 為程式碼產生單元測試
ms.date: 2015-10-05
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateIntelliTest
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: f0ea1fa864e108117d45c1a6edd4cc03f3e3024f
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294158"
---
# <a name="generate-unit-tests-for-your-code-with-intellitest"></a>使用 IntelliTest 為程式碼產生單元測試
IntelliTest 會探索您的 .NET 程式碼，從而產生測試資料及單元測試套件。 其會為程式碼中的每一個陳述式產生一個用以執行該陳述式的測試輸入。 程式碼的每個條件分支都會執行大小寫分析。 例如，可能擲回例外狀況的 `if` 陳述式、判斷提示及所有作業都會加以分析。 這項分析會用於為每個方法的參數型單元測試產生測試資料，從而建立具有高程式碼涵蓋範圍的單元測試。

 當您執行 IntelliTest 時，您很容易就能看到哪些測試失敗，進而加入必要的程式碼來修正測試。 您可以選取產生的測試，將其儲存到測試專案中做為迴歸套件。 當您變更程式碼時，請重新執行 IntelliTest，如此所產生的測試才能與您的程式碼變更保持同步。

## <a name="availability-and-extensions"></a>可用性和延伸模組

**建立 IntelliTest** 和**執行 IntelliTest** 功能表命令︰

* 只提供於 Visual Studio 2015 及更新版本的 Enterprise Edition。

* 只支援以 .NET Framework 為目標的 C# 程式碼。

* [可擴充](#extend-framework)，並且支援 MSTest、MSTest V2、NUnit、xUnit 格式的發出測試。

* 不支援 x64 設定。

## <a name="explore-use-intellitest-to-explore-your-code-and-generate-unit-tests"></a>探索：使用 IntelliTest 探索您的程式碼並產生單元測試
 若要產生單元測試，您的類型必須是公用的。 否則，就必須先 [建立單元測試](#NoRun) 才能產生它們。

1.  在 Visual Studio 中開啟您的方案。 開啟包含您要測試之方法的類別檔案。

2.  在您程式碼中的方法上按一下滑鼠右鍵，然後選擇 [執行 IntelliTest]  ，為方法中的程式碼產生單元測試。

     ![以滑鼠右鍵按一下您的方法，以產生單元測試](../test/media/runpex.png)

     IntelliTest 會以不同的輸入多次執行您的程式碼。 每次執行都會顯示在資料表中，並指出其測試資料及最終結果或例外狀況。

     ![[瀏覽結果] 視窗會與測試一併顯示](../test/media/pexexplorationresults.png)

     若要為類別中的所有公用方法產生單元測試，只要在該類別上 (而不要在特定的方法上) 按一下滑鼠右鍵即可。 然後選擇 [執行 IntelliTest] 。 您可以利用 [瀏覽結果] 視窗中的下拉式清單，顯示類別中每個方法的單元測試及輸入資料。

     ![從清單中選取要檢視的測試結果](../test/media/selectpextest.png)

     對於成功的測試，請查看結果資料欄中的報告結果，是否符合您對程式碼的要求。 請針對失敗的測試，適當修正程式碼。 然後重新執行 IntelliTest 來驗證修正。

## <a name="persist-save-the-unit-tests-as-a-regression-suite"></a>持續：將單元測試儲存為迴歸套件

1.  選取要與參數型單元測試一併儲存到測試專案中的資料列。

     ![選取測試，再按一下滑鼠右鍵，然後選擇 [儲存]](../test/media/savepextests.png)

     您可以檢視測試專案和已建立的參數化單元測試，其中每個資料列對應的個別單元測試會儲存在測試專案的 *.g.cs* 檔案中，而參數化的單元測試會儲存在其對應的 *.cs* 檔案中。 您可以從 [測試總管] 執行這些測試及檢視其結果，與您手動建立單元測試時所執行的各項作業無異。

     ![開啟測試方法中的類別檔案，以檢視單元測試](../test/media/testmethodpex.png)

     所有必要的參考也會一併加入測試專案中。

     當方法程式碼有所變更時，請重新執行 IntelliTest，如此單元測試才會與變更保持同步。

## <a name="assist-use-intellitest-to-focus-code-exploration"></a>協助：使用 IntelliTest 專注於程式碼的探索

1.  如果您有更複雜的程式碼，IntelliTest 可協助您專注探索程式碼。 例如，若您的方法在參數中設定了介面，而實作該介面的類別又不只一個，IntelliTest 會探索這些類別並回報警告。

     您可以檢視這些警告，決定您的因應對策。

     ![檢視警告](../test/media/pexviewwarning.png)

2.  當您檢查完程式碼，並確認您的測試標的之後，您可以修正警告，以選擇測試該介面時所要使用的類別。

     ![以滑鼠右鍵按一下警告，然後選擇 [修正]](../test/media/pexfixwarning.png)

     這個選擇會加入 *PexAssemblyInfo.cs* 檔案中。

     `[assembly: PexUseType(typeof(Camera))]`

3.  接著您可以重新執行 IntelliTest，並使用您剛才修正的類別，產生參數型單元測試及測試資料。

     ![重新執行 IntelliTest，以產生測試資料](../test/media/pexwarningsfixed.png)

## <a name="specify-use-intellitest-to-validate-correctness-properties-that-you-specify-in-code"></a>指定：使用 IntelliTest 來驗證您在程式碼中指定之屬性的正確性

指定輸入和輸出之間的一般關聯性，以用產生的單元測試來驗證。 此規格的封裝方法看似測試方法，但它卻是通用數量化的規格。 這是參數化的單元測試方法，因此您所進行的任何判斷提示必須保留所有 IntelliTest 產生的可能輸入值。

##  <a name="q--a"></a>問與答

### <a name="q-can-you-use-intellitest-for-unmanaged-code"></a>問：IntelliTest 適用於 Unmanaged 程式碼嗎？

**答：** 不適用，IntelliTest 只適用於 Managed 程式碼。

### <a name="q-when-does-a-generated-test-pass-or-fail"></a>問：產生的測試會在何時成功或失敗？

**答：** 一如其他單元測試般，只要未發生任何例外狀況，測試便會成功。 當有任何判斷提示失敗，或有測試的程式擲回無法處理的例外狀況時，測試便會失敗。

 若您的測試在擲回某些例外狀況時仍能成功，可以依據您的需求，在測試方法、測試類別或組件層級設定下列屬性：

-   **PexAllowedExceptionAttribute**

-   **PexAllowedExceptionFromTypeAttribute**

-   **PexAllowedExceptionFromTypeUnderTestAttribute**

-   **PexAllowedExceptionFromAssemblyAttribute**

### <a name="q-can-i-add-assumptions-to-the-parameterized-unit-test"></a>問：我可以在參數型單元測試中加入假設嗎？

**答：** 可以，您可以使用假設，為特定方法的單元測試指定不需要的測試資料。 您可以使用 <xref:Microsoft.Pex.Framework.PexAssume> 類別加入假設。 例如，您可以如下列範例般，加入長度變數不是 Null 的假設。

 `PexAssume.IsNotNull(lengths);`

 加入假設之後，請重新執行 IntelliTest，以移除不再相關的測試資料。

### <a name="q-can-i-add-assertions-to-the-parameterized-unit-test"></a>問：我可以在參數型單元測試中加入判斷提示嗎？

**答：** 可以，IntelliTest 會在執行單元測試時，檢查陳述式中的判斷提示是否符合實際情況。 使用 <xref:Microsoft.Pex.Framework.PexAssert> 類別或測試架構隨附的判斷提示 API，以加入判斷提示。 例如，您可以加入判斷提示，指出兩個變數相等。

 `PexAssert.AreEqual(a, b);`

 當您加入判斷提示並重新執行 IntelliTest 時，其會檢查該判斷提示是否正確，若不正確，測試即會失敗。

###  <a name="NoRun"></a> 問： 是否可以產生參數化的單元測試而不需先執行 IntelliTest?

**答：** 可以，只要以滑鼠右鍵按一下類別或方法，然後選擇 [建立 IntelliTest] 即可。

 ![以滑鼠右鍵按一下編輯器，選擇 [建立 IntelliTest]](../test/media/pexcreateintellitest.png)

 接受預設格式以產生測試，或變更專案和測試的命名方式。 您可以建立新的測試專案，或將您的測試儲存至現有的專案。

 ![以 MSTest 預設值建立 IntelliTest](../test/media/pexcreateintellitestmstest.png)

<a name="extend-framework"></a>
### <a name="q-can-i-use-other-unit-test-frameworks-with-intellitest"></a>問： 是否可以使用其他單元測試架構搭配 IntelliTest？

**答：** 可以，請遵循 [尋找並安裝其他架構](../test/install-third-party-unit-test-frameworks.md)中的步驟。
Visual Studio Marketplace 也提供測試架構延伸模組︰

* [測試產生器的 NUnit 延伸模組](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension-18371)
* [測試產生器的 xUnit.net 延伸模組](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)


重新啟動 Visual Studio 並重新開啟方案之後，以滑鼠右鍵按一下類別或方法，然後選擇 [建立 IntelliTest] 。 於此處選取您已安裝的架構：

![選取 IntelliTest 的其他單元測試架構](../test/media/pexcreateintellitestextensions.png)

然後執行 IntelliTest，以在對應的 *g.cs* 檔案中產生個別的單元測試。


### <a name="q-can-i-learn-more-about-how-the-tests-are-generated"></a>問：我可以進一步了解如何產生測試嗎？

**答：** 可以，如需高階概觀，請閱讀這篇 [部落格文章](https://blogs.msdn.microsoft.com/devops/2015/07/05/intellitest-one-test-to-rule-them-all/)。
