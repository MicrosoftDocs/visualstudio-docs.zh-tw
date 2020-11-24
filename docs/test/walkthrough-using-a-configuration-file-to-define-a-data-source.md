---
title: 使用組態檔定義資料來源
description: 瞭解如何使用 app.config 檔中定義的資料來源進行單元測試，從建立定義資料來源的 app.config 檔案開始。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration files [Visual Studio ALM], defining data sources
- unit tests, walkthrough
- data sources, defining with configuration files
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06e33721fa4ac1cc657c79c8aa68b35e5ceec00b
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598493"
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>逐步解說：使用組態檔定義資料來源

這個逐步解說會示範如何使用 *app.config* 檔案中所定義的資料來源來進行單元測試。 您會學到如何建立 *app.config* 檔案，它會定義 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> 類別可以使用的資料來源。 本逐步解說將說明的工作包括下列項目：

- 建立 *app.config* 檔案。

- 定義自訂組態區段。

- 定義連接字串。

- 定義資料來源。

- 使用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> 類別存取資料來源。

## <a name="prerequisites"></a>必要條件

若要完成這個逐步解說，您需要：

- Visual Studio Enterprise

- Microsoft Access 或 Microsoft Excel，以便提供至少其中一種測試方法的資料。

- 包含測試專案的 Microsoft Visual Studio 2010 方案。

## <a name="add-an-appconfig-file-to-the-project"></a>在專案中新增 app.config 檔案

