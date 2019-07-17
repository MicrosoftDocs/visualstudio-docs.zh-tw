---
title: MSSCCPRJ。SCC 檔案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 705e0fa821000716dc9cd729901fbb7db5fd759c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194212"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ.SCC 檔案
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當 Visual Studio 方案或專案置於使用 IDE 的原始檔控制下時，IDE 會接收來自原始檔控制外掛程式的字串形式的兩項關鍵的資訊。 "AuxPath 」 和 「 專案名稱 」，這些字串是不透明的 ide，但在版本控制中找出方案或專案所使用的外掛程式。 IDE 通常會取得這些字串在第一次呼叫[SccGetProjPath](../extensibility/sccgetprojpath-function.md)，它然後未來呼叫的方案或專案檔中儲存[SccOpenProject](../extensibility/sccopenproject-function.md)。 當內嵌的方案和專案檔中，"AuxPath 」 和 「 專案名稱 」 字串不會自動更新時使用者分支、 分支，或複製會在版本控制中的方案和專案檔。 若要確定方案和專案檔會指向其版本控制中的正確位置，使用者必須手動更新的字串。 字串會是不透明，因為它可能不清楚如何已更新。  
  
 原始檔控制外掛程式可以 「 AuxPath 」 和 「 專案名稱 」 字串儲存在名為 MSSCCPRJ 的特殊檔案，以避免這個問題。SCC 檔案。 它是本機用戶端的檔案，其中擁有及維護外掛程式。 此檔案也絕不會放在原始檔控制，但會產生包含原始檔控制檔案的每個目錄的外掛程式。 若要判斷哪些檔案是 Visual Studio 方案和專案檔，原始檔控制外掛程式可以比較檔案擴充功能符合標準] 或 [使用者提供的清單。 一旦 IDE 偵測到的外掛程式支援 MSSCCPRJ。SCC 檔案，它會停止內嵌"AuxPath 」 和 「 專案名稱 」 字串到方案和專案檔，它會將這些字串讀取 MSSCCPRJ。SCC 檔案改為。  
  
 原始檔控制外掛程式支援 MSSCCPRJ。SCC 檔案必須遵守下列指導方針：  
  
- 只能有一個 MSSCCPRJ。SCC 檔案，每個目錄。  
  
- MSSCCPRJ。SCC 檔案可以包含"AuxPath 」 和 「 專案名稱 」，在指定的目錄中的原始檔控制的多個檔案。  
  
- "AuxPath"字串不能在其中的引號。 它允許有用引號括住它做為分隔符號 （例如雙引號括住一組可用來表示空字串）。 讀取從 MSSCCPRJ 時，IDE 將帶狀所有從 「 AuxPath"字串的引號。SCC 檔案。  
  
- MSSCCPRJ"專案名稱 」 字串。SCC 檔案必須從傳回的字串完全相符`SccGetProjPath`函式。 如果函式所傳回的字串必須用引號括住它 MSSCCPRJ 中的字串。SCC 檔案必須具有引號括住，反之亦然。  
  
- MSSCCPRJ。SCC 檔案建立或更新時的檔案會放在原始檔控制。  
  
- 如果 MSSCCPRJ。SCC 檔案遭到刪除，提供者應該重新執行有關該目錄的原始檔控制作業的下一次產生它。  
  
- MSSCCPRJ。SCC 檔案必須嚴格遵循定義的格式。  
  
## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>MSSCCPRJ 圖例。SCC 檔案格式  
 以下是 MSSCCPRJ 的範例。SCC 檔案格式 （行號，才會提供做為指南，和不應包含在檔案內文）：  
  
 [第 1 行] `SCC = This is a Source Code Control file`  
  
 [第 2 行]  
  
 [第 3 行] `[TestApp.sln]`  
  
 [第 4 行] `SCC_Aux_Path = "\\server\vss\"`  
  
 [第 5 行] `SCC_Project_Name = "$/TestApp"`  
  
 [第 6 行]  
  
 [7 行] `[TestApp.csproj]`  
  
 [第 8 行] `SCC_Aux_Path = "\\server\vss\"`  
  
 [第 9 行] `SCC_Project_Name = "$/TestApp"`  
  
 第一行指出檔案的目的，並做為此類型的所有檔案的簽章。 這一行應該完全像這樣在所有 MSSCCPRJ 中會出現。SCC 檔案：  
  
 `SCC = This is a Source Code Control file`  
  
 接下來是設定每個檔案，在方括號中的檔案名稱來標記區段。 本節會針對所追蹤的每個檔案重複。 這一行是範例檔案名稱，也就是`[TestApp.csproj]`。 IDE 會預期要有下列兩行。 它不會不過，定義的樣式定義的值。 變數是`SCC_Aux_Path`和`SCC_Project_Name`。  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 這個區段沒有結尾分隔符號。 Scc.h 標頭檔中定義的檔案，以及出現在檔案中的所有常值名稱。 如需詳細資訊，請參閱 <<c0> [ 字串做為索引鍵以尋找原始檔控制外掛程式](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [用來做為索引鍵以尋找原始檔控制外掛程式的字串](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
