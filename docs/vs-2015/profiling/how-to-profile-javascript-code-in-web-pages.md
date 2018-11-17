---
title: 如何：分析網頁中的 JavaScript 程式碼 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
ms.assetid: 37d02aad-ca4d-4eb0-bf66-ca3ecef31fbe
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f9def923e0cc012a37c02d24b67e807668ae976
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792108"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>如何：分析網頁中的 JavaScript 程式碼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]程式碼剖析工具可以使用檢測程式碼剖析方法，針對 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web 應用程式、任意網頁或 JavaScript 應用程式中執行的 JavaScript 程式碼來收集效能資料。  
  
 **需求**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
-   Internet Explorer 8 (含) 以後版本。  
  
> [!WARNING]
>  若要對 Windows 市集應用程式中的 JavaScript 進行程式碼剖析，請參閱下列其中一個主題：  
> 
> - [JavaScript 函式計時](http://msdn.microsoft.com/library/b2bf49fc-aea7-4d9c-8fcf-cff8b8dd0c03)[遠端裝置上的 JavaScript 函式計時](http://msdn.microsoft.com/library/d78812b6-a97e-46dc-8d99-e724d1d725d8)  
>   -   [分析 JavaScript 函式計時資料](http://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b)  
>   -  
  
 您可以使用 [程式碼剖析精靈] 建立效能工作階段。 指定檢測方法，然後在效能工作階段的 [屬性] 對話方塊中，於 [檢測] 頁面上指定 JavaScript 程式碼剖析選項。  
  
 當您指定 JavaScript 程式碼剖析時，會同時對瀏覽器中執行的 JavaScript 程式碼與伺服器上執行的 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 程式碼進行程式碼剖析。  
  
-   如果是指定 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web 應用程式，會同時對瀏覽器中執行的 JavaScript 程式碼與伺服器上執行的 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 程式碼進行程式碼剖析。  
  
-   若是任意網頁，則會對瀏覽器中執行的 JavaScript 程式碼進行程式碼剖析。  
  
### <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>對 ASP.NET Web 應用程式專案中的 JavaScript 進行程式碼剖析  
  
1.  在 [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] 中，開啟 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web 專案。  
  
2.  按一下 [分析]  功能表上的 [啟動效能精靈] 。  
  
3.  在 [效能精靈] 的第一個頁面上，指定 [檢測]  程式碼剖析方法，然後按一下 [下一步] 。  
  
4.  在精靈的第二個頁面上，確定已在目標清單中選取目前專案，然後按一下 [下一步]   
  
5.  在精靈的第三個頁面上，選取 [分析 JavaScript]  核取方塊，然後按一下 [下一步] 。  
  
6.  在精靈的第四個頁面上，按一下 [完成]  ，在瀏覽器中啟動 Web 應用程式。  
  
7.  執行您要進行程式碼剖析的功能。  
  
8.  若要結束程式碼剖析工作階段，請關閉瀏覽器。  
  
### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>對個別網頁或 JavaScript 應用程式中的 JavaScript 進行程式碼剖析  
  
1.  開啟 [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)]。  
  
2.  按一下 [分析]  功能表上的 [啟動效能精靈] 。  
  
3.  在 [效能精靈] 的第一個頁面上，指定 [檢測]  程式碼剖析方法，然後按一下 [下一步] 。  
  
4.  在精靈的第二個頁面上，按一下 ASP.NET 或 JavaScript 應用程式，然後按一下 [下一步]   
  
5.  在精靈的第三個頁面上：  
  
    1.  在 [您要使用哪個 URL 或路徑執行應用程式?]  方塊中輸入網頁的 URL。  
  
    2.  選取 [分析 JavaScript]  核取方塊，然後按一下 [下一步] 。  
  
6.  在精靈的第四個頁面上，按一下 [完成]  ，在瀏覽器中啟動網頁。  
  
7.  執行您要進行程式碼剖析的功能。  
  
8.  若要結束程式碼剖析工作階段，請關閉瀏覽器。



