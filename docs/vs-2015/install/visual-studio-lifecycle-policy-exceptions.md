---
title: Visual Studio 週期原則例外 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c238489d-6181-42c6-aa60-f75d0889dc68
caps.latest.revision: 3
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: c7c60747429bd702cdcea5f19891829411cd4a9c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772621"
---
# <a name="visual-studio-lifecycle-policy-exceptions"></a>Visual Studio 週期原則例外
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 包含一組編譯器、語言、執行階段、環境和其他資源，可針對許多 Microsoft 平台進行開發。 為了方便我們的 Visual Studio 客戶，Visual Studio 可能會安裝特定 Microsoft SDK，以及針對和支援這些 Microsoft 平台的其他 Microsoft 元件。 這些元件可能依其本身的條款及原則進行授權及支援。  
  
## <a name="external-components-that-follow-a-lifecycle-policy-other-than-the-visual-studio-policy"></a>遵循非 Visual Studio 原則之週期原則的外部元件  
 下表列出可能隨附於 Visual Studio (視 Visual Studio 軟體的特定版本而定)，並有各自的支援原則和時間範圍的 Microsoft 平台元件。  
  
|產品系列|外部名稱|  
|--------------------|-------------------|  
|[.NET 3.5](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=net%20framework%203.5&Filter=FilterNO)|.NET 3.5 SDK<br /><br /> Windows Identity Foundation|  
|[.NET 4.5](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=net%20framework%204.5&Filter=FilterNO)|.NET 4.5 SDK|  
|[.NET 4.5.1](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=.NET%20Framework%204.5.1&Filter=FilterNO)|.NET 4.5.1 MT 套件 (傳統)<br /><br /> .NET 4.5.1 多目標套件 (市集)<br /><br /> .NET 4.5.1 OOB MSU<br /><br /> .NET 4.5.1 可轉散發套件<br /><br /> .NET 4.5.1 可轉散發套件語言套件<br /><br /> .NET 4.5.1 SDK|  
|[ASP.NET Web 堆疊](http://go.microsoft.com/fwlink/?LinkId=328918)|ASP.NET MVC 4<br /><br /> ASP.NET MVC 5<br /><br /> ASP.NET Web API<br /><br /> ASP.NET Web API 2<br /><br /> ASP.NET Web Pages 2<br /><br /> ASP.NET Web Pages 3|  
|[Entity Framework 6](http://go.microsoft.com/fwlink/?LinkId=328950)|Entity Framework 6|  
|[Exchange 2013](http://go.microsoft.com/fwlink/?LinkId=328950)|Exchange Web 服務|  
|[Microsoft OWIN](http://go.microsoft.com/fwlink/?LinkId=328951)|Microsoft OWIN|  
|[Microsoft Web Developer Tools 2013](http://go.microsoft.com/fwlink/?LinkId=328952)|Microsoft Web Developer Tools 2013|  
|這些元件的更新是透過 NuGet 散發，而且不遵循標準的 Microsoft 週期原則。  請參閱 [http://docs.nuget.org/](http://docs.nuget.org/) 以取得詳細資訊。|適用於 Microsoft .NET Framework 4.5 的 JSON Web Token Handler<br /><br /> NuGet 2.7<br /><br /> SignalR<br /><br /> Web Optimization Framework<br /><br /> WebGrease|  
|[ODataLib](http://go.microsoft.com/fwlink/?LinkId=328954)|ODataLib|  
|[Office 2013](http://support.microsoft.com/lifecycle/?p1=16674)|Open XML SDK|  
|[線上服務原則](http://support.microsoft.com/gp/OSSLpolicy)|Microsoft Ads SDK|  
|[SharePoint 2013](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=sharepoint%20server%202013&Filter=FilterNO)|SharePoint 用戶端元件<br /><br /> SharePoint Foundation 2013<br /><br /> Windows Identity Foundation 擴充功能|  
|[Silverlight 5](http://support.microsoft.com/lifecycle/?p1=16278)<br /><br /> <br />> 請參閱： [http://support.microsoft.com/gp/lifean45](http://support.microsoft.com/gp/lifean45)|Silverlight 5 執行階段<br /><br /> Silverlight 5 SDK|  
|[SQL Server 2008 R2](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=SQL%20Server%202008%20R2&Filter=FilterNO)|SQL 系統 CLR 類型 (SQL Server 2008 R2)|  
|[SQL Server 2012](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=SQL%20Server%202012&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> SQL 命令列公用程式<br /><br /> SQL 語言服務 - IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Native Client (Sqlncli)<br /><br /> SQL Server Express 2012 SP1<br /><br /> SQL 系統 CLR 類型 (SQL Server 2012)<br /><br /> SQLDOM|  
|[SQL Server 2014](https://support.microsoft.com/en-us/lifecycle/search?sort=PN&alpha=SQL%20Server%202014&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> SQL 命令列公用程式<br /><br /> SQL 語言服務 - IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Native Client (Sqlncli)<br /><br /> SQL Server Express 2014<br /><br /> SQL 系統 CLR 類型 (SQL Server 2014)<br /><br /> SQLDOM|  
|[SQL Server Compact Edition 4.0](http://support.microsoft.com/lifecycle/?p1=16106)|SQL Server Compact Edition 4.0|  
|[WCF RIA 服務 v1.0 SP2](http://go.microsoft.com/fwlink/?LinkId=328955)|WCF RIA Services v1.0 SP2|  
|[Windows Server 2008](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=Windows%20Server%202008&Filter=FilterNO)|適用於 Windows Server 2008 的 Windows Web 服務 (WWS)|  
|[Windows 7](http://support.microsoft.com/lifecycle/?c2=14019)|Windows 7 SDK|  
|[Windows 8](http://support.microsoft.com/lifecycle/?c2=16796)|Windows 8 SDK|  
|[Windows 8.1](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=windows%208.1&Filter=FilterNO)|Windows 8.1 SDK<br /><br /> 適用於 JavaScript 的 Windows Library (WinJS)|  
|[Microsoft Azure](http://support.microsoft.com/gp/azure-cloud-lifecycle-faq)<br /><br /> <br />> 請參閱：[線上週期原則](http://support.microsoft.com/gp/OSSLpolicy)|Microsoft Azure 行動服務 SDK<br /><br /> Microsoft Azure 行動服務工具|