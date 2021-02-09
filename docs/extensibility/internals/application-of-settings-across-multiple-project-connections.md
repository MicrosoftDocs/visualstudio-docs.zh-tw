---
title: 將設定套用到多個專案連接
description: 瞭解如何使用原始檔控制外掛程式來執行批次作業，以將設定套用到多個專案連接上。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 14b466112e3939756142a43568ddc3107e55d659
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906094"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>跨多個專案連接的設定應用程式
使用原始檔控制外掛程式 API 版本1.2 所建立的原始檔控制外掛程式，可以使用批次作業，跨多個專案或多個連接內容執行相同的原始檔控制作業。 您可以使用批次來消除使用者體驗中的多餘、每個專案的對話方塊。

 如果使用者在使用原始檔控制外掛程式 API 版本1.1 所建立的原始檔控制外掛程式中，選取多個屬於一個以上連接的專案 (例如，不同檔案共用電腦上的兩個 Web 專案) 並簽出，則使用者會重複看到相同的對話方塊。 即使使用者在對話方塊中按一下 [套用 **到全部** ] 核取方塊，還是會發生此情況，因為 IDE 會重設其每個連接內容的狀態。

## <a name="new-capability-flag"></a>新增功能旗標
 此函式 `SccBeginBatch` `SCC_CAP_BATCH` 會設定旗標，表示批次作業正在進行中。

## <a name="new-functions"></a>新的函式
下列新函數支援批次作業：

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

`SCCBeginBatch`函數會啟動一組原始檔控制作業。 `SccEndBatch`函數會關閉群組。 這些群組可能不會被嵌套。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 版本1.2 的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
