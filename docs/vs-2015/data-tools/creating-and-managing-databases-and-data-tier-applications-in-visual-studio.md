---
title: 建立及管理資料庫和資料層應用程式
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b793789e092b46f14db397c1f8aef4e98544f856
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851689"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>在 Visual Studio 中建立和管理資料庫與資料層應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

重要事項]
> 舊版中包含的資料庫專案 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 現在已在 [工具] 中提供 [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] 。 如需詳細資訊，請參閱 [SQL Server Developer 工具](https://msdn.microsoft.com/library/hh272686(VS.103).aspx)。

 您可以使用資料庫專案來建立新的資料庫、新的資料層應用程式 (Dac) ，以及更新現有的資料庫和資料層應用程式。 資料庫專案和 DAC 專案都可讓您將版本控制和專案管理技術套用至資料庫開發工作，就像是將這些技術套用至 managed 程式碼或原生程式碼一樣。 您可以藉由建立 *DAC 專案*、 *資料庫專案*或 *伺服器專案* ，並將其放在版本控制之下，協助您的開發小組管理資料庫和資料庫伺服器的變更。 然後，您的小組成員可以在與小組共用之前，先簽出檔案，以在 *隔離的開發環境*或沙箱中建立、建立及測試變更。 為了協助確保程式碼的品質，您的小組可以在將變更部署至生產環境之前，先完成並測試預備環境中特定版本資料庫的所有變更。

 如需資料層應用程式所支援的資料庫功能清單，請參閱 Microsoft 網站上的 [資料層應用程式中支援的功能](https://msdn.microsoft.com/library/ee362013(VS.100).aspx) 。 如果您在資料庫中使用資料層應用程式不支援的功能，您應該改為使用資料庫專案來管理資料庫的變更。

## <a name="common-high-level-tasks"></a>一般高階工作

|高層級工作|支援內容|
|----------------------|------------------------|
|**開始開發資料層應用程式：** DAC 是引進的新概念 [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] ，其中包含資料庫的定義 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 和用戶端伺服器或3層應用程式所使用的支援實例物件。 DAC 包含資料庫物件（例如資料表和視圖），以及實例實體（例如登入）。 您可以使用建立 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dac 專案、建立 dac 封裝檔案，然後將該 dac 封裝檔案傳送給資料庫管理員，以便部署到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database engine 的實例。|-    (Microsoft 網站) [建立及管理資料層應用程式](https://msdn.microsoft.com/library/ee361996(VS.100).aspx)<br />-   [SQL Server Management Studio](https://msdn.microsoft.com/library/hh213248(SQL.110).aspx)|
|**執行反復的資料庫開發：** 如果您是開發人員或測試人員，您可以簽出項目的各個部分，然後在隔離的開發環境中加以更新。 藉由使用這種類型的環境，您可以測試您的變更，而不會影響小組的其他成員。 變更完成之後，您可以將檔案簽回版本控制，讓其他小組成員可以取得您的變更，並將其建立並部署至測試伺服器。|-   [查詢與文字編輯器 (SQL Server Management Studio) ](https://msdn.microsoft.com/library/ms173477(SQL.110).aspx) (Microsoft 網站) <br />-   [Transact-sql 偵錯工具](https://msdn.microsoft.com/library/cc645997(SQL.110).aspx) (Microsoft 網站) |
|**原型設計、驗證測試結果，以及修改資料庫腳本和物件：** 您可以使用 [!INCLUDE[tsql](../includes/tsql-md.md)] 編輯器來執行其中一項常見的工作。|-   [查詢與文字編輯器 (SQL Server Management Studio) ](https://msdn.microsoft.com/library/ms173477(SQL.110).aspx) (Microsoft 網站) |

## <a name="see-also"></a>另請參閱
 [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)
