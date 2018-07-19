---
title: 如何： 使用 ClickOnce 部署可在多個.NET Framework 版本執行的應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, multiple .NET Framework versions
- ClickOnce deployment, multiple .NET Framework versions
- deploying applications [ClickOnce], multiple .NET Framework versions
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: eb4d8696755a70005923833625c72a95e5f1e80a
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079946"
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>如何： 使用 ClickOnce 來部署可在多個.NET framework 版本執行的應用程式
您可以部署目標使用 ClickOnce 部署技術的多個版本的.NET framework 的應用程式。 這需要您產生，並更新應用程式和部署資訊清單。  
  
> [!NOTE]
>  變更多個版本的.NET framework 為目標的應用程式之前，您應該確定您的應用程式執行與多個.NET Framework 版本。 版本的 common language runtime 是不同[!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]與.NET Framework 2.0、.NET Framework 3.0，以及.NET Framework 3.5。  
  
 此程序需要下列步驟：  
  
1.  產生應用程式和部署資訊清單。  
  
2.  變更部署資訊清單，若要列出多個.NET Framework 版本。  
  
3.  變更*app.config*列出相容的.NET Framework 執行階段版本的檔案。  
  
4.  變更應用程式資訊清單，以做為.NET Framework 組件的相依組件標記。  
  
5.  登入應用程式資訊清單。  
  
6.  更新，並簽署部署資訊清單。  
  
### <a name="to-generate-the-application-and-deployment-manifests"></a>若要產生應用程式和部署資訊清單  
  
-   使用 發行精靈 或 發行 頁面的 專案設計工具來發佈應用程式，並產生應用程式和部署資訊清單檔案。 如需詳細資訊，請參閱 <<c0> [ 如何： 發行 ClickOnce 應用程式使用發行精靈](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)或是[專案設計工具、 發行頁](../ide/reference/publish-page-project-designer.md)。  
  
### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>若要變更部署資訊清單，若要列出多個.NET Framework 版本  
  
1.  在發行目錄中，請在 Visual Studio 中使用 XML 編輯器開啟部署資訊清單。 部署資訊清單有 *.application*副檔名。  
  
2.  將 XML 程式碼之間`<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">`和`</compatibleFrameworks>`列出支援的.NET Framework 版本，您的應用程式的 XML 項目。  
  
     下表顯示一些可用的.NET Framework 版本和對應的 XML，您可以將它新增至部署資訊清單。  
  
    |.NET Framework 版本|XML|  
    |----------------------------|---------|  
    |4 個用戶端|\<framework targetversion 其中一個 ="4.0"profile ="Client"Supportedruntime> ="4.0.30319"/ >|  
    |4 全文|\<framework targetversion 其中一個 ="4.0"profile = 「 完整 」 Supportedruntime> ="4.0.30319"/ >|  
    |3.5 用戶端|\<framework targetversion 其中一個 ="3.5"profile ="Client"Supportedruntime> ="2.0.50727"/ >|  
    |3.5 完整|\<framework targetversion 其中一個 ="3.5"profile = 「 完整 」 Supportedruntime> ="2.0.50727"/ >|  
    |3.0|\<framework targetversion 其中一個 ="3.0"Supportedruntime> ="2.0.50727"/ >|  
  
### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>若要變更 app.config 檔案，以列出相容的.NET Framework 執行階段版本  
  
1.  在 [方案總管] 中，開啟*app.config* Visual Studio 中使用 XML 編輯器中的檔案。  
  
2.  取代 （或加入） 之間的 XML 程式碼`<startup>`和`</startup>`列出支援的.NET Framework 執行階段中，您的應用程式的 XML 項目。  
  
     下表顯示一些可用的.NET Framework 版本和對應的 XML，您可以將它新增至部署資訊清單。  
  
    |.NET framework 執行階段版本|XML|  
    |------------------------------------|---------|  
    |4 個用戶端|\<Supportedruntime> 版本 ="v4.0.30319"sku = 」。NETFramework，版本 = v4.0，設定檔 = 用戶端 」 / >|  
    |4 全文|\<Supportedruntime> 版本 ="v4.0.30319"sku = 」。NETFramework，版本 = v4.0"/ >|  
    |3.5 完整|\<Supportedruntime> version="v2.0.50727"/ >|  
    |3.5 用戶端|\<Supportedruntime> 版本 ="v2.0.50727"sku ="Client"/ >|  
  
### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>若要變更的應用程式資訊清單，以做為.NET Framework 組件的相依組件標記  
  
1.  在發行目錄中，請在 Visual Studio 中使用 XML 編輯器開啟應用程式資訊清單。 部署資訊清單有 *.manifest*副檔名。  
  
2.  新增`group="framework"`sentinel 組件相依性的 XML (`System.Core`， `WindowsBase`， `Sentinel.v3.5Client`，和`System.Data.Entity`)。 例如，XML 看起來應該如下所示：  
  
    ```xml  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3.  更新的版本號碼`<assemblyIdentity>`Microsoft.Windows.CommonLanguageRuntime 項目是最小公分母的.NET framework 的版本號碼。 例如，如果應用程式的目標.NET Framework 3.5 和[!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]，使用 [2.0.50727.0] 版本號碼和 XML 應該看起來如下：  
  
    ```xml  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>若要更新和重新簽署應用程式和部署資訊清單  
  
-   更新並重新簽署應用程式和部署資訊清單。 如需詳細資訊，請參閱 <<c0> [ 如何： 重新簽署應用程式和部署資訊清單](../deployment/how-to-re-sign-application-and-deployment-manifests.md)。  
  
## <a name="see-also"></a>另請參閱  
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [\<compatibleFrameworks > 項目](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [\<相依性 > 項目](../deployment/dependency-element-clickonce-application.md)   
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)   
 [組態檔結構描述](/dotnet/framework/configure-apps/file-schema/index)