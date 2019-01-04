---
title: 開始使用原始檔控制外掛程式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 829bf676a407fd166eda252cb4e6e2fbdb93fa41
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854499"
---
# <a name="get-started-with-source-control-plug-ins"></a>開始使用原始檔控制外掛程式
若要建立原始檔控制外掛程式，您必須建立可實作定義在原始檔控制外掛程式 API 中，該函式的 DLL，然後註冊 DLL[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]以使其可供使用原始程式碼版本控制中。  
  
 原始檔控制外掛程式 API （版本 1.1、 1.2 和 1.3） 的三個版本可供原始檔控制外掛程式。原始檔控制外掛程式 API，請參閱為 1.3 版。 它被設計為與原始檔控制外掛程式完全相容支援 1.1 和 1.2 版。 [的新功能 原始檔控制外掛程式 API 版本 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)章節將詳細說明支援的原始檔控制外掛程式 API 版本中的新功能。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：安裝原始檔控制外掛程式](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 描述如何進行原始檔控制 DLL 插入所需的登錄項目。  
  
 [什麼是原始檔控制外掛程式 API 版本 1.3 的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 提供對原始檔控制外掛程式 API 版本 1.3 所做的變更的簡短概觀。  
  
 [原始檔控制外掛程式 API 版本 1.2 中最新消息](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 提供對原始檔控制外掛程式 API，在 1.2 版所做的變更的簡短概觀。  
  
## <a name="related-sections"></a>相關章節  
 [原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)  
 提供原始檔控制外掛程式 API 中的所有項目的完整清單。  
  
 [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 定義原始檔控制外掛程式 SDK，並說明內含的資源。