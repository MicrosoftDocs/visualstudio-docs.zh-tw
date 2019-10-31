---
title: 偵錯工具和裝載進程 |Microsoft Docs
ms.date: 08/01/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], hosting process
- hosting process
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f77df2eae643b658e915662e0f50f6a376141d27
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188465"
---
# <a name="debugging-and-the-hosting-process"></a>偵錯和裝載處理序
Visual Studio 裝載處理序改進偵錯工具的效能並且啟用新的偵錯工具功能，例如部分信任偵錯和設計階段運算式評估。 如果需要的話可以停用裝載處理序。 下列章節描述使用或不使用裝載處理序進行偵錯之間的一些差異。

> [!NOTE]
> 從 Visual Studio 2017 開始，不再需要使用裝載進程來進行偵錯工具的選項，而且已移除。 如需詳細資訊，請參閱[偵錯工具： Visual Studio 2017 的目標，是要加速最愛](https://vslive.com/Blogs/News-and-Tips/2017/02/Debugging-Visual-Studio-2017-aims-to-speed-up-your-least-favorite-job.aspx)用的作業。

## <a name="partial-trust-debugging-and-click-once-security"></a>部分信任偵錯和 Click-Once 安全性
 部分信任偵錯需要裝載處理序。 如果您停用裝載處理序，即使在 [專案屬性] 的 [安全性]頁面上啟用部分信任安全性，部分信任偵錯也無法運作。 如需詳細資訊，請參閱[如何： Debug 部分信任應用程式](debugger-security.md)。

## <a name="design-time-expression-evaluation"></a>設計階段運算式評估
 設計階段運算式一定會使用裝載處理序。 在 [專案屬性] 中停用裝載處理序會停用類別庫專案的設計階段運算式評估， 但不會停用其他專案類型的設計階段運算式評估， 而是 Visual Studio 會啟動實際可執行檔，並且在不使用裝載處理序的情況下針對設計階段評估使用可執行檔。 這項差異會產生不同的結果。

## <a name="appdomaincurrentdomainfriendlyname-differences"></a>AppDomain.CurrentDomain.FriendlyName 差異
 `AppDomain.CurrentDomain.FriendlyName` 會根據是否啟用裝載處理序傳回不同的結果。 如果在啟用裝載處理序的情況下呼叫 `AppDomain.CurrentDomain.FriendlyName` ，它會傳回 *app_name*`.vhost.exe`。 如果在停用裝載處理序的情況下呼叫，它會傳回 *app_name*`.exe`。

## <a name="assemblygetcallingassemblyfullname-differences"></a>Assembly.GetCallingAssembly().FullName 差異
 `Assembly.GetCallingAssembly().FullName` 會根據是否啟用裝載處理序傳回不同的結果。 如果在啟用裝載處理序的情況下呼叫 `Assembly.GetCallingAssembly().FullName` ，它會傳回 `mscorlib`。 如果在停用裝載處理序的情況下呼叫 `Assembly.GetCallingAssembly().FullName` ，其會傳回應用程式名稱。

## <a name="see-also"></a>請參閱

- [如何：偵錯部分信任的應用程式](debugger-security.md)