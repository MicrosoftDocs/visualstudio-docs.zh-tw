---
title: 分析網頁中的 JavaScript 程式碼 | Microsoft Docs
description: 瞭解 Visual Studio 分析工具如何使用檢測程式碼剖析方法來收集 JavaScript 程式碼的效能資料。
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 64f0f61cc6afbce2542ac0b3e251764646ab1d97
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98723331"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>如何：分析網頁中的 JavaScript 程式碼

Visual Studio 分析工具可以使用檢測分析方法，針對 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式、任意網頁或 JavaScript 應用程式中執行的 JavaScript 程式碼來收集效能資料。 需要 Internet Explorer 8 或更新版本。

> [!WARNING]
> 若要對 UWP 應用程式中的 JavaScript 進行程式碼剖析，請參閱 [JavaScript 記憶體](../profiling/javascript-memory.md)

您可以使用 [程式碼剖析精靈] 建立效能工作階段。 指定檢測方法，然後在效能工作階段的 [屬性] 對話方塊中，於 [檢測] 頁面上指定 JavaScript 程式碼剖析選項。

當您指定 JavaScript 程式碼剖析時，會同時對瀏覽器中執行的 JavaScript 程式碼與伺服器上執行的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 程式碼進行程式碼剖析。

- 如果是指定 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式，會同時對瀏覽器中執行的 JavaScript 程式碼與伺服器上執行的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 程式碼進行分析。

- 若是任意網頁，則會對瀏覽器中執行的 JavaScript 程式碼進行分析。

## <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>對 ASP.NET Web 應用程式專案中的 JavaScript 進行分析

1. 在 Visual Studio 中開啟 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 專案。

2. 按一下 [分析]  功能表上的 [啟動效能精靈] 。

3. 在 [效能精靈] 的第一個頁面上，指定 [檢測]  程式碼剖析方法，然後按一下 [下一步] 。

4. 在精靈的第二個頁面上，確定已在目標清單中選取目前專案，然後按一下 [下一步] 

5. 在精靈的第三個頁面上，選取 [分析 JavaScript]  核取方塊，然後按一下 [下一步] 。

6. 在精靈的第四個頁面上，按一下 [完成]，以在瀏覽器中啟動 Web 應用程式。

7. 執行您要進行程式碼剖析的功能。

8. 若要結束程式碼剖析工作階段，請關閉瀏覽器。

### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>對個別網頁或 JavaScript 應用程式中的 JavaScript 進行分析

1. 開啟 Visual Studio。

2. 按一下 [分析]  功能表上的 [啟動效能精靈] 。

3. 在 [效能精靈] 的第一個頁面上，指定 [檢測]  程式碼剖析方法，然後按一下 [下一步] 。

4. 在精靈的第二個頁面上，按一下 ASP.NET 或 JavaScript 應用程式，然後按一下 [下一步] 

5. 在精靈的第三個頁面上：

    1. 在 [您要使用哪個 URL 或路徑執行應用程式?]  方塊中輸入網頁的 URL。

    2. 選取 [分析 JavaScript]  核取方塊，然後按一下 [下一步] 。

6. 在精靈的第四個頁面上，按一下 [完成]，以在瀏覽器中啟動網頁。

7. 執行您要進行程式碼剖析的功能。

8. 若要結束程式碼剖析工作階段，請關閉瀏覽器。
