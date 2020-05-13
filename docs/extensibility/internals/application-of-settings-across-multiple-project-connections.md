---
title: 跨多個項目連接應用設定 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bcaed0f7f2380dd36bcbffd776839025fe9efa16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710066"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>跨一個多個項目連線設定設定
使用原始碼管理外掛程式 API 版本 1.2 建構的原始程式碼管理外掛程式可以使用批次處理操作跨多個專案或多個連接上下文執行相同的原始程式碼管理操作。 批次處理可用於從使用者體驗中消除冗餘的每個項目對話框。

 如果用戶選擇多個項屬於使用原始程式碼管理外掛程式 API 版本 1.1 構建的原始程式碼管理外掛程式中的多個連接,並檢查它們,則使用者會反覆看到同一對話方塊。 即使使用者按下對話方塊中的「**適用於所有」** 複選框,也會發生此情況,因為 IDE 會為每個連接上下文重置其狀態。

## <a name="new-capability-flag"></a>新功能旗標
 該`SccBeginBatch`函數`SCC_CAP_BATCH`設置 標誌以指示批處理操作正在進行。

## <a name="new-functions"></a>新的函式
以下新功能支援批次處理操作:

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

該`SCCBeginBatch`函數啟動一組原始程式碼管理操作。 函數`SccEndBatch`關閉組。 組可能無法嵌套。

## <a name="see-also"></a>另請參閱
- [原始程式碼管理外掛程式 API 版本 1.2 中的新增功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
