---
title: MSSCCPRJ。SCC 檔案 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05360ca6e557ae0153715497b85792bc2fb6e2fc
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693031"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ。SCC 檔案
當您將 Visual Studio 方案或專案使用 IDE 的原始檔控制之下時，IDE 就會收到兩個關鍵資訊。 資訊是從原始檔控制外掛程式的字串形式提供。 "AuxPath 」 和 「 專案名稱 」，這些字串是不透明的 ide，但在版本控制中找出方案或專案正在使用的外掛程式。 IDE 通常呼叫以取得這些字串在第一次[SccGetProjPath](../extensibility/sccgetprojpath-function.md)，它然後未來呼叫的方案或專案檔中儲存[SccOpenProject](../extensibility/sccopenproject-function.md)。 當內嵌的方案和專案檔中，"AuxPath 」 和 「 專案名稱 」 字串不會自動更新時使用者分支、 分支，或複製會在版本控制中的方案和專案檔。 若要確定方案和專案檔會指向其版本控制中的正確位置，使用者必須手動更新的字串。 字串會是不透明，因為它可能不清楚如何已更新。

 原始檔控制外掛程式可以避免這個問題 「 AuxPath 」 和 「 專案名稱 」 字串儲存在特殊的檔案，稱為*MSSCCPRJ.SCC*檔案。 它是本機用戶端的檔案，其中擁有及維護外掛程式。 此檔案也絕不會放在原始檔控制，但會產生包含原始檔控制檔案的每個目錄的外掛程式。 若要判斷哪些檔案是 Visual Studio 方案和專案檔，原始檔控制外掛程式可以比較檔案擴充功能符合標準] 或 [使用者提供的清單。 當 IDE 偵測到外掛程式的支援*MSSCCPRJ.SCC*檔案，它會停止 「 AuxPath"和"專案名稱 」 字串嵌入方案和專案檔，並讀取從這些字串*MSSCCPRJ.SCC*改為檔案。

 原始檔控制外掛程式支援*MSSCCPRJ.SCC*檔案必須遵守下列指導方針：

-   只能有一個*MSSCCPRJ.SCC*每個目錄的檔案。

-   *MSSCCPRJ.SCC*檔案可以在指定的目錄中的原始檔控制的多個檔案包含"AuxPath 」 和 「 專案名稱 」。

-   "AuxPath"字串不能在其中的引號。 它允許有用引號括住它做為分隔符號 （例如雙引號括住一組可用來表示空字串）。 從讀取時，IDE 會移除所有 「 AuxPath"字串的引號*MSSCCPRJ.SCC*檔案。

-   「 專案名稱 」 字串*MSSCCPRJ。SCC 檔案*必須從傳回的字串完全相符`SccGetProjPath`函式。 如果函式所傳回的字串必須用引號括住的字串，它*MSSCCPRJ.SCC*檔案必須括住，反之亦然。

-   *MSSCCPRJ.SCC*檔案建立或更新時的檔案會放在原始檔控制。

-   如果*MSSCCPRJ.SCC*刪除檔案、 提供者應該重新執行有關該目錄的原始檔控制作業的下一次產生它。

-   *MSSCCPRJ.SCC*檔案必須嚴格遵循定義的格式。

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>MSSCCPRJ 圖例。SCC 檔案格式
 以下是範例*MSSCCPRJ.SCC* （行號，才會提供做為指南，和不應包含在檔案內文） 的檔案格式：

- [第 1 行] `SCC = This is a Source Code Control file`

- [第 2 行]

- [第 3 行] `[TestApp.sln]`

- [第 4 行] `SCC_Aux_Path = "\\server\vss\"`

- [第 5 行] `SCC_Project_Name = "$/TestApp"`

- [第 6 行]

- [7 行] `[TestApp.csproj]`

- [Line 8] `SCC_Aux_Path = "\\server\vss\"`

- [Line 9] `SCC_Project_Name = "$/TestApp"`

 第一行指出檔案的目的，並做為此類型的所有檔案的簽章。 這一行應該會出現完全像這樣總共*MSSCCPRJ.SCC*檔案：

 `SCC = This is a Source Code Control file`

 下一節詳細說明每個檔案，在方括號中的檔案名稱來標記的設定。 本節會針對所追蹤的每個檔案重複。 這一行是範例檔案名稱，也就是`[TestApp.csproj]`。 IDE 會預期要有下列兩行。 它不會不過，定義的樣式定義的值。 變數是`SCC_Aux_Path`和`SCC_Project_Name`。

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 這個區段沒有結尾分隔符號。 Scc.h 標頭檔中定義的檔案，以及出現在檔案中的所有常值名稱。 如需詳細資訊，請參閱 <<c0> [ 字串做為索引鍵以尋找原始檔控制外掛程式](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
- [字串做為索引鍵以尋找原始檔控制外掛程式](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)