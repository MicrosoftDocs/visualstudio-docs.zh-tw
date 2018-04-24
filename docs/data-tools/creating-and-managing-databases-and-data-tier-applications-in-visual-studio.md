---
title: 資料庫專案，伺服器專案和 Visual Studio 中的 DAC 專案
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e456d436145d859a24a224511dc69c1383bbcaeb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="database-projects-and-data-tier-applications-in-visual-studio"></a>資料庫專案和 Visual Studio 中的資料層應用程式
您可以使用資料庫專案建立新的資料庫，新的資料層應用程式 (Dac)，並且更新現有的資料庫和資料層應用程式。 資料庫專案和 DAC 專案可讓您套用至您的資料庫開發工作中相同的方式將這些技術套用至 managed 或原生程式碼中的版本控制和專案管理技術。 您可以協助您建立來管理對資料庫和資料庫伺服器的開發小組*DAC 專案*，*資料庫專案*，或*伺服器專案*並將它放置版本控制。 您的小組成員可以簽出檔案，以進行、 建置和測試中的變更*隔離式的開發環境*，或沙箱，與小組共用它們之前。 為協助確保程式碼品質，您的小組可以完成，並預備環境中測試之資料庫的特定版本的所有變更，然後再部署到實際執行環境的變更。

如需支援的資料層應用程式的資料庫功能的清單，請參閱[資料層應用程式中支援的功能](http://go.microsoft.com/fwlink/?LinkId=164239)Microsoft 網站上。 如果您使用您的資料庫中不支援的資料層應用程式的功能，您應該改為使用資料庫專案來管理您的資料庫變更。

## <a name="common-high-level-tasks"></a>高層級的一般工作

|高層級的工作|支援內容|
|----------------------|------------------------|
|**開始的資料層應用程式開發：** DAC 是引進的新概念[!INCLUDE[sskatmai_r2](../data-tools/includes/sskatmai_r2_md.md)]，其中包含定義[!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]資料庫，並支援執行個體所使用的用戶端-伺服器或 3 層物件應用程式。 DAC 包含資料庫物件，例如資料表和檢視表，以及執行個體的實體，例如登入。 您可以使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]建立 DAC 專案，建置 DAC 封裝檔案，並將 DAC 封裝檔案傳送至部署至執行個體的資料庫管理員[!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]資料庫引擎。|-   [建立和管理資料層應用程式](http://go.microsoft.com/fwlink/?LinkId=160741)（Microsoft 網站上）<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|
|**執行資料庫反覆開發：**如果您是開發人員或測試人員，您簽出專案的組件，並加以隔離式的開發環境中更新。 藉由使用這種環境，您可以測試您的變更，而不會影響小組的其他成員。 變更已完成之後，您可以檢查檔案重新加入版本控制，讓其他小組成員可以取得您的變更和建立並將其部署至測試伺服器。|-   [查詢與文字編輯器 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) （Microsoft 網站上）<br />-   [TRANSACT-SQL 偵錯工具](http://go.microsoft.com/fwlink/?LinkId=227324)（Microsoft 網站上）|
|**建立原型，驗證測試的結果，並修改資料庫指令碼和物件：**您可以使用[!INCLUDE[tsql](../data-tools/includes/tsql_md.md)]編輯器執行其中一個這些常見的工作。|-   [查詢與文字編輯器 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) （Microsoft 網站上）|

## <a name="see-also"></a>另請參閱

- [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)
