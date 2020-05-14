---
title: 從 .proj 與 .sln 檔案中移除原始碼管理資訊
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba3085a7806bfb0556613d1fca1b94953dcdb0b2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705594"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>從 .Proj 和 .Sln 檔案移除原始檔控制資訊
在原始程式碼管理外掛程式 API 的第 1.2 版中,SCC 資訊儲存在 MSSCCPRJ 中。SCC 檔。 MSSCCPRJ 的優勢。SCC 檔是 SCC 資訊不受原始程式碼控制,就像在 .proj 和 .sln 檔案中一樣。

## <a name="version-12-changes"></a>版本 1.2 變更
 在基於原始碼管理外掛程式 API 版本 1.1 的源碼管理外掛程式中,有關原始程式碼管理的資訊儲存在專案 (.proj) 和解決方案 (.sln) 檔案中。 原始程式碼管理資訊的資料庫位置由 AuxPath 指定,資料庫中的特定位置由 ProjName 指定。 此行為可能會導致分支、分叉或複製操作後出現問題,因為 ProjName 通常在任何這些操作後無效。

 在原始程式碼管理外掛程式 API 版本 1.1 中,IDE 使用 _SAK 檔來檢測外掛程式是否支援 MSSCCPRJ。存儲原始程式碼管理資訊的 SCC 方法。 原始程式碼管理外掛程式 API 版本 1.2 提供了檢測 MSSCCPRJ 支援的新功能。不使用_SAK檔的 SCC 檔。 有關詳細資訊,請參閱消除[_SAK 檔](../../extensibility/internals/elimination-of-tilde-sak-files.md)。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 1.2 版的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
