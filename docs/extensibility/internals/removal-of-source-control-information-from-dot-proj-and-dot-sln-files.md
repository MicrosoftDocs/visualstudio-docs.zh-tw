---
title: 從原始檔控制資訊移除。Proj 和。Sln 檔案 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: 14
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4131e3d5139911c6a1bb9b44d8d8acaefa6cb632
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>從原始檔控制資訊移除。Proj 和。Sln 檔案
原始檔控制外掛程式 API SCC 1.2 版中的資訊會儲存在 MSSCCPRJ。SCC 檔案。 MSSCCPRJ 的優點。SCC 檔案是，SCC 資訊是不在來源-控制像.proj 和.sln 檔案中一樣。  
  
## <a name="version-12-changes"></a>1.2 版的變更  
 原始檔控制外掛程式原始檔控制外掛程式 API 1.1 版為基礎，在原始檔控制的相關資訊會儲存在專案 (.proj) 和方案 (.sln) 檔案。 原始檔控制資訊的資料庫位置指定 AuxPath，且資料庫內的特定位置由指定專案名稱。 這種行為可能會造成問題的分支，「 分叉 」 或複製作業之後因為 ProjName 通常會設定不正確之後任一這些作業。  
  
 在 原始檔控制外掛程式 API 版本 1.1，IDE 使用 ~ 偵測如果外掛程式支援 MSSCCPRJ SAK 檔案。儲存原始檔控制資訊的 SCC 方法。 原始檔控制外掛程式 API 1.2 版提供一項新功能來偵測 MSSCCPRJ 的支援。SCC 檔案，而不使用 ~ SAK 檔案。 如需詳細資訊，請參閱[消除 ~ SAK 檔案](../../extensibility/internals/elimination-of-tilde-sak-files.md)。  
  
## <a name="see-also"></a>請參閱  
 [原始檔控制外掛程式 API 版本 1.2 的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)