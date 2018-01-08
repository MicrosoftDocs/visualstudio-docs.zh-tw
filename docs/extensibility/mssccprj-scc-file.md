---
title: "MSSCCPRJ。SCC 檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 90a21ba6aafa0c5d06565c66531e2a6779aa419f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ。SCC 檔案
當 Visual Studio 方案或專案放置在原始檔控制使用 IDE 時，IDE 會從原始檔控制外掛程式在字串的形式接收兩項重要的資訊。 這些字串"AuxPath"和"ProjName 」，並不清楚在 IDE 中，但是會使用由外掛程式版本控制中找出方案或專案。 IDE 通常會取得這些字串第一次呼叫[SccGetProjPath](../extensibility/sccgetprojpath-function.md)，它然後未來呼叫的方案或專案檔中儲存[SccOpenProject](../extensibility/sccopenproject-function.md)。 內嵌在此方案和專案檔時，「 AuxPath"和"ProjName"字串不會自動更新使用者分支中，就會分岔，或複製會在版本控制中的方案和專案檔時。 若要確定方案和專案檔會指向其正確的位置，在版本控制中，使用者必須手動更新的字串。 字串可當做不透明，因為它不一定清楚如何他們應該更新。  
  
 原始檔控制外掛程式可以避免這個問題 「 AuxPath"和"ProjName"字串儲存在稱為 MSSCCPRJ 的特殊檔案。SCC 檔案。 它是本機用戶端的檔案，其中擁有與維護的外掛程式。 這個檔案從未開出原始檔控制之下，但是會產生的每一個目錄，包含原始檔控制檔案的外掛程式。 若要判斷哪些檔案是 Visual Studio 方案和專案檔案，原始檔控制外掛程式可以比較檔案的副檔名與標準或使用者提供的清單。 一旦 IDE 偵測到的外掛程式支援 MSSCCPRJ。SCC 檔案，它就不會內嵌"AuxPath"和"ProjName"字串至方案和專案檔，它會從 MSSCCPRJ 讀取這些字串。SCC 檔案。  
  
 原始檔控制外掛程式支援 MSSCCPRJ。SCC 檔案必須遵守下列指導方針：  
  
-   只能有一個 MSSCCPRJ。每個目錄的 SCC 檔案。  
  
-   MSSCCPRJ。SCC 檔案可以包含"AuxPath"和"ProjName 「 多個檔案所指定的目錄中的原始檔控制之下。  
  
-   「 AuxPath"字串不能在它之內的引號。 允許將雙引號括住做為分隔符號 （例如，雙引號括住的一組可用來表示空字串）。 讀取從 MSSCCPRJ 時，IDE 將帶狀所有從 「 AuxPath"字串的引號。SCC 檔案。  
  
-   MSSCCPRJ"ProjName"字串。SCC 檔案必須符合傳回的字串`SccGetProjPath`函式。 如果函式所傳回的字串引號括住它 MSSCCPRJ 中的字串。SCC 檔必須以引號括住，反之亦然。  
  
-   MSSCCPRJ。SCC 檔案建立或更新檔案會放在原始檔控制。  
  
-   如果 MSSCCPRJ。SCC 檔案被刪除，提供者應重新產生在下次執行原始檔控制作業，取得關於該目錄。  
  
-   MSSCCPRJ。SCC 檔案必須嚴格遵守定義的格式。  
  
## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>MSSCCPRJ 的圖例。SCC 檔案格式  
 以下是 MSSCCPRJ 的範例。SCC 檔案格式 （行號做為指南，僅提供和不應該包含在檔案內文）：  
  
 [第 1 行]`SCC = This is a Source Code Control file`  
  
 [第 2 行]  
  
 [第 3]`[TestApp.sln]`  
  
 [行 4]`SCC_Aux_Path = "\\server\vss\"`  
  
 [第 5 行]`SCC_Project_Name = "$/TestApp"`  
  
 [第 6 行]  
  
 [Line 7]`[TestApp.csproj]`  
  
 [第 8 行]`SCC_Aux_Path = "\\server\vss\"`  
  
 [第 9 行]`SCC_Project_Name = "$/TestApp"`  
  
 第一行狀態檔案的目的，且可做為此類型的所有檔案的簽章。 這一行應該會出現在所有 MSSCCPRJ 一模一樣。SCC 檔案：  
  
 `SCC = This is a Source Code Control file`  
  
 以下是設定每個檔案，在方括號中的檔案名稱來標記的區段。 本節會針對正在追蹤的每個檔案重複。 這一行是範例檔案名稱，也就是`[TestApp.csproj]`。 在 IDE 中，必須要有下列兩行。 它不會不過，定義的樣式定義的值。 變數是`SCC_Aux_Path`和`SCC_Project_Name`。  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 沒有任何結尾分隔符號至這個區段。 Scc.h 標頭檔中定義的檔案，為所有出現在檔案中的常值的名稱。 如需詳細資訊，請參閱[字串做為索引鍵來尋找原始檔控制外掛程式](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)。  
  
## <a name="see-also"></a>請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [用來做為索引鍵以尋找原始檔控制外掛程式的字串](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)