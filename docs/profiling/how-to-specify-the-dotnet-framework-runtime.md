---
title: 指定 .NET Framework 執行階段 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 27846b448f7e0667004bd25d24bd447fe43f8e51
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851121"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>如何：指定 .NET Framework 執行階段

透過使用 .NET Framework 4 版本，應用程式可以由使用不同版本的 .NET Framework 執行階段所建置的模組組成。 根據預設，Visual Studio 分析工具預設會對應用程式所載入的第一個執行階段進行分析。 當您以程式碼剖析工具啟動應用程式時，以及當您將程式碼剖析工具附加至已在執行的應用程式時，都可以指定要進行程式碼剖析的執行階段。

## <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>在使用程式碼剖析工具來啟動應用程式時，指定要進行程式碼剖析的 .NET Framework 執行階段

1. 在 [效能總管]**** 中，以滑鼠右鍵按一下效能工作階段，按一下 [屬性]****，然後按一下 [進階]****。

     [目標 CLR 版本]**** 清單方塊會顯示 [自動]****，以及電腦上安裝的 .NET Framework 執行階段的版本。

2. 請執行下列其中一個步驟：

    - 按一下您要進行程式碼剖析的 CLR 版本。

    - 按一下 [自動]****，對應用程式所載入的第一個執行階段進行程式碼剖析。

## <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>在將程式碼剖析工具附加至應用程式時，指定要進行程式碼剖析的 .NET Framework 執行階段

1. 在 [分析]**** 功能表上，指向 [分析工具]****，然後按一下 [附加/中斷連結]****。

2. 在 [將分析工具附加至處理序]**** 對話方塊中，按一下您要進行分析的處理序。

     [目標 CLR 版本]**** 清單方塊會顯示 [自動]****，以及電腦上安裝的 .NET Framework 執行階段的版本。

3. 請執行下列其中一個步驟：

    - 按一下您要進行程式碼剖析的 CLR 版本。

    - 按一下 [自動]****，對程式碼剖析工具附加至應用程式時所載入的版本進行程式碼剖析。
