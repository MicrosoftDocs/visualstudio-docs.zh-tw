---
title: 資料庫專案及 DAC 專案
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- databases, managing change
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: ad784e0438e0b1f02607c3cb748c759b9266dbe6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53824570"
---
# <a name="database-projects-and-data-tier-applications"></a>資料庫專案和資料層應用程式

您可以使用資料庫專案來建立新的資料庫，新的資料層應用程式 (Dac)，並更新現有的資料庫和資料層應用程式。 資料庫專案和 DAC 專案，可讓您將版本控制和專案管理技術套用至您的資料庫開發工作中，相同的方式將這些技術套用至 managed 或原生程式碼中。 您可以協助您的開發小組藉由建立 DAC 專案，資料庫專案或伺服器專案，並將它放在版本控制下管理資料庫和資料庫伺服器的變更。 您的小組成員可以簽出、 建置，然後在隔離式的開發環境或沙箱中測試變更，與小組共用它們之前的檔案。 為了協助確保程式碼品質，您的小組可以完成，並在預備環境中測試所有變更的特定版本的資料庫，然後再部署到生產環境的變更。

如需支援的資料層應用程式的資料庫功能的清單，請參閱 < [SQL Server 物件的 DAC 支援](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions)。 如果您使用您的資料庫中不支援的資料層應用程式的功能，您應該改為使用資料庫專案，來管理您的資料庫變更。

## <a name="common-high-level-tasks"></a>常見的高層級工作

| 高層級的工作 | 支援內容 |
| - | - |
| **開始資料層應用程式的開發的工作：** 使用 SQL Server 2008 引進了資料層應用程式 (DAC) 的概念。 DAC 包含 SQL Server 資料庫和支援所使用的用戶端-伺服器或 3 層式架構應用程式的執行個體物件的定義。 DAC 包含資料庫物件，例如資料表和檢視表，以及執行個體的實體，例如登入。 您可以使用 Visual Studio 建立 DAC 專案，建置 DAC 封裝檔案，並傳送給資料庫管理員的 SQL Server database engine 的執行個體上部署的 DAC 封裝檔案。 | - [資料層應用程式](/sql/relational-databases/data-tier-applications/data-tier-applications)<br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **執行反覆的資料庫開發：** 開發人員可以簽出專案的組件，並加以更新隔離式的開發環境中。 透過這種環境，您可以測試您的變更，而不會影響小組的其他成員。 完成變更之後，您會檢查回版本控制，讓其他小組成員可以取得您的變更和建構並將其部署至測試伺服器的檔案。 | - [專案導向的離線資料庫開發 (SQL Server Data Tools)](/sql/ssdt/project-oriented-offline-database-development)<br />- [TRANSACT-SQL 偵錯工具 (SQL Server Management Studio)](/sql/ssms/scripting/transact-sql-debugger) |
| **建立原型，正在驗證測試結果，並修改資料庫指令碼和物件：** 您可以使用 TRANSACT-SQL 編輯器來執行這些常見工作的任何一個。 | - [查詢與文字編輯器 (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>另請參閱

- [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)