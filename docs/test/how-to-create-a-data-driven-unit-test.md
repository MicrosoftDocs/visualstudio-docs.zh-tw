---
title: 建立資料驅動的單元測試
description: 瞭解如何使用適用于 managed 程式碼的 Microsoft 單元測試架構來設定單元測試方法，以從資料來源取出值。
ms.custom: SEO-VS-2020
ms.date: 05/08/2019
ms.topic: how-to
f1_keywords:
- vs.test.testresults.unittest.datadriven
- vs.test.testresults.unittest.datadriven.failure
helpviewer_keywords:
- unit tests, running
- unit tests, data-driven
- data-driven unit tests
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 31e1fb08d77992e6fb592e286553196928b13ad4
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441192"
---
# <a name="how-to-create-a-data-driven-unit-test"></a>如何：建立資料驅動型單元測試

使用適用於受控碼的 Microsoft 單元測試架構，設定單元測試方法來從資料來源擷取值。 這個方法會針對資料來源中每個資料列依序執行，讓您輕鬆地用單一方法來測試各種輸入。

建立資料驅動型單元測試包含下列步驟︰

1. 建立資料來源，其中包含您在測試方法中使用的值。 資料來源可以是已註冊在執行測試之電腦上的任何類型。

2. 將私用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> 欄位和公用 `TestContext` 屬性新增至測試類別。

3. 建立單元測試方法，並在其中新增 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> 屬性。

4. 使用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> 索引子屬性，以擷取您在測試中使用的值。

## <a name="the-method-under-test"></a>受測方法

例如，假設我們具有：

1. 名為 `MyBank` 的方案，可接受並處理不同帳戶類型的交易。

2. 在 `MyBank` 中名為 `BankDb` 的專案，負責管理帳戶的交易。

3. `BankDb` 專案中名為 `Maths` 的類別，可執行數學函式以確保所有交易都是對銀行有利的。

4. 名為 `BankDbTests` 的單元測試專案，用來測試 `BankDb` 元件的行為。

5. 名為 `MathsTests` 的單元測試類別，用來驗證 `Maths` 類別的行為。

我們將會測試 `Maths` 中的一個方法，該方法會使用迴圈新增兩個整數：

```csharp
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

## <a name="create-a-data-source"></a>建立資料來源

若要測試 `AddIntegers` 方法，請建立一個資料來源，其中會指定參數的值範圍，以及您預期將傳回的總和。 在範例中，我們將建立名為 `MathsData` 的 SQL 壓縮資料庫，和名為 `AddIntegersData` 的資料表，其中包含下列資料行名稱和值

|FirstNumber|SecondNumber|總和|
|-|------------------|-|
|0|1|1|
|1|1|2|
|2|-3|-1|

## <a name="add-a-testcontext-to-the-test-class"></a>將 TestContext 新增至測試類別

單元測試架構會建立 `TestContext` 物件來儲存資料驅動型測試的資料來源資訊。 架構接著會設定此物件作為我們建立的 `TestContext` 屬性值。

```csharp
private TestContext testContextInstance;
public TestContext TestContext
{
    get { return testContextInstance; }
    set { testContextInstance = value; }
}
```

在測試方法中，您可以透過 `TestContext` 的 `DataRow` 索引子屬性來存取資料。

> [!NOTE]
> .NET Core 不支援 [DataSource](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute) 屬性。 若您嘗試在 .NET Core 或 UWP 單元測試專案中透過此方式存取測試資料，您將會看到與以下內容相似的錯誤：**"'TestContext' 沒有包含 'DataRow' 的定義，也找不到接受型別為 'TextContext' 第一個引數的可存取擴充方法 (您是否遺漏使用指示詞或組件參考？)"**。

## <a name="write-the-test-method"></a>撰寫測試方法

`AddIntegers` 的測試方法相當簡單。 針對資料來源中的每個資料列，請使用 **FirstNumber** 和 **SecondNumber** 資料行值作為參數呼叫 `AddIntegers`，並針對 **Sum** 資料行值驗證傳回值：

```csharp
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

