---
title: 如何： 啟用 ASP.NET 應用程式的偵錯 |Microsoft Docs
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
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
caps.latest.revision: 40
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9f96a53a6ccdd505735a09d3e9c39acaa3517c2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47500021"
---
# <a name="how-to-enable-debugging-for-aspnet-applications"></a>如何：啟用 ASP.NET 應用程式的偵錯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 啟用 ASP.NET 應用程式的偵錯](https://docs.microsoft.com/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications)。  
  
若要啟用偵錯，您必須先在 **專案屬性** 頁面以及應用程式的 web.config 檔案中啟用它。  
  
> [!NOTE]  
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-enable-aspnet-debugging-in-the-project-properties-visual-basicc"></a>在專案屬性中啟用 ASP.NET 偵錯 (Visual Basic/C#)  
  
1.  在 **方案總管**中，以滑鼠右鍵按一下 Web 專案的名稱，並選取 [屬性] 。  
  
2.  在 [專案屬性] 頁面中，按一下 [Web]  索引標籤。  
  
3.  在 [偵錯工具] 下，選取 [ASP.NET]  核取方塊。  
  
### <a name="to-enable-debugging-in-the-webconfig-file"></a>在 web.config 檔案中啟用偵錯  
  
1.  使用任何標準文字編輯器或 XML 剖析器，以開啟 web.config 檔案。  
  
    > [!NOTE]  
    > 不過，您無法使用網頁瀏覽器從遠端存取檔案。 基於安全性原因，[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 會設定 Microsoft IIS，以協助防止瀏覽器直接存取 Web.config 檔案。 如果您嘗試使用瀏覽器來存取組態檔，則會收到 HTTP 存取錯誤 403 (禁止)。  
  
2.  Web.config 是一個 XML 檔案，因此會包含透過標記所標記的巢狀區段。 找到 `configuration/system.web/compilation` 項目。 如果 compilation 項目不存在，請建立它。  
  
3.  如果 `compilation` 項目未包含 `debug` 屬性，請將屬性加入項目中。  
  
4.  請確定`debug`屬性值設為`true`。  
  
web.config 檔案應該如下列範例所示。 請注意，configuration 與 system.web 項目之間可能會有一些區段  
  
-   configuration 與 system.web 項目之間的項目區段  
  
-   system.web 與 compilation 項目之間的項目區段  
  
-   compilation 項目可以包含其他屬性或項目  
  
## <a name="example"></a>範例  
  
```  
<configuration>  
    ...  
    <system.web>  
        <compilation  
            debug="true"  
            ...  
        >  
        ...  
        </compilation>  
    </system.web>  
</configuration>  
```  
  
## <a name="robust-programming"></a>穩固程式設計  
[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 會自動偵測任何 Web.config 檔案變更，並套用新的組態設定。 您不需要重新啟動電腦或重新啟動 IIS 伺服器，變更就會生效。  
  
網站可以包含多個虛擬目錄和子目錄，而 Web.config 檔案可能存在於每一個目錄和子目錄中。 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 應用程式會繼承 URL 路徑中較高層級之 Web.config 檔案中的設定。 階層式組態檔可讓您同時變更數個 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 應用程式的設定 (例如，針對階層中其下的所有應用程式)。 不過，如果在階層中較低的檔案中設定 `debug` ，則會覆寫較高的值。  
  
例如，您可以在 www.microsoft.com/aaa/Web.config 中指定 `debug="true"` ，而且 aaa 資料夾或 aaa 之任何子資料夾中的任何應用程式都會繼承該設定。 因此，如果您[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]應用程式在 www.microsoft.com/aaa/bbb 時，它會繼承該設定，而任何[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]www.microsoft.com/aaa/ccc、 www.microsoft.com/aaa/ddd，等等中的應用程式。 唯一的例外是其中一個應用程式透過自己的較低 Web.config 檔案來覆寫設定時。  
  
啟用偵錯模式會大幅影響 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 應用程式的效能。 請務必先停用偵錯模式，再部署發行應用程式或進行效能度量。  
  
## <a name="see-also"></a>另請參閱  
[偵錯 ASP.NET 和 AJAX 應用程式](../debugger/debugging-aspnet-and-ajax-applications.md)  
  




