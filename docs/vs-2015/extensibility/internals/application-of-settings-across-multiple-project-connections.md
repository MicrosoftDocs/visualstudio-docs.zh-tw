---
title: 跨多個專案連接設定的應用程式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bca17fdc440fc373d0d4811ed57cd5d27a6c201a
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "58946057"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>跨多個專案連線套用設定
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

使用原始檔控制外掛程式 API 1.2，建置可以跨多個專案或多個連接內容中執行相同的原始檔控制作業批次作業使用原始檔控制外掛程式。 批次可以用於去除多餘]、 [每個專案的使用者經驗的對話方塊。  
  
 如果使用者選取多個屬於多個連接原始檔控制外掛程式在使用原始檔控制外掛程式 API 1.1 （比方說，在不同的檔案共用的電腦上兩個 「 Web 專案 」） 所建置的項目，並簽出，使用者會看到相同的對話方塊重複。 即使在使用者按一下，會發生此情況**套用到全部**核取方塊，在對話方塊中，因為 IDE 會重設其狀態，針對每個連接內容。  
  
## <a name="new-capability-flag"></a>新的功能旗標  
 `SccBeginBatch` 函式集`SCC_CAP_BATCH`旗標，表示批次作業正在進行中  
  
## <a name="new-functions"></a>新的函式  
 下列新函數支援批次作業：  
  
- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
- [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
  `SCCBeginBatch`函式會啟動一組原始檔控制作業。 `SccEndBatch` 關閉的群組。 可能不是巢狀群組。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 版本 1.2 的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
