---
title: 開始使用原始檔控制外掛程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 3f5c88d932fd2915273c86924d2df8f1233baeed
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128908"
---
# <a name="getting-started-with-source-control-plug-ins"></a>開始使用原始檔控制外掛程式
若要建立原始檔控制外掛程式，您必須建立會實作定義在原始檔控制外掛程式 API 中，該函式的 DLL，然後註冊的 DLL[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]以使其可供使用原始程式碼版本控制中。  
  
 三個原始檔控制外掛程式 API （版本 1.1、 1.2 和 1.3） 版本可供原始檔控制外掛程式。記載的原始檔控制外掛程式 API 是 1.3 版。 它設計為與原始檔控制外掛程式完全相容支援 1.1 和 1.2 版。 [What's New in 原始檔控制外掛程式 API 版本 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)一節詳細說明在原始檔控制外掛程式 API 的最新版本中支援的新功能。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：安裝原始檔控制外掛程式](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 描述如何進行插入了原始檔控制 DLL 所需的登錄項目。  
  
 [原始檔控制外掛程式 API 版本 1.3 的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 提供對原始檔控制外掛程式 API，1.3 版中所做的變更的簡短概觀。  
  
 [原始檔控制外掛程式 API 版本 1.2 的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 提供對原始檔控制外掛程式 API，在 1.2 版中所做的變更的簡短概觀。  
  
## <a name="related-sections"></a>相關章節  
 [原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)  
 提供完整的原始檔控制外掛程式 API 中的所有項目清單。  
  
 [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 定義原始檔控制外掛程式 SDK，並描述包含的資源。