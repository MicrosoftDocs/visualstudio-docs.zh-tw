---
title: 原始程式碼管理外掛程式 API 版本 1.3 中&#39;新增功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9654f1f3ae6d4a3d73ddc3afca2977a57a98297d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703367"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>來源控制外掛程式 API 版本 1.3 中&#39;新增功能
原始程式碼管理外掛程式 API 版本 1.3 引入了以下新功能,以提供更進階的控制。

## <a name="changes"></a>變更
 以下功能是原始碼管理外掛程式 API 版本 1.3 的新功能:

|函式|概觀|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|允許報告其他功能位|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|允許檢查版本控制資料庫中具有較新版本的檔案,而不是本地磁碟上的檔案|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|允許檢查指定檔案的名稱變更狀態(重新命名、新增和刪除)|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|允許檢查版本控制資料庫中的目錄與檔案|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|將指定的檔案清單從版本控制資料庫到目前項目|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|執行指定檔案的靜默取得「(不顯示使用者介面)|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|允許存取特定於使用者的選項|

## <a name="see-also"></a>另請參閱
- [快速入門](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [原始檔控制外掛程式 API 1.2 版的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
