---
title: MSSCCPRJ.SCC 檔 |微軟文件
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
ms.openlocfilehash: 89511b7c8b69c5793eceef7d58153dde253a4f47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702473"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ.SCC 檔
當您使用 IDE 將 Visual Studio 解決方案或專案置於原始碼管理之下時,IDE 會收到兩個關鍵資訊。 資訊來自以字串形式形式的原始程式碼管理外掛程式。 這些字串「AuxPath」和「ProjName」對 IDE 不透明,但外掛程式會使用這些字串在版本控制項中尋找解決方案或專案。 IDE 通常透過呼叫[SccGetProjPath](../extensibility/sccgetprojpath-function.md)第一次取得這些字串,然後將它們儲存在解決方案或專案檔中,以便將來呼叫[SccOpenProject](../extensibility/sccopenproject-function.md)。 嵌入解決方案和專案檔時,「AuxPath」和「ProjName」字串不會自動更新,當使用者分支、分叉或複製版本控制中的解決方案和專案檔時。 為了確保解決方案和專案檔指向其在版本控制件中的正確位置,用戶必須手動更新字串。 由於字串是不透明的,因此並不總是清楚應如何更新它們。

 原始程式管理外掛程式可以透過將「AuxPath」和「ProjName」字串儲存在稱為*MSSCCPRJ.SCC*檔的特殊文件中來避免此問題。 它是一個本地的用戶端檔,由外掛程式擁有和維護。 此文件永遠不會置於原始程式碼管理之下,但由包含原始程式碼管理檔的每個目錄的外掛程式生成。 要確定哪些檔案是 Visual Studio 解決方案和專案檔,原始程式碼管理外掛程式可以將檔案擴展名與標準或使用者提供的清單進行比較。 一旦 IDE 檢測到外掛程式支援*MSSCCPRJ.SCC*檔,它將停止將「AuxPath」和「ProjName」字串嵌入到解決方案和專案檔中,而是從*MSSCCPRJ.SCC*檔中讀取這些字串。

 支援*MSSCCPRJ.SCC*檔的原始程式碼管理外掛程式必須遵守以下準則:

- 每個目錄只能有一個*MSSCCPRJ.SCC*檔。

- *MSSCCPRJ.SCC*檔可以包含給定目錄中受原始程式碼管理中的多個檔的「輔助路徑」和「ProjName」。

- "輔助路徑"字串內不得有引號。 它允許它周圍具有引號作為分隔符(例如,一對雙引號可用於指示空字串)。 從*MSSCCPRJ.SCC*檔讀取"輔助路徑"字串時,IDE 將刪除其所有引號。

- MSSCCPRJ 中的「ProjName」字串 *。SCC 文件*必須與從函數`SccGetProjPath`返回的 字串完全匹配。 如果函數返回的字串周圍有引號,*則 MSSCCPRJ.SCC*檔中的字串必須圍繞它具有引號,反之亦然。

- 每當檔置於原始程式碼管理之下時,都會創建或更新*MSSCCPRJ.SCC*檔。

- 如果*MSSCCPRJ.SCC*檔被刪除,提供程式應在下次執行有關該目錄的原始程式碼管理操作時重新生成該檔。

- *MSSCCPRJ.SCC*文件必須嚴格遵守定義的格式。

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>MSSCCPRJ 的插圖。SCC 檔案格式
 下面是*MSSCCPRJ.SCC*檔格式的範例(行號僅作為指南提供,不應包含在檔正文中):

- [第1行]`SCC = This is a Source Code Control file`

- [第2行]

- [第3行]`[TestApp.sln]`

- [第4行]`SCC_Aux_Path = "\\server\vss\"`

- [第5行]`SCC_Project_Name = "$/TestApp"`

- [第6行]

- [第7行]`[TestApp.csproj]`

- [第8行]`SCC_Aux_Path = "\\server\vss\"`

- [第9行]`SCC_Project_Name = "$/TestApp"`

 第一行表示檔的用途,並用作此類型所有檔的簽名。 此行應在所有*MSSCCPRJ.SCC*檔中完全一樣顯示:

 `SCC = This is a Source Code Control file`

 以下部分詳細介紹了每個檔的設置,這些設置以方括弧中的檔名標記。 對於要跟蹤的每個檔,將重複此部分。 這個行是檔案名的範例,`[TestApp.csproj]`即 。 IDE 需要以下兩行。 但是,它不定義定義的值的樣式。 變數是`SCC_Aux_Path`與`SCC_Project_Name`。

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 此部分沒有結束分隔符。 檔案的名稱以及檔中出現的所有文本都在 scc.h 標頭檔中定義。 有關詳細資訊,請參閱[用作搜尋原始碼管理外掛程式的字串](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)。

## <a name="see-also"></a>另請參閱
- [原始程式管理外掛程式](../extensibility/source-control-plug-ins.md)
- [以找原始碼管理外掛程式鍵](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
