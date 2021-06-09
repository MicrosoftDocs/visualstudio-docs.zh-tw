---
title: 將資料來源加入至 Web 效能測試
description: 瞭解如何系結資料以提供不同的值給相同的測試，例如，為您的表單張貼參數提供不同的值。
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, data binding (database)
ms.assetid: 2ada376d-f168-455d-9643-6acb535360c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 71aa3dbf4657896093dae59451140f48f83f1622
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2021
ms.locfileid: "111761000"
---
# <a name="add-a-data-source-to-a-web-performance-test"></a>將資料來源加入至 Web 效能測試

繫結資料以提供不同的值給相同的測試，例如，提供不同的值給您的表單張貼參數。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

![將資料繫結至 Web 效能測試](../test/media/web_test_databinding_conceptual.png)

我們要使用範例 ASP.NET 應用程式。 其具有三個 .aspx 頁面：預設頁面、紅色頁面和藍色頁面。 預設頁面具有可選擇紅色或藍色的選項按鈕控制項和一個送出按鈕。 另外兩個 .aspx 頁面非常簡單。 一個具有名稱為 Red 的標籤，另一個有名稱為 Blue 的標籤。 當您在預設頁面上選取送出時，我們會顯示另外兩個之一的頁面。 您可以下載 [ColorWebApp](https://code.msdn.microsoft.com/Sample-ColorWebApp-76ff7506) 範例，或是就以您自己的 Web 應用程式跟著做。

![執行要測試的 Web 應用程式](../test/media/web_test_databinding_runwebapp.png)

您的方案也應該包括瀏覽 Web 應用程式頁面的 Web 效能測試。

![包含 Web 效能測試的方案](../test/media/web_test_databinding_solution.png)

## <a name="create-a-sql-database"></a>建立 SQL 資料庫

::: moniker range="vs-2017"

1. 如果您沒有 Visual Studio Enterprise，則可以從 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面予以下載。

2. 建立 SQL 資料庫。

     ![加入新的 SQL 資料庫](../test/media/web_test_databinding_sql_addnewdb.png)

3. 建立資料庫專案。

     ![從資料庫建立新專案](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. 將資料表加入到資料庫專案。

     ![將新資料表加入至資料庫專案](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. 將欄位加入至資料表。

     ![將欄位加入至資料表](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. 發行資料庫專案。

     ![從 [方案總管] 發行資料庫專案](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. 將資料加入至欄位。

     ![將資料加入至欄位](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. 如果您沒有 Visual Studio Enterprise，則可以從 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads)頁面予以下載。

2. 建立 SQL 資料庫。

     ![加入新的 SQL 資料庫](../test/media/web_test_databinding_sql_addnewdb.png)

3. 建立資料庫專案。

     ![從資料庫建立新專案](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. 將資料表加入到資料庫專案。

     ![將新資料表加入至資料庫專案](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. 將欄位加入至資料表。

     ![將欄位加入至資料表](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. 發行資料庫專案。

     ![從 [方案總管] 發行資料庫專案](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. 將資料加入至欄位。

     ![將資料加入至欄位](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

## <a name="add-the-data-source"></a>加入資料來源

1. 新增資料來源。

     ![將資料來源加入至 Web 效能測試](../test/media/web_test_databinding_sql_adddatasource.png)

2. 選擇資料來源的類型並命名。

     ![為資料庫來源命名](../test/media/web_test_databinding_sql_adddatasourcedialog.png)

3. 建立連線。

     ![選取 [新增連接]](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

     輸入連接詳細資料。

     ![輸入 SQL 資料庫連接屬性](../test/media/web_test_databinding_sql_adddatasourcedialogconnection.png)

4. 選取您要用於測試的資料表。

     ![加入 Color 資料表做為資料來源](../test/media/web_test_databinding_sql_adddatasourcedialogaddtable.png)

     資料表繫結至測試。

     ![已加入至 Web 效能測試的 [資料來源] 節點](../test/media/web_test_databinding_requestnodeadded_mdb.png)

5. 儲存測試。

## <a name="bind-the-data"></a>繫結資料

1. 繫結 **ColorName** 欄位。

     ![將 ColorName 欄位繫結至 RadioButtonList1 值](../test/media/web_test_databinding_sql_binddatasource.png)

2. 開啟 [方案總管] 中的 Local.testsettings 檔案，並選取 [每一資料來源資料列一次執行] 選項。

     ![編輯測試設定檔案](../test/media/web_test_databinding_sql_testsettings.png)

3. 儲存 Web 效能測試。

## <a name="run-the-test-with-the-data"></a>使用資料執行測試

1. 執行測試。

     ![執行 Web 效能測試以確認繫結](../test/media/web_test_databinding_sql_runtest.png)

     為每個資料列中顯示兩個回合。 回合 1 傳送 Red.aspx 頁面的要求，而回合 2 傳送 Blue.aspx 頁面的要求。

     ![測試回合結果](../test/media/web_test_databinding_sql_runresults.png)

     當您繫結至資料來源時，您可能違反預設回應 URL 規則。 在這種情況下，回合 2 中的錯誤是由預期原始測試記錄提供 Red.aspx 頁面的規則所造成，但是資料繫結現在會將其導向至 Blue.aspx 頁面。

2. 刪除 **回應 URL** 驗證規則並再次執行測試，即可修正驗證錯誤。

     ![刪除回應 URL 驗證規則](../test/media/web_test_databinding_sql_deleteresponseurl.png)

     Web 效能測試使用資料繫結，現在測試成功。

     ![使用資料繫結的測試可通過](../test/media/web_test_databinding_sql_deleteresponseurlrunresults.png)

## <a name="q--a"></a>問答集

### <a name="q-what-databases-can-i-use-as-a-data-source"></a>問：我可以使用哪些資料庫做為資料來源？

**答：** 您可使用下列項目：

- Microsoft SQL Azure。

- 任何版本的 Microsoft SQL Server 2005 (含) 以後版本。

- Microsoft SQL Server 資料庫檔案 (包括 SQL Express)。

- Microsoft ODBC。

- 使用 .NET Framework Data Provider for OLE DB 的 Microsoft Access 檔案。

- Oracle 7.3、8i、9i 或 10g。

### <a name="q-how-do-i-use-a-comma-separated-value-csv-text-file-as-a-data-source"></a>問：如何使用逗號分隔值 (CSV) 文字檔做為資料來源？

**答：** 方式如下：

1. 建立資料夾以組織您的專案資料庫成品並加入項目。

     ![將新項目加入至 Data 資料夾](../test/media/web_test_databinding_foldernewitem.png)

2. 建立文字檔

     ![將新的文字檔命名為 ColorData.csv](../test/media/web_test_databinding_foldernewitemtextfile.png)

3. 編輯文字檔並加入下列內容：

    ```text
    ColorId, ColorName
    0,Red
    1,Blue
    ```

4. 使用[新增資料來源](#add-the-data-source)中的步驟，但要選擇 CSV 檔案作為資料來源。

     ![輸入名稱並選擇 CSV 檔案](../test/media/web_test_databinding_adddatasourcedialog.png)

### <a name="q-what-if-my-existing-csv-file-does-not-contain-column-headers"></a>問：如果我現有的 CSV 檔未包含資料行標頭，該如何處理？

**答：** 如果無法新增資料行標頭，您可以使用結構描述檔案將 CSV 檔案當成資料庫處理。

1. 新增名為 schema.ini 的文字檔。

     ![加入 schema.ini 檔案](../test/media/web_test_databinding_schemafile.png)

2. 請編輯 schema.ini 檔案，新增可描述您資料結構的資訊。 例如，描述 CSV 檔案的結構描述檔可能像這樣：

    ```text
    [testdata.csv]
    ColNameHeader=False
    ```

3. 將資料來源加入至測試。

     ![將資料來源加入至 Web 效能測試](../test/media/web_test_databinding_sql_adddatasource.png)

4. 如果您使用 schema.ini 檔案，請選擇 [資料庫] (而非 CSV 檔案) 作為資料來源並為其命名。

     ![加入資料庫資料來源](../test/media/web_test_databinding_adddatasourcecolortext.png)

5. 建立新的連線。

     ![選取 [新增連接]](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

6. 選取 .NET Framework Data Provider for OLE DB。

     ![選取 .NET Framework OLE DB 資料提供者](../test/media/web_test_databinding_adddatasourcecolortext2.png)

7. 選擇 [ **Advanced**]。

     ![選擇 [進階]](../test/media/web_test_databinding_advanced.png)

8. 針對 [提供者] 屬性，選取 [Microsoft.Jet.OLEDB.4.0]，然後將 [擴充屬性] 設定為 [Text;HDR=NO]。

     ![套用進階屬性](../test/media/web_test_databinding_advancedproperties.png)

9. 輸入包含結構描述檔案的資料夾名稱，然後測試連接。

     ![輸入 Data 資料夾的路徑](../test/media/web_test_databinding_adddatasourcecolortext5.png)

10. 選取想要使用的 CSV 檔案。

     ![選取文字檔](../test/media/web_test_databinding_adddatasourcecolortext6.png)

     在您完成後，CSV 檔案顯示為資料表。

     ![已加入至測試的資料來源](../test/media/web_test_databinding_adddatasourcecolortext7.png)

### <a name="q-how-do-i-use-an-xml-file-as-a-data-source"></a>問：如何使用 XML 檔案做為資料來源？

**答：** 是。

1. 建立資料夾以組織您的專案資料庫成品並加入項目。

     ![將新項目加入至 Data 資料夾](../test/media/web_test_databinding_foldernewitem.png)

2. 建立 XML 檔。

     ![加入 ColorData.xml 檔案](../test/media/web_test_databinding_additemxmlfile.png)

3. 編輯 XML 檔案並加入您的資料：

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <ColorData>
        <Color>
            <ColorId>0</ColorId>
            <ColorName>Red</ColorName>
        </Color>
        <Color>
            <ColorId>1</ColorId>
            <ColorName>Blue</ColorName>
        </Color>
    </ColorData>
    ```

4. 使用[新增資料來源](#add-the-data-source)中的步驟，但要選擇 XML 檔案作為資料來源。

     ![輸入名稱並選擇 XML 檔案](../test/media/web_test_databinding_adddatasourcedialogxml.png)

### <a name="q-can-i-add-data-binding-to-a-web-service-request-that-uses-soap"></a>問：我可以將資料繫結加入至使用 SOAP 的 Web 服務要求嗎？

**答：** 是，您必須手動變更 SOAP XML。

1. 在要求樹狀結構中選擇 Web 服務要求，並在 [屬性] 視窗中選擇 [字串內容] 屬性中的省略符號 (...)。

     ![編輯 Web 服務字串內容](../test/media/web_test_databinding_webservicerequest.png)

2. 請使用下列語法，以資料繫結值取代 SOAP 主體中的值：

    ```xml
    {{DataSourceName.TableName.ColumnName}}
    ```

    例如，如果您有下列的程式碼：

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>string</userName> <password>string</password> <orderID>int</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

    您可以將其變更如下：

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>{{DataSourceName.Users.Name}}</userName> <password>{{DataSourceName.Users.Password}}</password> <orderID>{{DataSourceName.Orders.OrderID}}</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

3. 儲存測試。
