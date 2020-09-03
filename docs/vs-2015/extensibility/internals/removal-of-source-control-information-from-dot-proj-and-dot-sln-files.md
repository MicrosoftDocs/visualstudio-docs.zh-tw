---
title: 從移除原始檔控制資訊。Proj 和。.Sln 檔案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b7cdaeb02f77d3775096f840a513f68e531b1299
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199381"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>從 .Proj 和 .Sln 檔案移除原始檔控制資訊
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

在原始檔控制外掛程式 API 的1.2 版中，SCC 資訊儲存在 MSSCCPRJ.SCC 中。SCC 檔。 MSSCCPRJ.SCC 的優點。SCC 檔是 SCC 資訊不是原始檔控制的資訊，就像是在 proj 和 .sln 檔案中一樣。  
  
## <a name="version-12-changes"></a>版本1.2 變更  
 在以原始檔控制外掛程式 API 1.1 版為基礎的原始檔控制外掛程式中，原始檔控制的相關資訊會儲存在專案中 ( 專案) 和方案 ( .sln) 檔。 原始檔控制資訊的資料庫位置是由 AuxPath 所指定，而且資料庫內的特定位置是由 ProjName 所指定。 這種行為可能會在分支、分叉或複製作業之後造成問題，因為在這些作業中的任何一項作業之後，ProjName 通常會無效。  
  
 在原始檔控制外掛程式 API 版本1.1 中，IDE 使用 ~ SAK 檔案來偵測外掛程式是否支援 MSSCCPRJ.SCC。儲存原始檔控制資訊的 SCC 方法。 原始檔控制外掛程式 API 版本1.2 提供偵測 MSSCCPRJ.SCC 支援的新功能。不使用 ~ SAK 檔案的 SCC 檔。 如需詳細資訊，請參閱 [~ SAK 檔案的排除](../../extensibility/internals/elimination-of-tilde-sak-files.md)。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 1.2 版的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
