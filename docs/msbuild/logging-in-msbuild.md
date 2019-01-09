---
title: MSBuild 中的記錄 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, logging
ms.assetid: 9aea2e76-8f60-4234-913d-598e7bbad808
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 259fbda65a745c265315f347e5a04a1cff39ad1c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53842457"
---
# <a name="logging-in-msbuild"></a>MSBuild 中的記錄
記錄功能提供一種方式讓您能夠監視組建的進度。 記錄功能會擷取記錄檔中建置事件、訊息、警告和錯誤。  
  
## <a name="in-this-section"></a>本節內容  
 [取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)  
 說明 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 中各個層面的記錄。  
  
 [組建記錄器](../msbuild/build-loggers.md)  
 概述建立單一處理器的記錄器時所需的步驟。  
  
 [在多處理器環境中記錄](../msbuild/logging-in-a-multi-processor-environment.md)  
 說明記錄功能在多處理器環境中的運作方式，以及兩個多處理器記錄模型。  
  
 [撰寫能夠辨識多處理器的記錄器](../msbuild/writing-multi-processor-aware-loggers.md)  
 概述如何建立能夠辨識多處理器的記錄器以及如何使用 ConfigurableForwardingLogger。  
  
 [建立轉送記錄器](../msbuild/creating-forwarding-loggers.md)  
 概述如何建立自訂的轉送記錄器。  
  
## <a name="see-also"></a>另請參閱  
 [平行建置多個專案](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)  
 說明如何透過讓專案平行執行的方式，加快建置多個專案的速度。