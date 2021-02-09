---
title: 偵錯工具和裝載進程 |Microsoft Docs
description: 針對2017之前的 Visual Studio 版本，請使用裝載進程來改善偵錯工具效能，以及存取某些偵錯工具功能。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 750b210ce04850e0cb6370094cdcc835f577b587
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872868"
---
# <a name="debugging-and-the-hosting-process"></a>偵錯和裝載處理序
Visual Studio 裝載處理序改進偵錯工具的效能並且啟用新的偵錯工具功能，例如部分信任偵錯和設計階段運算式評估。 如果需要的話可以停用裝載處理序。 下列章節描述使用或不使用裝載處理序進行偵錯之間的一些差異。

> [!NOTE]
> 從 Visual Studio 2017 開始，已不再需要使用裝載進程進行偵錯工具的選項，而且已經移除。 如需詳細資訊，請參閱 [偵錯工具： Visual Studio 2017 的目標是加快最愛的作業](https://vslive.com/Blogs/News-and-Tips/2017/02/Debugging-Visual-Studio-2017-aims-to-speed-up-your-least-favorite-job.aspx)。

## <a name="partial-trust-debugging-and-click-once-security"></a>部分信任偵錯和 Click-Once 安全性
 部分信任偵錯需要裝載處理序。 如果您停用裝載處理序，即使在 [專案屬性]  的 [安全性] 頁面上啟用部分信任安全性，部分信任偵錯也無法運作。 如需詳細資訊，請參閱 [如何：對部分信任應用程式進行 Debug](debugger-security.md)。

## <a name="design-time-expression-evaluation"></a>設計階段運算式評估
 設計階段運算式一定會使用裝載處理序。 在 [專案屬性]  中停用裝載處理序會停用類別庫專案的設計階段運算式評估， 但不會停用其他專案類型的設計階段運算式評估， 而是 Visual Studio 會啟動實際可執行檔，並且在不使用裝載處理序的情況下針對設計階段評估使用可執行檔。 這項差異會產生不同的結果。

## <a name="appdomaincurrentdomainfriendlyname-differences"></a>AppDomain.CurrentDomain.FriendlyName 差異
 `AppDomain.CurrentDomain.FriendlyName` 會根據是否啟用裝載處理序傳回不同的結果。 如果您在 `AppDomain.CurrentDomain.FriendlyName` 啟用裝載進程的情況下呼叫，它會傳回 *app_name* `.vhost.exe` 。 如果您呼叫它，裝載進程會停用，它會傳回 *app_name* `.exe` 。

## <a name="assemblygetcallingassemblyfullname-differences"></a>Assembly.GetCallingAssembly().FullName 差異
 `Assembly.GetCallingAssembly().FullName` 會根據是否啟用裝載處理序傳回不同的結果。 如果在啟用裝載處理序的情況下呼叫 `Assembly.GetCallingAssembly().FullName` ，它會傳回 `mscorlib`。 如果在停用裝載處理序的情況下呼叫 `Assembly.GetCallingAssembly().FullName` ，其會傳回應用程式名稱。

## <a name="see-also"></a>另請參閱

- [How to: Debug a Partial Trust Application](debugger-security.md)