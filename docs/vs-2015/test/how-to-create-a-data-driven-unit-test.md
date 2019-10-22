---
title: 如何：建立資料驅動型單元測試 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.test.testresults.unittest.datadriven
- vs.test.testresults.unittest.datadriven.failure
helpviewer_keywords:
- unit tests, running
- unit tests, data-driven
- data-driven unit tests
ms.assetid: a0322bc5-02c8-4f9f-af43-100a60b1bd28
caps.latest.revision: 35
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b9dc5ad44a73f517b91562209abfab8b0b3e8d4a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660527"
---
# <a name="how-to-create-a-data-driven-unit-test"></a>如何：建立資料驅動型單元測試
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用適用於 Managed 程式碼的 Microsoft 單元測試架構，您就可以設定單元測試方法，從資料來源擷取用於測試方法中的值。 這個方法會針對資料來源中每個資料列依序執行，讓您輕鬆地用單一方法來測試各種輸入。

 此主題包括下列章節：

- [受測方法](../test/how-to-create-a-data-driven-unit-test.md#BKMK_The_method_under_test)

- [建立資料來源](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Creating_a_data_source)

- [將 TestContext 加入測試類別](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Adding_a_TestContext_to_the_test_class)

- [撰寫測試方法](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Writing_the_test_method)

  - [指定 DataSourceAttribute](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Specifying_the_DataSourceAttribute)

  - [使用 TestContext.DataRow 存取資料](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Using_TestContext_DataRow_to_access_the_data)

- [執行測試和檢視結果](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Running_the_test_and_viewing_results)

  建立資料驅動型單元測試包含下列步驟︰

1. 建立資料來源，其中包含您在測試方法中使用的值。 資料來源可以是已註冊在執行測試之電腦上的任何類型。

2. 將私用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> 欄位和公用 `TestContext` 屬性新增至測試類別。

3. 建立單元測試方法，並在其中新增 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> 屬性。

4. 使用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> 索引子屬性，以擷取您在測試中使用的值。

## <a name="BKMK_The_method_under_test"></a> 受測方法
 例如，假設我們已建立：

1. 名為 `MyBank` 的方案，可接受並處理不同帳戶類型的交易。

2. 在 `MyBank` 中名為 `BankDb` 的專案，負責管理帳戶的交易。

3. `DbBank` 專案中名為 `Maths` 的類別，可執行數學函式以確保所有交易都是對銀行有利的。

4. 名為 `BankDbTests` 的單元測試專案，用來測試 `BankDb` 元件的行為。

5. 名為 `MathsTests` 的單元測試類別，用來驗證 `Maths` 類別的行為。

   我們要測試 `Maths` 中的一個方法，它會使用迴圈加入兩個整數：

```
public int AddIntegers(int first, int second)
{
    int sum = first;
    for( int i = 0; i < second; i++)
    {
        sum += 1;
    }
    return sum;
}
```

## <a name="BKMK_Creating_a_data_source"></a> 建立資料來源
 若要測試 `AddIntegers` 方法，我們會建立一個資料來源，其中會指定參數的值範圍，以及您預期將傳回的總和。 在範例中，我們建立名為 `MathsData` 的 SQL 壓縮資料庫，和名為 `AddIntegersData` 的資料表，其中包含下列資料行名稱和值

|FirstNumber|SecondNumber|Sum|
|-----------------|------------------|---------|
|0|1|1|
|1|1|2|
|2|-3|-1|

## <a name="BKMK_Adding_a_TestContext_to_the_test_class"></a> 將 TestContext 加入測試類別
 單元測試架構會建立 `TestContext` 物件來儲存資料驅動型測試的資料來源資訊。 架構接著會設定此物件做為我們建立的 `TestContext` 屬性值。

```

private TestContext testContextInstance;
public TestContext TestContext
{
    get { return testContextInstance; }
    set { testContextInstance = value; }
}

```

 在測試方法中，您可以透過 `TestContext` 的 `DataRow` 索引子屬性來存取資料。

## <a name="BKMK_Writing_the_test_method"></a> 撰寫測試方法
 `AddIntegers` 的測試方法相當簡單。 針對資料來源中的每個資料列，我們使用 **FirstNumber** 和 **SecondNumber** 資料行值做為參數呼叫 `AddIntegers`，並針對 **Sum** 資料行值驗證傳回值：

```

[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0; Data Source=C:\Data\MathsData.sdf;", "Numbers")]
[TestMethod()]
public void AddIntegers_FromDataSourceTest()
{
    var target = new Maths();

    // Access the data
    int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
    int y = Convert.ToInt32(TestContext.DataRow["SecondNumber"]);
    int expected = Convert.ToInt32(TestContext.DataRow["Sum"]);
    int actual = target.IntegerMethod(x, y);
    Assert.AreEqual(expected, actual,
        "x:<{0}> y:<{1}>",
        new object[] {x, y});

}

```

 請注意，`Assert` 方法包含顯示失敗之反覆項目的 `x`和 `y` 值。 根據預設，判斷提示的值 `expected` 和 `actual` 已經包含在失敗測試的詳細資料中。

### <a name="BKMK_Specifying_the_DataSourceAttribute"></a> 指定 DataSourceAttribute
 `DataSource` 屬性會指定資料來源的連接字串，以及您用於測試方法中的資料表名稱。 連接字串的確切資訊視您所使用的資料來源類型而有所不同。 在此範例中，我們使用了 SqlServerCe 資料庫。

```
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]
```

 DataSource 屬性有三個建構函式。

```
[DataSource(dataSourceSettingName)]
```

 具有一個參數的建構函式在方案中使用 app.config 檔案中儲存的連接資訊。 *dataSourceSettingsName* 是組態檔中用來指定連接資訊的 XML 項目名稱。

 使用 app.config 檔案可讓您變更資料來源的位置，而不用變更單元測試本身。 如需如何建立和使用 app.config 檔案的資訊，請參閱[逐步解說：使用組態檔定義資料來源](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)

```
[DataSource(connectionString, tableName)]
```

 具有兩個參數的 `DataSource` 建構函式指定資料來源的連接字串，以及包含測試方法資料的資料表名稱。

 連接字串取決於資料來源的類型，但應該包含指定資料提供者非變異名稱的 Provider 元素。

```
[DataSource(
    dataProvider,
    connectionString,
    tableName,
    dataAccessMethod
    )]
```

### <a name="BKMK_Using_TestContext_DataRow_to_access_the_data"></a> 使用 TestContext.DataRow 存取資料
 若要存取 `AddIntegersData` 資料表中的資料，您要使用 `TestContext.DataRow` 索引子。 `DataRow` 是 <xref:System.Data.DataRow> 物件，因此我們透過索引或資料行名稱來擷取資料行值。 因為值會以物件傳回，我們必須將它們轉換為適當類型：

```
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);

```

## <a name="BKMK_Running_the_test_and_viewing_results"></a> 執行測試和檢視結果
 當您完成撰寫測試方法後，就可建置測試專案。 測試方法會顯示於 [測試總管] 視窗中的 [未執行的測試] 群組。 當您執行、撰寫及重新執行測試時，[測試總管] 會將結果顯示在 [失敗的測試]、[通過的測試] 和 [未執行的測試] 等群組中。 您可以選擇 [全部執行] 以執行所有測試，或選擇 [執行...] 以選擇要執行測試的子集合。

 [測試總管] 頂端的測試結果列會隨您的測試回合產生動畫效果。 在測試回合結束時，如果所有的測試都通過，狀態列會變成綠色，如果有任何測試失敗則變成紅色。 測試回合摘要會顯示在 [測試總管] 視窗底部的詳細資料窗格中。 在底部窗格中選取某個測試以檢視該測試的詳細資料。

 如果您執行範例中的 `AddIntegers_FromDataSourceTest` 方法，結果列會變成紅色，且測試方法會移動到 [失敗的測試] 中。如果任何來自資料來源的反覆執行方法失敗，資料驅動型測試就會失敗。 當您在 [測試總管] 視窗中選擇失敗的資料驅動型測試時，詳細資料窗格會顯示每個反覆項目的結果，各反覆項目是以資料列索引識別。 在本範例中，它會顯示 `AddIntegers` 演算法並未正確處理負數值。

 當受測方法已修正並重新執行測試時，結果列會變成綠色，且測試方法會移動到 [通過的測試] 群組。

## <a name="see-also"></a>請參閱
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName> <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>
 [如何：建立及執行單元測試](https://msdn.microsoft.com/5e0f43cf-5e51-48e2-9c98-0eb9324bdc48)[單元測試您的程式碼](../test/unit-test-your-code.md)[執行單元測試使用測試瀏覽器](../test/run-unit-tests-with-test-explorer.md)[使用適用于 Managed 程式碼的 Microsoft 單元測試架構來撰寫 .NET Framework 的單元](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)測試
