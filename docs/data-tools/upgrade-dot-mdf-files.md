---
title: "如何：升級為 LocalDB 或繼續使用 SQL Server Express | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "LocalDB"
  - "SQL Server Express"
  - "SQL Server LocalDB"
  - "SQLEXPRESS"
  - "從 SQLExpress 升級至 SQLExpress"
  - "升級至 LocalDB"
ms.assetid: 14ca6f76-f80e-4926-8020-3fee2d802b75
caps.latest.revision: 33
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 如何：升級為 LocalDB 或繼續使用 SQL Server Express
本主題說明升級資料庫檔案 \(.mdf\) 的選項，以便在安裝之後 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 並包含下列工作的指示:  
  
-   升級使用的資料庫檔案。LocalDB  
  
-   升級資料庫檔案使用 SQL Server Express 的新版本  
  
-   在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 的資料庫檔案，但保留與 [!INCLUDE[ssKatmai_exp](../data-tools/includes/sskatmai_exp_md.md)]的相容性  
  
-   執行 SQL Server Express 預設資料庫引擎  
  
 您可以使用 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 開啟包含使用 SQL Server Express，的舊版所建立的資料庫檔案的專案 \(.mdf\)  不過，繼續開發以 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]的專案，您必須先有在電腦上安裝 SQL Server Express 的版本與 Visual Studio 相同的或是必須升級資料庫檔案加入至使用 SQL Server Express LocalDB。  如果您要升級資料庫檔案，您將無法存取它與 SQL Server Express 的舊版。  
  
 您也會提示您升級使用建立 [!INCLUDE[sql_Denali_exp](../data-tools/includes/sql_denali_exp_md.md)] 的資料庫檔案，如果檔案版本與目前安裝 SQL Server Express 的執行個體。  若要解決這個問題， Visual Studio 會提示您升級檔案至 SQL Server Express 的新版本。  
  
> [!IMPORTANT]
>  建議您備份資料庫檔案，在升級之前。  
  
 在您升級資料庫之前，您應該考慮下列準則:  
  
-   如果您想要處理在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 和 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]的專案中，請勿升級。  
  
-   請勿升級，如果應用程式中使用 SQL Server Express 而不是 LocalDB 的環境。  
  
-   請勿升級，如果應用程式使用遠端連接，因為不會 LocalDB 方便他們。  
  
-   如果應用程式依賴 Internet Information Services \(IIS\)，請勿升級。  
  
-   升級"，如果您在沙箱環境中您要測試的資料庫應用程式，但不想要執行資料庫。  
  
### 升級使用的資料庫檔案。LocalDB  
  
1.  在 \[**伺服器總管**\]，選取 \[**連接到資料庫**\] 按鈕。  
  
2.  在 \[**加入資料連接**\] 對話方塊中，指定下列資訊:  
  
    -   \[**資料來源:**\] Microsoft SQL Server \(SqlClient\)  
  
    -   \[**伺服器名稱:**\] \(LocalDB\) \\ v11.0  
  
    -   \[**附加資料庫檔案:**\]*路徑*，其中 *路徑* 是主要 .mdf 檔案的實體路徑。  
  
    -   \[**邏輯名稱:**\]*名稱**名稱* ，其中是您要使用的檔案名稱。  
  
3.  選取 \[**確定**\] 按鈕。  
  
4.  當系統提示您時，請選擇 \[**是**\] 按鈕升級檔案。  
  
 資料庫升級，附加至 LocalDB 資料庫引擎和不再與 [!INCLUDE[ssKatmai_exp](../data-tools/includes/sskatmai_exp_md.md)]相容。  
  
 您也可以修改 SQLExpress 連接是透過開啟捷徑功能表"連接然後選取 \[**修改連接**\] 使用 LocalDB。  在 \[**修改連接**\] 對話方塊，變更伺服器名稱 \(\) LocalDB \\ v11.0。  在 \[**進階屬性**\] 對話方塊中，確定 \[**使用者執行個體**\] 設為 False。  
  
### 升級為 SQL Server Express 的新版本  
  
1.  在連接的捷徑功能表與資料庫，請選取 \[**修改連接**\]。  
  
2.  在 \[**修改連接**\] 對話方塊中，選取 \[**進階**\] 按鈕。  
  
3.  在 \[**進階屬性**\] 對話方塊中，選取 \[**確定**\] 按鈕，但不變更伺服器名稱。  
  
 資料庫檔案升級符合 [!INCLUDE[sql_Denali_exp](../data-tools/includes/sql_denali_exp_md.md)]版本。  
  
### 在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 的資料庫，但是會保留與 [!INCLUDE[ssKatmai_exp](../data-tools/includes/sskatmai_exp_md.md)]的相容性  
  
1.  在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]，請開啟專案，而不需要進行升級。  
  
    -   若要執行專案，請選取 F5 鍵。  
  
    -   您可以如同在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]，並做了要編輯資料庫，請開啟 \[**方案總管**\] 的 .mdf 檔案，並展開 \[**伺服器總管**\] 的節點與資料庫搭配使用。  
  
### 執行 SQL Server Express 預設資料庫引擎  
  
1.  在功能表列上的 \[\]，然後選取 \[**工具**\]， \[**選項**\]。  
  
2.  在 \[**選項**\] 對話方塊中，展開 \[**資料工具**\] \[\]，然後選取 \[**資料連接**\] 節點。  
  
3.  在 \[**SQL Server 執行個體名稱**\] 文字方塊中，指定您要使用 SQL Server Express 執行個體的名稱。  如果這個執行個體未命名，請指定 `. \SQLEXPRESS`。  
  
4.  選取 \[**確定**\] 按鈕。  
  
 SQL Server Express 將成為應用程式的預設資料庫引擎。  
  
## 請參閱  
 [區域資料概觀](../data-tools/local-data-overview.md)   
 [逐步解說：連接至本機資料庫檔案中的資料 \(Windows Form\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Local%20Database%20File%20\(Windows%20Forms\).md)