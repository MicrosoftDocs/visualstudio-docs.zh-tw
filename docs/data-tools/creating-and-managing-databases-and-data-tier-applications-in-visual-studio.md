---
title: 資料庫專案、 伺服器專案和 Visual Studio 中的 DAC 專案
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6ca08103614989ddbfd096a08a1531e756c9f67c
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176098"
---
# <a name="database-projects-and-data-tier-applications-in-visual-studio"></a>資料庫專案和 Visual Studio 中的資料層應用程式

您可以使用資料庫專案來建立新的資料庫，新的資料層應用程式 (Dac)，並更新現有的資料庫和資料層應用程式。 資料庫專案和 DAC 專案，可讓您將版本控制和專案管理技術套用至您的資料庫開發工作中，相同的方式將這些技術套用至 managed 或原生程式碼中。 您可以協助您的開發小組藉由建立 DAC 專案，資料庫專案或伺服器專案，並將它放在版本控制下管理資料庫和資料庫伺服器的變更。 您的小組成員可以簽出、 建置，然後在隔離式的開發環境或沙箱中測試變更，與小組共用它們之前的檔案。 為了協助確保程式碼品質，您的小組可以完成，並在預備環境中測試所有變更的特定版本的資料庫，然後再部署到生產環境的變更。

如需支援的資料層應用程式的資料庫功能的清單，請參閱 <<c0> [ 資料層應用程式中支援的功能](/previous-versions/visualstudio/visual-studio-2010/ee362013(v=vs.100))。 如果您使用您的資料庫中不支援的資料層應用程式的功能，您應該改為使用資料庫專案，來管理您的資料庫變更。

## <a name="common-high-level-tasks"></a>常見的高層級工作

|高層級的工作|支援內容|
|----------------------|------------------------|
|**開始的資料層應用程式的開發工作：** DAC 是一種所引進的新概念[!INCLUDE[sskatmai_r2](../data-tools/includes/sskatmai_r2_md.md)]，其中包含定義[!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]資料庫，並支援執行個體所使用的用戶端-伺服器或 3 層式架構的物件應用程式。 DAC 包含資料庫物件，例如資料表和檢視表，以及執行個體的實體，例如登入。 您可以使用 Visual Studio 建立 DAC 專案，建置 DAC 封裝檔案，並將該 DAC 封裝檔案傳送至部署的執行個體上的資料庫管理員[!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]資料庫引擎。|-   [建立和管理資料層應用程式](http://go.microsoft.com/fwlink/?LinkId=160741)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|
|**執行反覆的資料庫開發：** 如果您是開發人員或測試人員，您簽出專案的組件，並加以隔離式的開發環境中更新。 透過這種環境，您可以測試您的變更，而不會影響小組的其他成員。 完成變更之後，您會檢查回版本控制，讓其他小組成員可以取得您的變更和建構並將其部署至測試伺服器的檔案。|-   [查詢與文字編輯器 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327)<br />-   [TRANSACT-SQL 偵錯工具](http://go.microsoft.com/fwlink/?LinkId=227324)|
|**建立原型，正在驗證測試結果，並修改資料庫指令碼和物件：** 您可以使用[!INCLUDE[tsql](../data-tools/includes/tsql_md.md)]執行任一這些常見工作的編輯器。|-   [查詢與文字編輯器 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327)|

## <a name="see-also"></a>另請參閱

- [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)
