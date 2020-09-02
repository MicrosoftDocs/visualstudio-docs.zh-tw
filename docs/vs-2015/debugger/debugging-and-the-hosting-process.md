---
title: 偵錯工具和裝載進程 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], hosting process
- hosting process
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 10f3968367b188203671fa6bfff48bc482efe4f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157889"
---
# <a name="debugging-and-the-hosting-process"></a>偵錯和裝載處理序
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 裝載處理序改進偵錯工具的效能並且啟用新的偵錯工具功能，例如部分信任偵錯和設計階段運算式評估。 如果需要的話可以停用裝載處理序。 如需詳細資訊，請參閱 [How to: Disable the Hosting Process](../ide/how-to-disable-the-hosting-process.md)。 下列章節描述使用或不使用裝載處理序進行偵錯之間的一些差異。  
  
## <a name="partial-trust-debugging-and-click-once-security"></a>部分信任偵錯和 Click-Once 安全性  
 部分信任偵錯需要裝載處理序。 如果您停用裝載處理序，即使在 [專案屬性] **** 的 [安全性] **** 頁面上啟用部分信任安全性，部分信任偵錯也無法運作。 如需詳細資訊，請參閱 [How to: Disable the Hosting Process](../ide/how-to-disable-the-hosting-process.md) 與 [How to: Debug a Partial Trust Application](../debugger/how-to-debug-a-partial-trust-application.md)。  
  
## <a name="design-time-expression-evaluation"></a>設計階段運算式評估  
 設計階段運算式一定會使用裝載處理序。 在 [專案屬性] **** 中停用裝載處理序會停用類別庫專案的設計階段運算式評估， 但不會停用其他專案類型的設計階段運算式評估， 而是 Visual Studio 會啟動實際可執行檔，並且在不使用裝載處理序的情況下針對設計階段評估使用可執行檔。 這項差異會產生不同的結果。  
  
## <a name="appdomaincurrentdomainfriendlyname-differences"></a>AppDomain.CurrentDomain.FriendlyName 差異  
 `AppDomain.CurrentDomain.FriendlyName` 會根據是否啟用裝載處理序傳回不同的結果。 如果您在 `AppDomain.CurrentDomain.FriendlyName` 啟用裝載進程的情況下呼叫，它會傳回*app_name* `.vhost.exe` 。 如果您呼叫它，裝載進程會停用，它會傳回*app_name* `.exe` 。  
  
## <a name="assemblygetcallingassemblyfullname-differences"></a>Assembly.GetCallingAssembly().FullName 差異  
 `Assembly.GetCallingAssembly().FullName` 會根據是否啟用裝載處理序傳回不同的結果。 如果在啟用裝載處理序的情況下呼叫 `Assembly.GetCallingAssembly().FullName` ，它會傳回 `mscorlib`。 如果在停用裝載處理序的情況下呼叫 `Assembly.GetCallingAssembly().FullName` ，其會傳回應用程式名稱。  
  
## <a name="see-also"></a>另請參閱  
 [裝載進程 ( # A0) ](../ide/hosting-process-vshost-exe.md)   
 [如何：對部分信任應用程式進行偵錯工具](../debugger/how-to-debug-a-partial-trust-application.md)   
 [如何：停用裝載進程](../ide/how-to-disable-the-hosting-process.md)
