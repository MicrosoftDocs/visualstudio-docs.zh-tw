---
title: Visual Studio 生命週期原則例外狀況 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
ms.assetid: c238489d-6181-42c6-aa60-f75d0889dc68
caps.latest.revision: 3
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: cc3a18fe1ce76b6214766ba45fc5441e80c56cef
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918481"
---
# <a name="visual-studio-lifecycle-policy-exceptions"></a>Visual Studio 週期原則例外
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 包含一組編譯器、語言、執行階段、環境和其他資源，可針對許多 Microsoft 平台進行開發。 為了方便我們的 Visual Studio 客戶，Visual Studio 可能會安裝特定 Microsoft SDK，以及針對和支援這些 Microsoft 平台的其他 Microsoft 元件。 這些元件可能依其本身的條款及原則進行授權及支援。  
  
## <a name="external-components-that-follow-a-lifecycle-policy-other-than-the-visual-studio-policy"></a>遵循非 Visual Studio 原則之週期原則的外部元件  
 下表列出可能隨附於 Visual Studio (視 Visual Studio 軟體的特定版本而定)，並有各自的支援原則和時間範圍的 Microsoft 平台元件。  
  
|產品系列|EXTERNAL NAME|  
|--------------------|-------------------|  
|[.NET 3.5](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=net%20framework%203.5&Filter=FilterNO)|.NET 3.5 SDK<br /><br /> Windows Identity Foundation|  
|[.NET 4.5](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=net%20framework%204.5&Filter=FilterNO)|.NET 4.5 SDK|  
|[.NET 4.5.1](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=.NET%20Framework%204.5.1&Filter=FilterNO)|.NET 4.5.1 MT 套件 (傳統)<br /><br /> .NET 4.5.1 多目標套件 (市集)<br /><br /> .NET 4.5.1 OOB MSU<br /><br /> .NET 4.5.1 可轉散發套件<br /><br /> .NET 4.5.1 可轉散發套件語言套件<br /><br /> .NET 4.5.1 SDK|  
|[ASP.NET Web 堆疊](https://support.microsoft.com/kb/2902020)|ASP.NET MVC 4<br /><br /> ASP.NET MVC 5<br /><br /> ASP.NET Web 應用程式開發介面<br /><br /> ASP.NET Web API 2<br /><br /> ASP.NET Web Pages 2<br /><br /> ASP.NET Web Pages 3|  
|[Entity Framework 6](https://support.microsoft.com/kb/2902020)|Entity Framework 6|  
|[Exchange 2013](https://support.microsoft.com/kb/2902020)|Exchange Web 服務|  
|[Microsoft OWIN](https://support.microsoft.com/kb/2902020)|Microsoft OWIN|  
|[Microsoft Web Developer Tools 2013](https://support.microsoft.com/kb/2902020)|Microsoft Web Developer Tools 2013|  
|這些元件的更新是透過 NuGet 散發，而且不遵循標準的 Microsoft 週期原則。  請參閱 [http://docs.nuget.org/](/nuget/) 以取得詳細資訊。|適用於 Microsoft .NET Framework 4.5 的 JSON Web Token Handler<br /><br /> NuGet 2.7<br /><br /> SignalR<br /><br /> Web Optimization Framework<br /><br /> WebGrease|  
|[ODataLib](https://support.microsoft.com/kb/2902020)|ODataLib|  
|[Office 2013](https://support.microsoft.com/lifecycle/search/?p1=16674)|Open XML SDK|  
|[線上服務原則](https://support.microsoft.com/hub/4095338/microsoft-lifecycle-policy)|Microsoft Ads SDK|  
|[SharePoint 2013](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=sharepoint%20server%202013&Filter=FilterNO)|SharePoint 用戶端元件<br /><br /> SharePoint Foundation 2013<br /><br /> Windows Identity Foundation 擴充功能|  
|[Silverlight 5](https://support.microsoft.com/lifecycle/search/?p1=16278)<br /><br /> <br />> 另請參閱：[http://support.microsoft.com/gp/lifean45](https://support.microsoft.com/gp/lifean45)|Silverlight 5 執行階段<br /><br /> Silverlight 5 SDK|  
|[SQL Server 2008 R2](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202008%20R2&Filter=FilterNO)|SQL 系統 CLR 類型 (SQL Server 2008 R2)|  
|[SQL Server 2012](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202012&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> SQL 命令列公用程式<br /><br /> SQL 語言服務 - IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Native Client (Sqlncli)<br /><br /> SQL Server Express 2012 SP1<br /><br /> SQL 系統 CLR 類型 (SQL Server 2012)<br /><br /> SQLDOM|  
|[SQL Server 2014](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202014&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> SQL 命令列公用程式<br /><br /> SQL 語言服務 - IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Native Client (Sqlncli)<br /><br /> SQL Server Express 2014<br /><br /> SQL 系統 CLR 類型 (SQL Server 2014)<br /><br /> SQLDOM|  
|[SQL Server Compact Edition 4.0](https://support.microsoft.com/lifecycle/search/?p1=16106)|SQL Server Compact Edition 4.0|  
|[WCF RIA Services v1.0 SP2](https://support.microsoft.com/kb/2902020)|WCF RIA Services v1.0 SP2|  
|[Windows Server 2008](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=Windows%20Server%202008&Filter=FilterNO)|適用於 Windows Server 2008 的 Windows Web 服務 (WWS)|  
|[Windows 7](https://support.microsoft.com/lifecycle/search/?c2=14019)|Windows 7 SDK|  
|[Windows 8](https://support.microsoft.com/lifecycle/search/?c2=16796)|Windows 8 SDK|  
|[Windows 8.1](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=windows%208.1&Filter=FilterNO)|Windows 8.1 SDK<br /><br /> 適用於 JavaScript 的 Windows Library (WinJS)|  
|[Microsoft Azure](https://support.microsoft.com/help/18486/lifecycle-faq-azure)<br /><br /> <br />> 另請參閱：[線上生命週期原則](https://support.microsoft.com/hub/4095338/microsoft-lifecycle-policy)|Microsoft Azure 行動服務 SDK<br /><br /> Microsoft Azure 行動服務工具|
