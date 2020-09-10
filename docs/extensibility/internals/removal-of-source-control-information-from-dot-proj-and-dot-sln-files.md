---
title: 從 proj 和 .sln 檔案移除原始檔控制資訊
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
ms.openlocfilehash: 54b403d105b1c2b3a3113885189868e8bae4efcc
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743055"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>從 proj 和 .sln 檔案移除原始檔控制資訊

在原始檔控制外掛程式 API 的1.2 版中，SCC 資訊儲存在 MSSCCPRJ.SCC 中。SCC 檔。 MSSCCPRJ.SCC 的優點。SCC 檔是 SCC 資訊不是原始檔控制的資訊，就像是在 proj 和 .sln 檔案中一樣。

## <a name="version-12-changes"></a>版本1.2 變更

 在以原始檔控制外掛程式 API 1.1 版為基礎的原始檔控制外掛程式中，原始檔控制的相關資訊會儲存在專案中 ( 專案) 和方案 ( .sln) 檔。 原始檔控制資訊的資料庫位置是由 AuxPath 所指定，而且資料庫內的特定位置是由 ProjName 所指定。 這種行為可能會在分支、分叉或複製作業之後造成問題，因為在這些作業中的任何一項作業之後，ProjName 通常會無效。

 在原始檔控制外掛程式 API 版本1.1 中，IDE 使用 ~ SAK 檔案來偵測外掛程式是否支援 MSSCCPRJ.SCC。儲存原始檔控制資訊的 SCC 方法。 原始檔控制外掛程式 API 版本1.2 提供偵測 MSSCCPRJ.SCC 支援的新功能。不使用 ~ SAK 檔案的 SCC 檔。 如需詳細資訊，請參閱 [~ SAK 檔案的排除](../../extensibility/internals/elimination-of-tilde-sak-files.md)。

## <a name="see-also"></a>另請參閱

- [原始檔控制外掛程式 API 1.2 版的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
