---
title: 裝載處理序 (vshost.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- vshost.exe
- hosting process
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f11bed43a9595a3ce0034555f05a18f7a9dfa7d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="hosting-process-vshostexe"></a>裝載處理序 (vshost.exe)
Visual Studio 的裝載處理序功能可改善偵錯效能、啟用部分信任偵錯及設計階段運算式評估。 裝載處理序檔案的檔名中包含 *vshost*，並放在您專案的輸出資料夾中。 如需詳細資訊，請參閱[偵錯和裝載處理序](../debugger/debugging-and-the-hosting-process.md)。  
  
> [!NOTE]
>  裝載處理序檔案 (*.vshost.exe*) 是供 Visual Studio 使用，因此不應該直接執行或與應用程式一起部署。  
  
## <a name="improved-debugging-performance"></a>改進偵錯效能  
 裝載處理序會建立應用程式定義域，並將偵錯工具與應用程式建立關聯。 執行上述工作會導致偵錯開始的時間與應用程式執行的時間出現明顯延遲。 裝載處理序可藉由建立應用程式定義域、將其與背景的偵錯工具產生關聯，並在應用程式執行之間儲存應用程式定義域與偵錯工具的狀態，以協助提升效能。 如需應用程式定義域的詳細資訊，請參閱[應用程式定義域](/dotnet/framework/app-domains/application-domains)。  
  
## <a name="partial-trust-debugging"></a>部分信任偵錯  
 您可在 [專案設計工具] 的[安全性頁面](../ide/reference/security-page-project-designer.md)中，將應用程式指定為部分信任的應用程式。 在偵錯部分信任的應用程式時，需要進行應用程式定義域的特殊初始設定。 這項初始化設定會由裝載處理序進行處理。  
  
## <a name="design-time-expression-evaluation"></a>設計階段運算式評估  
 設計階段運算式評估可讓您透過 [即時運算] 視窗來測試程式碼，而不需執行應用程式。 在設計階段運算式評估期間，裝載處理序會執行這個程式碼。 如需詳細資訊，請參閱[即時運算視窗](../ide/reference/immediate-window.md)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯和主機處理序](../debugger/debugging-and-the-hosting-process.md)   
 [如何：停用裝載處理序](../ide/how-to-disable-the-hosting-process.md)   
 [即時運算視窗](../ide/reference/immediate-window.md)   
 [應用程式定義域](/dotnet/framework/app-domains/application-domains)