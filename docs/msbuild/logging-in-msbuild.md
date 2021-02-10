---
title: MSBuild 中的記錄 | Microsoft Docs
description: 瞭解 MSBuild 記錄如何藉由在記錄檔中捕捉組建事件、訊息、警告和錯誤，來監視組建進度。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, logging
ms.assetid: 9aea2e76-8f60-4234-913d-598e7bbad808
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: afbb79e2ce8ebdccc68def6ca4c42fde85c11bf0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966249"
---
# <a name="logging-in-msbuild"></a>MSBuild 中的記錄

記錄功能提供一種方式讓您能夠監視組建的進度。 記錄功能會擷取記錄檔中建置事件、訊息、警告和錯誤。

## <a name="in-this-section"></a>本節內容

- [取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)

 描述 MSBuild 中記錄的各個層面。

- [組建記錄器](../msbuild/build-loggers.md)

 概述建立單一處理器的記錄器時所需的步驟。

- [在多處理器環境中記錄](../msbuild/logging-in-a-multi-processor-environment.md)

 說明記錄功能在多處理器環境中的運作方式，以及兩個多處理器記錄模型。

- [撰寫能夠辨識多處理器的記錄器](../msbuild/writing-multi-processor-aware-loggers.md)

 概述如何建立能夠辨識多處理器的記錄器以及如何使用 ConfigurableForwardingLogger。

- [建立轉送記錄器](../msbuild/creating-forwarding-loggers.md)

 概述如何建立自訂的轉送記錄器。

## <a name="see-also"></a>另請參閱

- [平行建置多個專案](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md) 描述如何透過讓專案平行執行的方式，加快建置多個專案的速度。
