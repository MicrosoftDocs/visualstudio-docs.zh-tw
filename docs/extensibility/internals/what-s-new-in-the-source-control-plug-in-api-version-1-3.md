---
title: 原始&#39;檔控制外掛程式 API 版本1.3 中的新功能 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f45eeb3c57d5339b1e9fd66951dcbb60970e108
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721580"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>原始&#39;檔控制外掛程式 API 版本1.3 中的新功能
原始檔控制外掛程式 API 版本1.3 引進了下列新功能，以提供更多的先進控制。

## <a name="changes"></a>變更
 以下是原始檔控制外掛程式 API 1.3 版的新功能：

|功能|總覽|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|允許報告其他功能位|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|允許檢查版本控制資料庫中具有較新版本的檔案，而不是本機磁片上的檔案|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|允許檢查指定檔案的名稱變更狀態（重新命名、新增和刪除）|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|允許檢查版本控制資料庫中的目錄和檔案|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|從版本控制資料庫將指定的檔案清單加入至目前的專案|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|執行指定檔案的無訊息「取得」（未顯示使用者介面）|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|允許存取使用者特有的選項|

## <a name="see-also"></a>請參閱
- [使用者入門](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [原始檔控制外掛程式 API 版本 1.2 的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)