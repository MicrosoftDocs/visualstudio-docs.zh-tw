---
title: "Creating and Managing Databases and Data-tier Applications in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing change, databases"
  - "database features of Visual Studio, managing change"
  - "databases, managing change"
  - "managing change, database servers"
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 37
caps.handback.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating and Managing Databases and Data-tier Applications in Visual Studio
> [!IMPORTANT]
>  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 包括舊版的資料庫專案中 [!INCLUDE[sql_Denali_long](../data-tools/includes/sql_denali_long_md.md)] 工具現在提供。  如需詳細資訊， [SQL Server 開發人員工具](http://go.microsoft.com/fwlink/?LinkId=228126)請參閱  
  
 您可以使用資料庫專案建立新的資料庫、新的資料層應用程式 \(DAC\)，以及更新現有的資料庫和資料層應用程式。  資料庫專案和 DAC 專案都能讓您以套用版本控制和專案管理技術至 Managed 程式碼或機器碼的相同方式，將這些技術套用至您的資料庫開發工作。  您可以建立「*DAC 專案*」\(DAC Project\)、「*資料庫專案*」\(Database Project\) 或「*伺服器專案*」\(Server Project\)，並對專案進行版本控制，藉以協助開發小組管理資料庫和資料庫伺服器的變更。  接著，您的小組成員可以先將檔案簽出至「*隔離的開發環境*」\(Isolated Development Environment\) \(或沙箱\) 中執行、建置和測試變更，之後再與小組分享這些變更。  為了確保程式碼品質，您可以要求小組先在開發用環境中完成並測試特定資料庫版本的所有變更，之後您再將變更部署實際執行環境。  
  
 如需資料層應用程式支援資料庫功能清單，請參閱 Microsoft [在資料層應用程式所支援的功能](http://go.microsoft.com/fwlink/?LinkId=164239) 網站上。  如果您在資料庫中使用資料層應用程式不支援的功能，則應改用資料庫專案來管理資料庫的變更。  
  
## 一般高階工作  
  
|高階工作|支援內容|  
|----------|----------|  
|**開始開發資料層應用程式**：DAC 是 [!INCLUDE[sskatmai_r2](../data-tools/includes/sskatmai_r2_md.md)] 引進的新概念，包含 [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] 資料庫的定義，以及主從式架構或 3 層應用程式所使用的支援執行個體物件。  DAC 包括資料庫物件 \(例如資料表與檢視表\) 以及執行個體實體 \(例如登入\)。  您可以使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 來建立 DAC 專案、建置 DAC 封裝檔案，以及將該 DAC 封裝檔案傳送給資料庫管理員，以便部署至 [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] 資料庫引擎的執行個體上。|-   [建立並管理資料層應用程式](http://go.microsoft.com/fwlink/?LinkId=160741) \(Microsoft 網站\)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|  
|**執行反覆資料庫開發**：如果您是開發人員或測試人員，則需簽出專案的一部分，然後在隔離的開發環境中進行更新。  透過使用這種環境中，您可以測試您的變更，而不會影響小組的其他成員。  完成變更之後，再將檔案簽入版本控制中，其他小組成員就能取得您所做的變更，並將這些變更建置和部署到測試伺服器。|-   [查詢和文字編輯器 \(SQL Server Management Studio\)](http://go.microsoft.com/fwlink/?LinkId=227327) \(Microsoft 網站\)<br />-   [Transact\-SQL 偵錯工具](http://go.microsoft.com/fwlink/?LinkId=227324) \(Microsoft 網站\)|  
|**原型處理、驗證測試結果以及修改資料庫指令碼和物件**：您可以使用 [!INCLUDE[tsql](../data-tools/includes/tsql_md.md)] 編輯器來執行這些一般工作。|-   [查詢和文字編輯器 \(SQL Server Management Studio\)](http://go.microsoft.com/fwlink/?LinkId=227327) \(Microsoft 網站\)|