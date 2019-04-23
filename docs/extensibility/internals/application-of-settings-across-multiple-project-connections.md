---
title: 跨多個專案連接設定的應用程式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6dbc2638fa23a1e0c7bf1301c3c978a1ef864c75
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60074095"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>跨多個專案連接設定的應用程式
使用原始檔控制外掛程式 API 版本 1.2，建置可以跨多個專案或多個連接內容中執行相同的原始檔控制作業批次作業使用原始檔控制外掛程式。 批次可以用於去除多餘]、 [每個專案的使用者經驗的對話方塊。

 如果使用者選取多個屬於多個連接原始檔控制外掛程式在使用原始檔控制外掛程式 API 版本 1.1 （比方說，在不同的檔案共用的電腦上兩個 「 web 專案 」） 所建置的項目，並簽出，則使用者會看到相同對話方塊的 重複。 即使在使用者按一下，就會發生此情況**套用到全部**核取方塊，在對話方塊中，因為 IDE 會重設其狀態，針對每個連接內容。

## <a name="new-capability-flag"></a>新的功能旗標
 `SccBeginBatch`函式集`SCC_CAP_BATCH`旗標，表示批次作業正在進行中。

## <a name="new-functions"></a>新的函式
下列新函數支援批次作業：

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

`SCCBeginBatch`函式會啟動一組原始檔控制作業。 `SccEndBatch`函式會關閉該群組。 可能不是巢狀群組。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 版本 1.2 中最新消息](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)