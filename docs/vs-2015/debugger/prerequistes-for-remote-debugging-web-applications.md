---
title: 遠端偵錯 Web 應用程式的必要條件 |Microsoft Docs
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
- debugging ASP.NET Web applications, remote servers
- remote debugging, prerequisites
- remote servers, debugging Web applications
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1eda777fa335cc844eedc13f350aa44319f587fd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940825"
---
# <a name="prerequistes-for-remote-debugging-web-applications"></a>Web 應用程式遠端偵錯的必要條件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 偵錯工具，您就可以在本機電腦或遠端伺服器上無障礙地對 Web 應用程式進行偵錯。 這表示，偵錯工具的運作方式相同，並可讓您在任一部電腦上使用相同的功能。 不過，為了要讓遠端偵錯正確進行，有一些先決條件必須遵守。  
  
-   [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 遠端偵錯元件必須安裝在您要偵錯的伺服器上。 如需詳細資訊，請參閱 <<c0> [ 設定遠端偵錯](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)。  
  
-   根據預設，[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 背景工作處理序會以 ASPNET 使用者處理序的方式執行。 因此，您必須在執行 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 的電腦上具有系統管理員權限，才能進行偵錯。 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 背景工作處理序的名稱會隨著偵錯情節和 IIS 的版本而有所不同。 如需詳細資訊，請參閱[如何：尋找 ASP.NET 處理序的名稱](../debugger/how-to-find-the-name-of-the-aspnet-process.md)。  
  
## <a name="see-also"></a>另請參閱  
 [對 ASP.NET 和 AJAX 應用程式進行偵錯](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [系統需求](../debugger/aspnet-debugging-system-requirements.md)
