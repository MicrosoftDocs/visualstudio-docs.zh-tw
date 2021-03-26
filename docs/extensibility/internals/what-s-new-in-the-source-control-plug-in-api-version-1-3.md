---
title: '&apos;原始檔控制外掛程式 API 1.3 中的新功能'
description: 深入瞭解原始檔控制外掛程式 API 版本1.3 的新功能，其中引進了新的功能，可提供更多的 advanced 控制項。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7ab9079248931758efbcfcd792ce3c79ccffb270
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074258"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>原始檔控制外掛程式 API 版本1.3 的新功能&#39;
原始檔控制外掛程式 API 版本1.3 引進了下列新功能，以提供更多的 advanced 控制項。

## <a name="changes"></a>變更
 以下是原始檔控制外掛程式 API 版本1.3 的新功能：

|函式|概觀|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|允許報告其他功能位|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|允許檢查版本控制資料庫中有較新版本的檔案，而不是本機磁片上的檔案|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|允許檢查名稱變更狀態， (指定檔案的重新命名、新增和刪除) |
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|允許檢查版本控制資料庫中的目錄和檔案|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|將指定的檔案清單從版本控制資料庫新增至目前的專案|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|執行指定檔案的無訊息 "Get" (不會顯示任何使用者介面) |
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|允許存取使用者特定的選項|

## <a name="see-also"></a>另請參閱
- [快速入門](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [原始檔控制外掛程式 API 1.2 版的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
