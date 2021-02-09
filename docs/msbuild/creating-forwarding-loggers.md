---
title: 建立轉送記錄器 | Microsoft Docs
description: 藉由讓您在建立專案時選擇要監視的事件，以建立 MSBuild 轉送記錄器來改善記錄效率。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, forwarding loggers
- MSBuild, logging
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0ffe175d9ea73640cae1197fe91656d3565525f6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901361"
---
# <a name="create-forwarding-loggers"></a>建立轉送記錄器

轉送記錄器可讓您選擇在多處理器系統上建置專案時想要監視的事件，以提高記錄的效率。 啟用轉送記錄器時，您可以防止不必要的事件塞滿中央記錄器，而導致建置時間變慢、記錄空間暴增等問題。

 若要建立轉送記錄器，您可以實作 <xref:Microsoft.Build.Framework.IForwardingLogger> 介面，然後以手動方式實作它的方法，或使用 <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> 類別和其預先設定的方法。 對大部分的應用程式來說，採用後者就足夠了。

## <a name="register-events-and-respond-to-them"></a>註冊與回應事件

 轉送記錄器會收集由次要建置引擎所報告的建置事件相關資訊；次要建置引擎是在多處理器系統上建置期間，由主要建置程序建立的背景工作處理序。 接著，轉送記錄器會根據您所提供的指示，選取要轉送給中央記錄器的事件。

 您必須註冊轉送記錄器，才能處理想要監視的事件。 若要註冊事件，記錄器必須覆寫 <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> 方法。 這個方法現在包含一個 `nodecount` 選擇性參數，您可用來設定系統處理器的數量。 預設值為 1。

 您可以監視的事件範例為 <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>、<xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> 和 <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>。

 在多處理器環境中，可能不會按順序接收事件訊息。 因此，您必須使用轉送記錄器中的事件處理常式來評估事件，並為它編寫程式以決定哪些事件要傳遞到重新導向程式，並轉送給中央記錄器。 若要完成此動作，您可以使用每個訊息附加的 <xref:Microsoft.Build.Framework.BuildEventContext> 類別，以協助識別您想要轉送的事件，然後將事件的名稱傳遞給 <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> 類別 (或它的子類別)。 當您使用這個方法時，不需要任何其他特定編碼即可轉送事件。

## <a name="specify-a-forwarding-logger"></a>指定轉送記錄器

 當轉送記錄器已編譯成元件之後，您必須告知 MSBuild 在組建期間使用它。 若要這樣做，請使用 `-FileLogger` 、 `-FileLoggerParameters` 和 `-DistributedFileLogger` 參數搭配 *MSBuild.exe*。 此 `-FileLogger` 參數會告知 *MSBuild.exe* 是否已直接附加記錄器。 `-DistributedFileLogger` 參數表示每個節點都有一個記錄檔。 若要設定轉送記錄器的參數，請使用 `-FileLoggerParameters` 參數。 如需這些參數和其他 *MSBuild.exe* 參數的詳細資訊，請參閱 [命令列參考](../msbuild/msbuild-command-line-reference.md)。

## <a name="multi-processor-aware-loggers"></a>能夠辨識多處理器的記錄器

 當您在多處理器系統建置專案時，來自每個處理器的建置訊息不會自動按一致順序交錯排列。 因此，您必須使用附加至每個訊息的 <xref:Microsoft.Build.Framework.BuildEventContext> 類別，以建立訊息群組優先順序。 如需多處理器建立的詳細資訊，請參閱 [在多處理器環境中記錄](../msbuild/logging-in-a-multi-processor-environment.md)。

## <a name="see-also"></a>另請參閱

- [取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)
- [組建記錄器](../msbuild/build-loggers.md)
- [在多處理器環境中記錄](../msbuild/logging-in-a-multi-processor-environment.md)