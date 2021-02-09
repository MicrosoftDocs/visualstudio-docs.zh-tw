---
title: 收集網站的效能資料 |微軟
description: 瞭解如何使用 Performance Wizard 收集 ASP.NET web 應用程式的效能資料。 應用程式會在您的本機電腦上執行，而且可以在 Visual Studio 中開啟。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vsperf.url.url
- vsperf.chooseurl
- vs.performance.wizard.asppage
- vsperf.url.ok
- vsperf.url.cancel
helpviewer_keywords:
- Profiling Tools,profiling ASP.NET
- web sites, performance profiling
- ASP.NET, performance profilng
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a8e42522967b39c381e834ea93ccb1965aeb97fe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886219"
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>如何：收集網站的效能資料

您可以使用 [效能精靈] 收集 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式的效能資料。 您可以對 Visual Studio 中開啟的 Web 應用程式進行分析，也可以對位於本機電腦上但未在 Visual Studio IDE 中開啟的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 網站進行分析。

> [!NOTE]
> [效能精靈]  可讓您將階層互動 (TIP) 資料及/或 JScript 效能資料新增至收集的程式碼剖析資料。 TIP 選項會從伺服器端處理序收集資料。 JScript 程式碼剖析會從本機或遠端網站上執行的指令碼收集資料。 在大部分情況下，您應該只選擇其中一個選項。

 依據系統管理員提供的使用者存取權限設定，個別使用者不一定具有安全性權限可以在裝載 ASP.NET 處理序的電腦上建立分析工具工作階段。 下列範例説明各使用者之間可能存在的差異：

- 當系統管理員將驅動程式和服務設定為啟動時，某些使用者可能會存取進階的分析功能。

- 網域使用者可能僅會存取範例分析。

- 某些使用者可能會拒絕其他所有使用者存取分析功能。

  如需詳細資訊，請參閱[分析和 Windows Vista 安全性](../profiling/profiling-and-windows-vista-security.md)，以及 [VSPerfCmd](../profiling/vsperfcmd.md) 中的 ADMIN 選項。

## <a name="to-profile-a-web-site-project"></a>對網站專案進行分析

1. 在 Visual Studio 中開啟 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 專案。

2. 在 [分析] 功能表上，選取 [效能分析工具]，再選取 [效能總管]，然後選取 [啟動]。

3. 在精靈的第一個頁面上，選取程式碼剖析方法，然後按一下 [下一步] 。 如需分析方法的詳細資訊，請參閱[了解效能收集方法](../profiling/understanding-performance-collection-methods.md)。 請注意，並行視覺化檢視程式碼剖析方法不適用於 Web 應用程式。

4. 在 [您要以哪一個應用程式作為分析的目標?]  下拉式清單中，確認已選取目前的專案，然後按一下 [下一步] 。

5. 在精靈的第三個頁面上，您可以選擇是否要新增階層互動分析 (TIP) 資料及/或網頁中執行之 JavaScript 的資料。

    - 若要收集階層互動，請選取 [啟用階層互動分析]  核取方塊。

    - 若要從網頁中執行的 JavaScript 收集資料，請選取 [ **分析 javascript** ] 核取方塊。

6. 按一下 [下一步] 。

7. 在精靈的第四個頁面上，按一下 [完成] 。

8. 隨即為 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式建立效能工作階段，並在瀏覽器中啟動網站。 執行您要進行程式碼剖析的功能，然後關閉瀏覽器。

     分析工具隨即產生資料檔案，並在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 主視窗中顯示資料的 [摘要] 檢視。

## <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>對網站進行分析，但不在 Visual Studio 中開啟專案

1. 開啟 Visual Studio。

2. 在 [分析] 功能表上，選取 [效能分析工具]，再選取 [效能總管]，然後選取 [啟動]。

3. 在精靈的第一個頁面上，選取程式碼剖析方法，然後按一下 [下一步] 。 如需詳細資訊，請參閱[了解效能收集方法](../profiling/understanding-performance-collection-methods.md)。

4. 在精靈的第二個頁面上，選取 [為 ASP.NET 或 JavaScript 應用程式進行程式碼剖析]  選項，然後按一下 [下一步] 。

5. 在精靈第三個頁面的 [您要使用哪個 URL 或路徑執行 Web 應用程式]  方塊中，輸入應用程式首頁的 URL，然後按一下 [下一步] 。

   - 針對 (IIS) 基礎網站的伺服器，請輸入如下的 URL： **<`http://localhost/MySite/default.aspx`>** 。 這會對本機電腦上位於 MySite 之應用程式根目錄的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式進行程式碼剖析，然後 Internet Explorer 會啟動該網站的 default.aspx 頁面以開始工作階段。

   - 針對檔案架構的網站，請輸入如檔案///**c:\WebSites\MySite\default.aspx** 之類的路徑。 這會對位於 c:\webSites\MySite 的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式進行分析，然後 Internet Explorer 會啟動 `http://localhost:nnnn/MySite/default.aspx` 頁面以開始工作階段。

   - 針對您想要收集 JavaScript 資料的外部網站，請鍵入如 `http://www.contoso.com` 之類的 URL。

     如需詳細資訊，請檢視 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 目標二進位檔的屬性頁。

6. 在精靈的第三個頁面上，您可以選擇是否要新增階層互動分析 (TIP) 資料及/或網頁中執行之 JavaScript 的資料。

    - 若要收集階層互動，請選取 [啟用階層互動分析]  核取方塊。

    - 若要從網頁中執行的 JavaScript 收集資料，請選取 [分析 JavaScript] 核取方塊。

7. 按一下 [下一步] 。

8. 在精靈的第四個頁面上，按一下 [完成] 。

9. 隨即為 ASP.NET 應用程式建立效能工作階段，並在瀏覽器中啟動網站。 執行您要進行程式碼剖析的功能，然後關閉瀏覽器。

     分析工具隨即產生資料檔案，並在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 主視窗中顯示資料的 [摘要] 檢視。

## <a name="see-also"></a>另請參閱

[概覽](../profiling/overviews-performance-tools.md) 
[設定效能會話](../profiling/configuring-performance-sessions.md) 
[瞭解檢測資料值](../profiling/understanding-instrumentation-data-values.md) 
[瞭解取樣資料值](../profiling/understanding-sampling-data-values.md)
