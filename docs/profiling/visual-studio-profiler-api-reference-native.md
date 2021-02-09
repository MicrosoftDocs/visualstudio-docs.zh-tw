---
title: Visual Studio 分析工具 API 參考 (原生)
description: 瞭解 Visual Studio profiler Api 如何讓您以程式設計方式控制收集的資料量，並在分析期間插入時間戳記和設定檔標記。
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, API
- Profiler, API
ms.assetid: a0c3be92-c263-4678-9fb9-bafead3bd5f5
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 9d8fe6f4f1f38277a8cf317fa55fbc883b85394a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890535"
---
# <a name="visual-studio-profiler-api-reference-native"></a>Visual Studio 分析工具 API 參考 (原生)
Visual Studio 分析工具 API 可讓您以程式設計方式控制收集的資料量，並在分析期間插入時間戳記和設定檔標記。 若要使用原生 API，您可以在您的專案中包含 *VSPerf.h* 標頭檔，並新增 *VSPerf.lib*。

> [!NOTE]
> 若要取得分析工具的路徑，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。

## <a name="in-this-section"></a>本節內容
[CommentMarkAtProfile](../profiling/commentmarkatprofile.md)

[CommentMarkProfile](../profiling/commentmarkprofile.md)

[MarkProfile](../profiling/markprofile.md)

[NameProfile](../profiling/nameprofile.md)

[ResumeProfile](../profiling/resumeprofile.md)

[StartProfile](../profiling/startprofile.md)

[StopProfile](../profiling/stopprofile.md)

[SuspendProfile](../profiling/suspendprofile.md)

[PROFILE_CURRENTID](../profiling/profile-currentid.md)

## <a name="see-also"></a>另請參閱

- [程式碼剖析工具 Api](../profiling/profiling-tools-apis.md)
- [逐步解說：使用分析工具 API](../profiling/walkthrough-using-profiler-apis.md)
