---
title: 跨多個專案的連接設定的應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0dff30ea80fb2de9bf4d90ffa48cd2f9b3d40756
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="application-of-settings-across-multiple-project-connections"></a>跨多個專案的連接設定的應用程式
使用原始檔控制外掛程式 API 1.2 建置可以跨多個專案或多個連線內容中執行相同的原始檔控制作業批次作業使用原始檔控制外掛程式。 若要刪除備援，每個專案的使用者經驗的對話方塊可用批次。  
  
 如果使用者選取多個屬於多個連接原始檔控制外掛程式在使用原始檔控制外掛程式 API 1.1，（比方說，在不同的檔案共用的電腦上兩個 「 Web 專案 」） 建置的項目，並檢查出，使用者會看到在同一個對話方塊重複。 即使在使用者按一下此時**全部套用**核取方塊，在對話方塊中，因為 IDE 會重設其狀態，針對每個連接內容。  
  
## <a name="new-capability-flag"></a>新的功能旗標  
 `SccBeginBatch` 函式設定`SCC_CAP_BATCH`旗標，表示批次作業正在進行中  
  
## <a name="new-functions"></a>新的函式  
 下列新函數支援批次作業：  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
 `SCCBeginBatch`函數啟動的原始檔控制作業群組。 `SccEndBatch` 關閉群組。 可能不是巢狀群組。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 版本 1.2 的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)