1. 如果您的測試專案中已經有 *app.config* 檔案，請移至 [定義自訂組態區段](#define-a-custom-configuration-section)。

2. 在 [方案總管] 中，以滑鼠右鍵按一下您的測試專案，然後選取 [新增] > [新增項目]。

     [新增項目] 視窗隨即開啟。

3. 選取 [應用程式組態檔] 範本，然後按一下 [新增]。

## <a name="define-a-custom-configuration-section"></a>定義自訂組態區段

檢查 *app.config* 檔案。 這個檔案至少會包含 XML 宣告和一個根項目。

### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>若要將自訂組態區段加入 app.config 檔案

1. *app.config* 的根項目應該是 **configuration** 項目。 在 **configuration** 項目內建立 **configSections** 項目。 **configSections** 應該是 *app.config* 檔案中的第一個項目。

2. 在 **configSections** 項目內建立 **section** 項目。

3. 在 **section** 項目中新增稱為 `name` 的屬性，並為它指派值 `microsoft.visualstudio.testtools`。 新增另一個稱為 `type` 的屬性，並為它指派值 `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions`。

**section** 項目應該看起來像這樣：

```xml
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions" />
```

> [!NOTE]
> 組件名稱必須符合您所使用的版本。

## <a name="define-connection-strings"></a>定義連接字串

連接字串會定義提供者存取資料來源的特定資訊。 在組態檔中定義的連接字串，可以提供能在整個應用程式中重複使用的資料提供者資訊。 在這個章節中，您會建立兩個連接字串，以供「自訂組態區段」中所定義的資料來源使用。

### <a name="to-define-connection-strings"></a>若要定義連接字串

1. 在 **configSections** 項目之後，建立 **connectionStrings** 項目。

2. 在 **connectionStrings** 項目內，建立兩個 **add** 項目。

3. 在第一個 **add** 項目中建立下列屬性和值，以連線至 Microsoft Access 資料庫：

|屬性|值|
|-|------------|
|`name`|`"MyJetConn"`|
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|
|`providerName`|`"System.Data.OleDb"`|

在第二個 **add** 項目中建立下列屬性和值，以連線至 Microsoft Excel 試算表：

|屬性|值|
|-|-|
|`name`|`"MyExcelConn"`|
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5"`|
|`providerName`|`"System.Data.Odbc"`|

**connectionStrings** 項目應該看起來像這樣：

```xml
<connectionStrings>
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
</connectionStrings>
```

## <a name="define-data-sources"></a>定義資料來源

資料來源區段會包含四個屬性，測試引擎會利用這些屬性，從資料來源中擷取資料。

- `name` 會定義 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> 所使用的識別，以指定要使用哪一個資料來源。

- `connectionString` 可識別在先前＜定義連接字串＞小節中所建立的連接字串。

- `dataTableName` 會定義測試中所使用之資料所在的資料表或工作表。

- `dataAccessMethod` 會定義存取資料來源之資料值的技巧。

在本節中，您會定義兩個將用於單元測試的資料來源。

### <a name="to-define-data-sources"></a>若要定義資料來源

1. 在 **connectionStrings** 項目之後，建立 **microsoft.visualstudio.testtools** 項目。 這個區段會建立在「定義自訂組態區段」中。

2. 在 **microsoft.visualstudio.testtools** 項目內，建立 **dataSources** 項目。

3. 在 **dataSources** 項目內，建立兩個 **add** 項目。

4. 在第一個 **add** 項目中建立下列屬性和值，以供 Microsoft Access 資料來源使用：

|屬性|值|
|-|------------|
|`name`|`"MyJetDataSource"`|
|`connectionString`|`"MyJetConn"`|
|`dataTableName`|`"MyDataTable"`|
|`dataAccessMethod`|`"Sequential"`|

在第二個 **add** 項目中建立下列屬性和值，以供 Microsoft Excel 資料來源使用：

|屬性|值|
|-|-|
|`Name`|`"MyExcelDataSource"`|
|`connectionString`|`"MyExcelConn"`|
|`dataTableName`|`"Sheet1$"`|
|`dataAccessMethod`|`"Sequential"`|

**microsoft.visualstudio.testtools** 項目應該看起來像這樣：

```xml
<microsoft.visualstudio.testtools>
    <dataSources>
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
    </dataSources>
</microsoft.visualstudio.testtools>
```

最終的 *app.config* 檔案看起來應該像這樣：

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <configSections>
        <section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions" />
    </configSections>
    <connectionStrings>
        <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
        <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
    </connectionStrings>
    <microsoft.visualstudio.testtools>
        <dataSources>
            <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
            <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
        </dataSources>
    </microsoft.visualstudio.testtools>
</configuration>
```

## <a name="create-a-unit-test-that-uses-data-sources-defined-in-appconfig"></a>使用 app.config 中所定義的資料來源建立單元測試

現在 *app.config* 檔案已經定義完成，您將建立單元測試，此單位測試會使用 *app.config* 檔案中所定義之資料來源中的資料。 在這個章節中，您將執行下列項目：

- 建立在 *app.config* 檔案中找到的資料來源。

- 使用兩個測試方法中的資料來源，它們會比較每個資料來源中的值。

### <a name="to-create-a-microsoft-access-data-source"></a>若要建立 Microsoft Access 資料來源

1. 建立名為 *testdatasource.accdb* 的 Microsoft Access 資料庫。

2. 在 *testdatasource.accdb* 中，建立資料表並將其命名為 `MyDataTable`。

3. 使用 `Number` 資料型別，在 `MyDataTable` 中建立兩個名為 `Arg1` 和 `Arg2` 的欄位。

4. 在 `MyDataTable` 中加入五個實體，分別使用下列的值做為 `Arg1` 和 `Arg2` 的值：(10,50)、(3,2)、(6,0)、(0,8) 和 (12312,1000)。

5. 儲存並關閉資料庫。

6. 變更連接字串以指向此資料庫的位置。 變更 `Data Source` 的值，使其反映資料庫的位置。

### <a name="to-create-a-microsoft-excel-data-source"></a>若要建立 Microsoft Excel 資料來源

1. 建立名為 *data.xlsx* 的 Microsoft Excel 試算表。

2. 建立名為 `Sheet1` 的工作表 (如果 *data.xlsx* 中尚無這個工作表)。

3. 在 `Sheet1` 中建立兩個資料行標頭，分別命名為 `Val1` 和 `Val2`。

4. 在 `Sheet1` 中加入五個實體，分別使用下列的值做為 `Val1` 和 `Val2` 的值：(1,1)、(2,2)、(3,3)、(4,4) 和 (5,0)。

5. 儲存並關閉試算表。

6. 變更連接字串以指向此試算表的位置。 變更 `dbq` 的值，使其反映試算表的位置。

### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>若要使用 app.config 中所定義的資料來源建立單元測試

1. 在測試專案中加入單元測試。

2. 以下列程式碼取代自動產生的單元測試內容：

    ```csharp
    using System;
    using Microsoft.VisualStudio.TestTools.UnitTesting;

    namespace TestProject1
    {
         [TestClass]
        public class UnitTest1
        {
            private TestContext context;

            public TestContext TestContext
            {
                get { return context; }
                set { context = value; }
            }

            [TestMethod()]
            [DeploymentItem("MyTestProject\\testdatasource.accdb")]
            [DataSource("MyJetDataSource")]
            public void MyTestMethod()
            {
                int a = Int32.Parse(context.DataRow["Arg1"].ToString());
                int b = Int32.Parse(context.DataRow["Arg2"].ToString());
                Assert.AreNotEqual(a, b, "A value was equal.");
            }

            [TestMethod()]
            [DeploymentItem("MyTestProject\\data.xlsx")]
            [DataSource("MyExcelDataSource")]
            public void MyTestMethod2()
            {
                Assert.AreEqual(context.DataRow["Val1"], context.DataRow["Val2"]);
            }
        }
    }
    ```

3. 檢查 DataSource 屬性。 請注意 *app.config* 檔案的設定名稱。

4. 建置您的方案，然後執行 MyTestMethod 和 MyTestMethod2 測試。

> [!IMPORTANT]
> 部署項目 (例如資料來源)，使其能供部署目錄中的測試存取。

## <a name="see-also"></a>另請參閱

- [對程式碼進行單元測試](../test/unit-test-your-code.md)
- [如何：建立資料驅動型單元測試](../test/how-to-create-a-data-driven-unit-test.md)
