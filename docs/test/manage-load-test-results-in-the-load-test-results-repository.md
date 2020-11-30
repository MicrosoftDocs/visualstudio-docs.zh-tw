---
title: 管理負載測試結果
description: 瞭解如何管理負載測試期間所收集的資料，這些資料會儲存在 Load 測試結果存放庫 SQL 資料庫中。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
ms.assetid: 1cd63c4b-4f74-4133-b675-5e8fbeab25f3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ea27d94f4fbe4c0ebe81cf0153ce2e98a0789dd6
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328739"
---
# <a name="manage-load-test-results-in-the-load-test-results-repository"></a>管理負載測試結果存放庫中的負載測試結果

當您執行負載測試時，負載測試執行期間所收集到的任何資訊，都可以儲存在「負載測試結果儲存機制」(也就是 SQL 資料庫) 中。 [負載測試結果儲存機制] 含有效能計數器資料，以及已記錄之錯誤的相關資訊。 結果儲存機制資料庫是由控制器的安裝程式所建立，或是在第一次從本機執行負載測試時自動建立。 對於本機執行，如果不存在負載測試結構描述，就會自動建立資料庫。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

如果您修改了控制器的結果存放庫連接字串以使用不同的伺服器，新的伺服器就需要執行 *loadtestresultsrepository.sql* 指令檔來建立結構描述。

Visual Studio Enterprise 提供具名計數器集合，可根據技術收集常用的效能計數器。 當您在分析 IIS 伺服器、ASP.NET 伺服器或 SQL 伺服器時，這些集合都相當有用。 以計數器集合收集的所有資料，都會儲存在負載測試結果儲存機制中。

> [!IMPORTANT]
> 計數器集合與效能計數器資料不同。 效能集合是中繼資料 (Metadata)， 它定義了一組效能計數器，這些計數器的收集來源應該是執行特定角色 (例如 IIS 或 SQL Server) 的電腦。 因此這個計數器集合會是負載測試定義的一部分。 而效能計數器資料則是根據計數器集合、特定電腦之計數器集合的對應，以及取樣率來進行收集。

## <a name="sql-server-versions"></a>SQL Server 版本

若要使用負載測試，您可以使用隨 Visual Studio 一起安裝的 SQL Server Express LocalDB。 它是負載測試的預設資料庫伺服器 (包括 Microsoft Excel 整合)。 SQL Server Express LocalDB 是以程式開發人員為目標的 SQL Server Express 執行模式。 SQL Server Express LocalDB 安裝會複製啟動 SQL Server Database Engine 所需的一組最少的檔案。

如果您的小組預計會有大量的資料庫需求，或是您的專案過大而不適合使用 SQL Server Express LocalDB，則應該考慮升級至 SQL Express 或 SQL Server 完整版，以提供進一步調整的可能性。 如果您升級 SQL Server，SQL Server Express LocalDB 的 MDF 及 LDF 檔案會儲存在使用者設定檔資料夾中。 這些檔案可以用來將負載測試資料庫匯入 SQL Server Express 或 SQL Server 中。

## <a name="load-test-results-store-considerations"></a>負載測試結果存放區考量

若已安裝 Visual Studio Enterprise，則負載測試結果存放區會設定為使用電腦上所安裝的 SQL Express 執行個體。 SQL Express 最多只能使用 4GB 的磁碟空間。 如果您要長時間執行許多負載測試，就應該考慮將負載測試結果存放區設定為使用完整 SQL Server 產品的執行個體 (如果有的話)。

## <a name="load-test-analyzer-tasks"></a>負載測試分析器工作

|工作|相關主題|
|-|-----------------------|
|**設定負載測試結果儲存機制：** 您可以在 SQL 資料庫上設定負載測試結果儲存機制。 **注意：** 您也可以在安裝測試控制器時建立負載測試儲存機制。 如需詳細資訊，請參閱[安裝和設定測試代理程式](../test/lab-management/install-configure-test-agents.md)。||
|**選取及檢視結果儲存機制：** 您可以選取特定的結果儲存機制。 您不必侷限於本機結果存放區。 負載測試通常會在遠端代理程式電腦集合上執行。 從代理程式或本機電腦產生的測試結果，可以儲存在任何已經存有您所建立之負載測試結果存放區的 SQL Server 上。 在任何一種情況下，您都必須使用 [管理測試控制器] 視窗來識別要儲存負載測試結果的位置。|-   [如何：選取負載測試結果存放庫](../test/how-to-select-a-load-test-results-repository.md)<br />-   [如何：存取負載測試結果以進行分析](../test/how-to-access-load-test-results-for-analysis.md)|
|**從儲存機制中刪除負載測試結果：** 您可以使用 [開啟和管理負載測試結果] 對話方塊，從 [負載測試編輯器] 移除負載測試結果。|-   [如何：從存放庫中刪除負載測試結果](../test/how-to-delete-load-test-results-from-a-repository.md)|
|**匯入和匯出結果至儲存機制：** 您可以使用從 [負載測試編輯器] 匯入和匯出負載測試結果。|-   [如何：將負載測試結果匯入至存放庫](../test/how-to-import-load-test-results-into-a-repository.md)<br />-   [如何：從存放庫匯出負載測試結果](../test/how-to-export-load-test-results-from-a-repository.md)|

## <a name="related-tasks"></a>相關工作

[分析負載測試結果](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

您可以使用 [負載測試分析器] 來檢視執行中之負載測試和已完成之負載測試的結果。

## <a name="see-also"></a>另請參閱

- [分析負載測試結果](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [如何：存取負載測試結果以進行分析](../test/how-to-access-load-test-results-for-analysis.md)
