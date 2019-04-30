---
title: 建立和管理資料庫和資料層應用程式
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d6cb4a3beb12d2b33b8b13441df66116fe449d09
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431149"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>建立和管理資料庫和 Visual Studio 中的資料層應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

重要事項]
> 資料庫專案所包含的舊版[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]現已提供在[!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)]工具。 如需詳細資訊，請參閱 < [SQL Server Developer Tools](http://go.microsoft.com/fwlink/?LinkId=228126)。

 您可以使用資料庫專案來建立新的資料庫，新的資料層應用程式 (Dac)，並更新現有的資料庫和資料層應用程式。 資料庫專案和 DAC 專案，可讓您將版本控制和專案管理技術套用至您的資料庫開發工作中，相同的方式將這些技術套用至 managed 或原生程式碼中。 您可以協助您建立來管理對資料庫和資料庫伺服器的開發團隊*DAC 專案*，*資料庫專案*，或有*伺服器專案*並放到在版本控制。 您的小組成員可以簽出檔案進行、 建置和測試中的變更*隔離式的開發環境*，或沙箱，與小組共用它們之前。 為了協助確保程式碼品質，您的小組可以完成，並在預備環境中測試所有變更的特定版本的資料庫，然後再部署到生產環境的變更。

 如需支援的資料層應用程式的資料庫功能的清單，請參閱 <<c0> [ 資料層應用程式中支援的功能](http://go.microsoft.com/fwlink/?LinkId=164239)Microsoft 網站上。 如果您使用您的資料庫中不支援的資料層應用程式的功能，您應該改為使用資料庫專案，來管理您的資料庫變更。

## <a name="common-high-level-tasks"></a>常見的高層級工作

|高層級的工作|支援內容|
|----------------------|------------------------|
|**開始資料層應用程式的開發的工作：** DAC 是一種所引進的新概念[!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)]，其中包含定義[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]資料庫，並支援執行個體所使用的用戶端-伺服器或 3 層式架構應用程式的物件。 DAC 包含資料庫物件，例如資料表和檢視表，以及執行個體的實體，例如登入。 您可以使用[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]若要建立 DAC 專案，建置 DAC 封裝檔案，並將該 DAC 封裝檔案傳送至部署的執行個體上的資料庫管理員[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]資料庫引擎。|-   [建立和管理資料層應用程式](http://go.microsoft.com/fwlink/?LinkId=160741)（Microsoft 網站上）<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|
|**執行反覆的資料庫開發：** 如果您是開發人員或測試人員，您簽出專案的組件，然後再將它們更新隔離式的開發環境中。 透過這種環境，您可以測試您的變更，而不會影響小組的其他成員。 完成變更之後，您會檢查回版本控制，讓其他小組成員可以取得您的變更和建構並將其部署至測試伺服器的檔案。|-   [查詢與文字編輯器 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) （Microsoft 網站上）<br />-   [TRANSACT-SQL 偵錯工具](http://go.microsoft.com/fwlink/?LinkId=227324)（Microsoft 網站上）|
|**建立原型，正在驗證測試結果，並修改資料庫指令碼和物件：** 您可以使用[!INCLUDE[tsql](../includes/tsql-md.md)]執行任一這些常見工作的編輯器。|-   [查詢與文字編輯器 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) （Microsoft 網站上）|

## <a name="see-also"></a>另請參閱
 [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)
