---
title: MSSCCPRJ.SCC.SCC 檔案 |Microsoft Docs
description: 深入瞭解 MSSCCPRJ.SCC。SCC 檔，這是原始檔控制外掛程式所使用的本機用戶端檔案，可搭配 Visual Studio SDK 使用。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 253482f840350ae1d3cf7ee83e03a88ace15a6cd
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863477"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ.SCC.SCC 檔案
當您使用 IDE 在原始檔控制下放置 Visual Studio 的方案或專案時，IDE 會收到兩個重要的資訊片段。 此資訊來自原始檔控制外掛程式的字串格式。 這些字串 "AuxPath" 和 "ProjName" 對 IDE 而言是不透明的，但外掛程式會使用它們來尋找版本控制中的方案或專案。 IDE 通常會藉由呼叫 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)來取得這些字串，然後將它們儲存在方案或專案檔中，以供未來對 [SccOpenProject](../extensibility/sccopenproject-function.md)的呼叫使用。 內嵌在方案和專案檔中時，當使用者分支、派生或複製版本控制中的方案和專案檔時，不會自動更新 "AuxPath" 和 "ProjName" 字串。 為了確保方案和專案檔指向版本控制中的正確位置，使用者必須手動更新字串。 因為這些字串是不透明的，不一定會清楚應如何更新。

 原始檔控制外掛程式可以將 "AuxPath" 和 "ProjName" 字串儲存在稱為 *mssccprj.scc* 的特殊檔案中，以避免這個問題。 它是由外掛程式所擁有及維護的本機用戶端檔案。 這個檔案永遠不會放置在原始檔控制下，而是由外掛程式針對包含原始檔控制檔案的每個目錄所產生。 為了判斷哪些檔案是 Visual Studio 方案和專案檔，原始檔控制外掛程式可以比較檔案延伸與標準或使用者提供的清單。 一旦 IDE 偵測到外掛程式支援 *MSSCCPRJ.SCC SCC* 檔案，它就會停止將 "AuxPath" 和 "ProjName" 字串內嵌到方案和專案檔中，而是改為從 *mssccprj.scc* 檔中讀取這些字串。

 支援 *mssccprj.scc* 的原始檔控制外掛程式必須遵守下列指導方針：

- 每個目錄只能有一個 *mssccprj.scc 的 SCC* 檔。

- *Mssccprj.scc 的 SCC* 檔案可以包含在指定目錄內的原始檔控制下的多個檔案的 "AuxPath" 和 "ProjName"。

- "AuxPath" 字串中不能有引號。 您可以用引號括住它作為分隔符號 (例如，可以使用成對的雙引號來表示) 的空字串。 從 *mssccprj.scc* 檔案讀取時，IDE 會從 "AuxPath" 字串中去除所有引號。

- Mssccprj.scc 中的 "ProjName" 字串 *。SCC* 檔必須完全符合函式所傳回的字串 `SccGetProjPath` 。 如果函式所傳回的字串有引號，則 *mssccprj.scc* 檔中的字串必須用引號括住，反之亦然。

- 每次在原始檔控制下放置檔案時，就會建立或更新 *mssccprj.scc 的 SCC* 檔。

- 如果 *mssccprj.scc 的 SCC* 檔案遭到刪除，則提供者應該在下次執行與該目錄有關的原始檔控制作業時，重新產生此檔案。

- *Mssccprj.scc 的 SCC* 檔必須嚴格遵循定義的格式。

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>MSSCCPRJ.SCC 的圖例。SCC 檔案格式
 以下是 *mssccprj.scc* 的範例檔案格式 (行號只提供作為指南，不應該包含在檔案主體) 中：

- [行 1] `SCC = This is a Source Code Control file`

- [第2行]

- [第3行] `[TestApp.sln]`

- [第4行] `SCC_Aux_Path = "\\server\vss\"`

- [第5行] `SCC_Project_Name = "$/TestApp"`

- [第6行]

- [第7行] `[TestApp.csproj]`

- [第8行] `SCC_Aux_Path = "\\server\vss\"`

- [第9行] `SCC_Project_Name = "$/TestApp"`

 第一行指出檔案的用途，並做為此類型之所有檔案的簽章。 這一行在所有 *mssccprj.scc 的 SCC* 檔案中看起來應該像這樣：

 `SCC = This is a Source Code Control file`

 下一節將詳細說明每個檔案的設定，以方括弧括住的檔案名。 每個要追蹤的檔案都會重複此區段。 這一行是檔案名的範例，亦即 `[TestApp.csproj]` 。 IDE 預期會有下列兩行。 但是，它並不會定義定義之值的樣式。 變數為 `SCC_Aux_Path` 和 `SCC_Project_Name` 。

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 此區段沒有結尾分隔符號。 檔案的名稱以及出現在檔案中的所有常值，都是在 scc 標頭檔中定義。 如需詳細資訊，請參閱 [用來尋找原始檔控制外掛程式之索引鍵的字串](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)。

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
- [用來作為用來尋找原始檔控制外掛程式之索引鍵的字串](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
