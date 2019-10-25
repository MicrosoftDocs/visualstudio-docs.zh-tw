---
title: 從 proj 和 .sln 檔案移除原始檔控制資訊
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 68e50932a83e3db6d405119d3721d021144cbaeb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724282"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>從 .Proj 和 .Sln 檔案移除原始檔控制資訊
在原始檔控制外掛程式 API 的版本1.2 中，SCC 資訊儲存在 MSSCCPRJ.SCC 中。SCC 檔案。 MSSCCPRJ.SCC 的優點。SCC 檔案是 SCC 資訊並不受原始檔控制，像是在 proj 和 .sln 檔案中。

## <a name="version-12-changes"></a>版本1.2 變更
 在以原始檔控制外掛程式 API 版本1.1 為基礎的原始檔控制外掛程式中，原始檔控制的相關資訊會儲存在專案檔（proj）和方案（.sln）檔案中。 原始檔控制資訊的資料庫位置是由 AuxPath 所指定，而資料庫內的特定位置則是由 ProjName 指定。 這種行為可能會在分支、分叉或複製作業之後造成問題，因為在這些作業中，ProjName 通常會無效。

 在原始檔控制外掛程式 API 版本1.1 中，IDE 使用 ~ SAK files 來偵測外掛程式是否支援 MSSCCPRJ.SCC。SCC 儲存原始檔控制資訊的方法。 原始檔控制外掛程式 API 1.2 版提供新的功能，可用來偵測 MSSCCPRJ.SCC 的支援。SCC 檔案，而不使用 ~ SAK 檔案。 如需詳細資訊，請參閱[去除 ~ SAK Files](../../extensibility/internals/elimination-of-tilde-sak-files.md)。

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式 API 版本 1.2 的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)