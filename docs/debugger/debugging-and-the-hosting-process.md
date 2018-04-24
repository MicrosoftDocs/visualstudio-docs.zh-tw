---
title: 偵錯和裝載處理序 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04d6500ba45b10a4cc6a309e7f60872febc19736
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="debugging-and-the-hosting-process"></a>偵錯和裝載處理序
Visual Studio 裝載處理序改進偵錯工具的效能並且啟用新的偵錯工具功能，例如部分信任偵錯和設計階段運算式評估。 如果需要的話可以停用裝載處理序。 如需詳細資訊，請參閱 [How to: Disable the Hosting Process](../ide/how-to-disable-the-hosting-process.md)。 下列章節描述使用或不使用裝載處理序進行偵錯之間的一些差異。  
  
## <a name="partial-trust-debugging-and-click-once-security"></a>部分信任偵錯和 Click-Once 安全性  
 部分信任偵錯需要裝載處理序。 如果您停用裝載處理序，即使在 [專案屬性]  的 [安全性] 頁面上啟用部分信任安全性，部分信任偵錯也無法運作。 如需詳細資訊，請參閱 [How to: Disable the Hosting Process](../ide/how-to-disable-the-hosting-process.md) 與 [How to: Debug a Partial Trust Application](../debugger/how-to-debug-a-partial-trust-application.md)。  
  
## <a name="design-time-expression-evaluation"></a>設計階段運算式評估  
 設計階段運算式一定會使用裝載處理序。 在 [專案屬性]  中停用裝載處理序會停用類別庫專案的設計階段運算式評估， 但不會停用其他專案類型的設計階段運算式評估， 而是 Visual Studio 會啟動實際可執行檔，並且在不使用裝載處理序的情況下針對設計階段評估使用可執行檔。 這項差異會產生不同的結果。  
  
## <a name="appdomaincurrentdomainfriendlyname-differences"></a>AppDomain.CurrentDomain.FriendlyName 差異  
 `AppDomain.CurrentDomain.FriendlyName` 會根據是否啟用裝載處理序傳回不同的結果。 如果在啟用裝載處理序的情況下呼叫 `AppDomain.CurrentDomain.FriendlyName` ，它會傳回 *app_name*`.vhost.exe`。 如果在停用裝載處理序的情況下呼叫，它會傳回 *app_name*`.exe`。  
  
## <a name="assemblygetcallingassemblyfullname-differences"></a>Assembly.GetCallingAssembly().FullName 差異  
 `Assembly.GetCallingAssembly().FullName` 會根據是否啟用裝載處理序傳回不同的結果。 如果在啟用裝載處理序的情況下呼叫 `Assembly.GetCallingAssembly().FullName` ，它會傳回 `mscorlib`。 如果在停用裝載處理序的情況下呼叫 `Assembly.GetCallingAssembly().FullName` ，其會傳回應用程式名稱。  
  
## <a name="see-also"></a>另請參閱  
 [裝載處理序 (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [如何： 偵錯部分信任應用程式](../debugger/how-to-debug-a-partial-trust-application.md)   
 [如何：停用裝載處理序](../ide/how-to-disable-the-hosting-process.md)