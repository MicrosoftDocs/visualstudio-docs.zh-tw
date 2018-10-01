---
title: 遠端偵錯 Web 應用程式的必要條件 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 197a6e9b433173f1de13e3506db79e7edf53bade
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489933"
---
# <a name="prerequistes-for-remote-debugging-web-applications"></a>Web 應用程式遠端偵錯的必要條件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[遠端偵錯 Web 應用程式的必要條件](https://docs.microsoft.com/visualstudio/debugger/prerequistes-for-remote-debugging-web-applications)。  
  
使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 偵錯工具，您就可以在本機電腦或遠端伺服器上無障礙地對 Web 應用程式進行偵錯。 這表示，偵錯工具的運作方式相同，並可讓您在任一部電腦上使用相同的功能。 不過，為了要讓遠端偵錯正確進行，有一些先決條件必須遵守。  
  
-   [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 遠端偵錯元件必須安裝在您要偵錯的伺服器上。 如需詳細資訊，請參閱 <<c0> [ 設定遠端偵錯](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)。  
  
-   根據預設，[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 背景工作處理序會以 ASPNET 使用者處理序的方式執行。 因此，您必須在執行 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 的電腦上具有系統管理員權限，才能進行偵錯。 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 背景工作處理序的名稱會隨著偵錯情節和 IIS 的版本而有所不同。 如需詳細資訊，請參閱 [How to: Find the Name of the ASP.NET Process](../debugger/how-to-find-the-name-of-the-aspnet-process.md)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 ASP.NET 和 AJAX 應用程式](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [系統需求](../debugger/aspnet-debugging-system-requirements.md)



