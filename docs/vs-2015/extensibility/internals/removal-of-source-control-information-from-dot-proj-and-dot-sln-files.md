---
title: 從原始檔控制資訊移除。Proj 和。Sln 檔案 |Microsoft Docs
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199381"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>從 .Proj 和 .Sln 檔案移除原始檔控制資訊
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

原始檔控制外掛程式 API SCC 1.2 版中的資訊會儲存在 MSSCCPRJ。SCC 檔案。 MSSCCPRJ 的優點。SCC 檔案是，SCC 資訊是不在來源-控制，例如它位於.proj 和.sln 檔案。  
  
## <a name="version-12-changes"></a>1\.2 版的變更  
 在原始檔控制外掛程式原始檔控制外掛程式 API 1.1 版為基礎，原始檔控制的相關資訊儲存在專案 (.proj) 和方案 (.sln) 檔案。 AuxPath，指定資料庫位置的原始檔控制資訊，並在資料庫內的特定位置由專案名稱。 此行為會造成問題，分支、 分支或複製作業之後，因為專案名稱通常是不正確之後任何一項作業。  
  
 在 原始檔控制外掛程式 API 版本 1.1，IDE 使用 ~ SAK 檔案，以偵測如果外掛程式支援 MSSCCPRJ。SCC 儲存原始檔控制資訊的方法。 原始檔控制外掛程式 API 1.2 版提供一項新功能來偵測 MSSCCPRJ 的支援。SCC 檔案，而不使用 ~ SAK 檔案。 如需詳細資訊，請參閱 <<c0> [ 消除 ~ SAK 檔案](../../extensibility/internals/elimination-of-tilde-sak-files.md)。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 版本 1.2 的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
