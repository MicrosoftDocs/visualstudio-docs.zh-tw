---
title: 資料庫專案和 DAC 專案
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- databases, managing change
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 11e60c43e2b9935f4aaf2ffcc5d5c7e3683665d1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648581"
---
# <a name="database-projects-and-data-tier-applications"></a>資料庫專案和資料層應用程式

您可以使用資料庫專案來建立新的資料庫、新的資料層應用程式（Dac），以及更新現有的資料庫和資料層應用程式。 資料庫專案和 DAC 專案都可讓您將版本控制和專案管理技術套用至資料庫開發工作，就像將這些技術套用至 managed 程式碼或機器碼一樣。 您可以藉由建立 DAC 專案、資料庫專案或伺服器專案，並將其放在版本控制之下，協助您的開發小組管理資料庫和資料庫伺服器的變更。 小組成員接著可以簽出檔案，在隔離的開發環境或沙箱中建立、建立和測試變更，然後再與小組共用。 為了協助確保程式碼品質，您的小組可以在將變更部署到生產環境之前，先完成並測試預備環境中特定資料庫版本的所有變更。

如需資料層應用程式支援的資料庫功能清單，請參閱[SQL Server 物件的 DAC 支援](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions)。 如果您在資料庫中使用資料層應用程式不支援的功能，您應該改為使用資料庫專案來管理對資料庫所做的變更。

## <a name="common-high-level-tasks"></a>常見的高層級工作

| 高階工作 | 支援內容 |
| - | - |
| **開始開發資料層應用程式：** 資料層應用程式（DAC）的概念是在 SQL Server 2008 中引進。 DAC 包含 SQL Server 資料庫的定義，以及用戶端伺服器或3層應用程式所使用的支援實例物件。 DAC 包含資料庫物件（例如資料表和 views）以及實例實體（例如登入）。 您可以使用 Visual Studio 來建立 DAC 專案、建立 DAC 封裝檔案，以及將 DAC 封裝檔案傳送給資料庫管理員，以便部署到 SQL Server database engine 的實例上。 | - [資料層應用程式](/sql/relational-databases/data-tier-applications/data-tier-applications)<br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **執行反復資料庫開發：** 開發人員可以簽出項目的各個部分，並在隔離的開發環境中加以更新。 藉由使用這種類型的環境，您可以測試變更，而不會影響小組的其他成員。 變更完成之後，您可以將檔案簽回版本控制，讓其他小組成員可以取得您的變更，並將其建立並部署到測試伺服器。 | - [專案導向的離線資料庫開發（SQL Server Data Tools）](/sql/ssdt/project-oriented-offline-database-development)<br />- [transact-sql 偵錯工具（SQL Server Management Studio）](/sql/ssms/scripting/transact-sql-debugger) |
| **原型設計、驗證測試結果，以及修改資料庫腳本和物件：** 您可以使用 Transact-sql 編輯器來執行其中任何一項一般工作。 | - [查詢與文字編輯器 (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>請參閱

- [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)