---
title: "如何： 使用 ClickOnce 部署可以在多個版本的.NET Framework 執行的應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, multiple .NET Framework versions
- ClickOnce deployment, multiple .NET Framework versions
- deploying applications [ClickOnce], multiple .NET Framework versions
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
caps.latest.revision: "17"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: d634d320df50dafc203ea1b1b4c8366ae3e24a41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>如何：使用 ClickOnce 來部署可在多個 .NET Framework 版本上執行的應用程式
您可以部署應用程式的使用 clickonce 部署為目標的.NET framework 的多個版本。 這需要您產生和更新的應用程式和部署資訊清單。  
  
> [!NOTE]
>  變更要以多個版本的.NET framework 為目標的應用程式之前，您應該確定您的應用程式，會以多個版本的.NET Framework 執行。 版本的 common language runtime 是不同之間[!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]與.NET Framework 2.0、.NET Framework 3.0，以及.NET Framework 3.5。  
  
 此程序需要下列步驟：  
  
1.  產生應用程式和部署資訊清單。  
  
2.  變更部署資訊清單，列出多個.NET Framework 版本。  
  
3.  變更要列出相容的.NET Framework 執行階段版本的 app.config 檔案。  
  
4.  變更應用程式資訊清單，以做為.NET Framework 組件的相依組件標記。  
  
5.  登入應用程式資訊清單。  
  
6.  更新，並簽署部署資訊清單。  
  
### <a name="to-generate-the-application-and-deployment-manifests"></a>若要產生應用程式和部署資訊清單  
  
-   使用 發行精靈 或 發行 頁面的 專案設計工具來發行應用程式和產生的應用程式和部署資訊清單檔案。 如需詳細資訊，請參閱[如何： 發行 ClickOnce 應用程式使用發行精靈](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)或[專案設計工具、 發行頁](../ide/reference/publish-page-project-designer.md)。  
  
### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>若要變更部署資訊清單，列出多個.NET Framework 版本  
  
1.  在發行目錄中，使用 Visual Studio 中的 XML 編輯器開啟部署資訊清單。 部署資訊清單有.application 的副檔名。  
  
2.  之間的 XML 程式碼取代`<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">`和`</compatibleFrameworks>`xml 程式碼，列出您的應用程式支援的.NET Framework 版本的項目。  
  
     下表顯示一些可用的.NET Framework 版本和您可以將它加入至部署資訊清單的對應 XML。  
  
    |.NET Framework 版本|XML|  
    |----------------------------|---------|  
    |4 用戶端|\<framework targetVersion ="4.0"設定檔 = 「 用戶端 」 supportedRuntime ="4.0.30319"/ >|  
    |4 全文|\<framework targetVersion ="4.0"設定檔 「 完整 」 supportedRuntime 的 = ="4.0.30319"/ >|  
    |3.5 用戶端|\<framework targetVersion ="3.5"設定檔 = 「 用戶端 」 supportedRuntime ="2.0.50727"/ >|  
    |3.5 完整|\<framework targetVersion ="3.5"設定檔 = 「 完整 」 supportedRuntime ="2.0.50727"/ >|  
    |3.0|\<framework targetVersion ="3.0"supportedRuntime ="2.0.50727"/ >|  
  
### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>若要變更要列出相容的.NET Framework 執行階段版本的 app.config 檔案  
  
1.  在 [方案總管] 中，開啟 Visual Studio 中使用 XML 編輯器的 App.config 檔案。  
  
2.  取代 （或加入） 之間的 XML 程式碼`<startup>`和`</startup>`xml 程式碼，列出您的應用程式支援的.NET Framework 執行階段的項目。  
  
     下表顯示一些可用的.NET Framework 版本和您可以將它加入至部署資訊清單的對應 XML。  
  
    |.NET framework 執行階段版本|XML|  
    |------------------------------------|---------|  
    |4 用戶端|\<supportedRuntime 版本 ="v4.0.30319"sku ="。NETFramework，Version = v4.0，Profile = Client"/ >|  
    |4 全文|\<supportedRuntime 版本 ="v4.0.30319"sku ="。NETFramework，Version = v4.0"/ >|  
    |3.5 完整|\<supportedRuntime version="v2.0.50727"/ >|  
    |3.5 用戶端|\<supportedRuntime 版本 ="v2.0.50727"sku = 「 用戶端 」 / >|  
  
### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>若要變更應用程式資訊清單，以做為.NET Framework 組件的相依組件標記  
  
1.  在發行目錄中，開啟 Visual Studio 中使用 XML 編輯器的應用程式資訊清單。 部署資訊清單有.manifest 的副檔名。  
  
2.  新增`group="framework"`給 sentinel 組件相依性的 XML (`System.Core`， `WindowsBase`， `Sentinel.v3.5Client`，和`System.Data.Entity`)。 例如，XML 看起來應該如下所示：  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3.  更新的版本號碼`<assemblyIdentity>`Microsoft.Windows.CommonLanguageRuntime 項目是最低公分母的.NET framework 的版本號碼。 例如，如果應用程式的目標.NET Framework 3.5 和[!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]，使用 [2.0.50727.0] 版本號碼和 XML 應該如下所示：  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>若要更新並重新簽署應用程式和部署資訊清單  
  
-   更新並重新簽署應用程式和部署資訊清單。 如需詳細資訊，請參閱[如何： 重新簽署應用程式和部署資訊清單](../deployment/how-to-re-sign-application-and-deployment-manifests.md)。  
  
## <a name="see-also"></a>另請參閱  
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [\<w > 項目](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [\<相依性 > 項目](../deployment/dependency-element-clickonce-application.md)   
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)   
 [組態檔結構描述](/dotnet/framework/configure-apps/file-schema/index)