---
title: 偵錯和裝載處理序 |Microsoft Docs
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
ms.openlocfilehash: 109bd4ee3c54e8d468714c2a955e349ec76db2fe
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54952089"
---
# <a name="debugging-and-the-hosting-process"></a>偵錯和裝載處理序
Visual Studio 裝載處理序改進偵錯工具的效能並且啟用新的偵錯工具功能，例如部分信任偵錯和設計階段運算式評估。 如果需要的話可以停用裝載處理序。 下列章節描述使用或不使用裝載處理序進行偵錯之間的一些差異。

> [!NOTE]
> 在 Visual Studio 2017 中，不再需要使用裝載處理序進行偵錯的選項，並已移除。 如需詳細資訊，請參閱[偵錯。Visual Studio 2017 目標是您最喜愛的作業加快](https://vslive.com/Blogs/News-and-Tips/2017/02/Debugging-Visual-Studio-2017-aims-to-speed-up-your-least-favorite-job.aspx)。

## <a name="partial-trust-debugging-and-click-once-security"></a>部分信任偵錯和 Click-Once 安全性
 部分信任偵錯需要裝載處理序。 如果您停用裝載處理序，即使在 [專案屬性]  的 [安全性] 頁面上啟用部分信任安全性，部分信任偵錯也無法運作。 如需詳細資訊，請參閱[＜How to：針對部分信任的應用程式進行偵錯](/visualstudio/debugger/debugger-security)。

## <a name="design-time-expression-evaluation"></a>設計階段運算式評估
 設計階段運算式一定會使用裝載處理序。 在 [專案屬性]  中停用裝載處理序會停用類別庫專案的設計階段運算式評估， 但不會停用其他專案類型的設計階段運算式評估， 而是 Visual Studio 會啟動實際可執行檔，並且在不使用裝載處理序的情況下針對設計階段評估使用可執行檔。 這項差異會產生不同的結果。

## <a name="appdomaincurrentdomainfriendlyname-differences"></a>AppDomain.CurrentDomain.FriendlyName 差異
 `AppDomain.CurrentDomain.FriendlyName` 會根據是否啟用裝載處理序傳回不同的結果。 如果在啟用裝載處理序的情況下呼叫 `AppDomain.CurrentDomain.FriendlyName` ，它會傳回 *app_name*`.vhost.exe`。 如果在停用裝載處理序的情況下呼叫，它會傳回 *app_name*`.exe`。

## <a name="assemblygetcallingassemblyfullname-differences"></a>Assembly.GetCallingAssembly().FullName 差異
 `Assembly.GetCallingAssembly().FullName` 會根據是否啟用裝載處理序傳回不同的結果。 如果在啟用裝載處理序的情況下呼叫 `Assembly.GetCallingAssembly().FullName` ，它會傳回 `mscorlib`。 如果在停用裝載處理序的情況下呼叫 `Assembly.GetCallingAssembly().FullName` ，其會傳回應用程式名稱。

## <a name="see-also"></a>另請參閱

- [如何：針對部分信任的應用程式進行偵錯](/visualstudio/debugger/debugger-security)