`Assert` 方法包含顯示失敗之反覆項目的 `x`和 `y` 值。 根據預設，判斷提示的值 (`expected` 和 `actual`) 都已包含在失敗的測試詳細資料中。

### <a name="specify-the-datasourceattribute"></a>指定 DataSourceAttribute

`DataSource` 屬性會指定資料來源的連接字串，以及您用於測試方法中的資料表名稱。 連接字串的確切資訊視您所使用的資料來源類型而有所不同。 在此範例中，我們使用了 SqlServerCe 資料庫。

```csharp
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]
```

DataSource 屬性有三個建構函式。

```csharp
[DataSource(dataSourceSettingName)]
```

具有一個參數的函式會使用儲存在方案之 *app.config* 檔案中的連接資訊。 *dataSourceSettingsName* 是組態檔中用來指定連接資訊的 XML 項目名稱。

使用 *app.config* 檔可讓您變更資料來源的位置，而不需要對單元測試本身進行變更。 如需有關如何建立和使用 *app.config* 檔案的詳細資訊，請參閱 [逐步解說：使用設定檔定義資料來源](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)

```csharp
[DataSource(connectionString, tableName)]
```

具有兩個參數的 `DataSource` 建構函式指定資料來源的連接字串，以及包含測試方法資料的資料表名稱。

連接字串取決於資料來源的類型，但應該包含指定資料提供者非變異名稱的 Provider 元素。

```csharp
[DataSource(
    dataProvider,
    connectionString,
    tableName,
    dataAccessMethod
    )]
```

### <a name="use-testcontextdatarow-to-access-the-data"></a>使用 TestContext.DataRow 存取資料

若要存取 `AddIntegersData` 資料表中的資料，您要使用 `TestContext.DataRow` 索引子。 `DataRow` 是 <xref:System.Data.DataRow> 物件，因此請透過索引或資料行名稱來擷取資料行值。 因為值會以物件傳回，請將它們轉換為適當類型：

```csharp
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
```

## <a name="run-the-test-and-view-results"></a>執行測試並檢視結果

當您完成撰寫測試方法後，就可建置測試專案。 測試方法會顯示於 [測試總管] 中的 [未執行的測試] 群組。 當您執行、撰寫及重新執行測試時，[ **測試瀏覽器** ] 會將結果顯示為 **失敗的測試** 群組、通過的 **測試**，而 **不是執行測試**。 您可以選擇 [全部執行]  以執行所有測試，或選擇 [執行]  以選擇要執行的一小組測試。

[測試總管] 頂端的測試結果列會隨您的測試回合產生動畫效果。 在測試回合結束時，如果所有的測試都通過，狀態列會變成綠色，如果有任何測試失敗則變成紅色。 測試回合的摘要會顯示在 [ **測試瀏覽器** ] 視窗底部的詳細資料窗格中。 在底部窗格中選取某個測試以檢視該測試的詳細資料。

> [!NOTE]
> 每個資料的資料列都會有結果，也會有一個摘要結果。 如果資料的每個資料列都測試通過，執行的摘要會顯示為 **通過**。 如果有任何資料列測試失敗，執行的摘要會顯示為 **失敗**。

如果您執行我們範例中的 `AddIntegers_FromDataSourceTest` 方法，結果列會變成紅色，而測試方法會移至 [失敗的測試]。 如果來自資料來源的任何反覆執行方法失敗，資料驅動的測試將會失敗。 當您在 [ **測試瀏覽器** ] 視窗中選擇失敗的資料驅動測試時，[詳細資料] 窗格會顯示資料列索引所識別之每個反復專案的結果。 在本範例中，它會顯示 `AddIntegers` 演算法並未正確處理負數值。

當受測方法已修正並重新執行測試時，結果列會變成綠色，且測試方法會移動到 [通過的測試] 群組。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>
- [對程式碼進行單元測試](../test/unit-test-your-code.md)
- [使用測試總管執行單元測試](../test/run-unit-tests-with-test-explorer.md)
- [使用 Microsoft 單元測試架構撰寫適用於 .NET 的單元測試](../test/unit-test-your-code.md)
