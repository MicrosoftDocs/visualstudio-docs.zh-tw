---
title: 使用 ClickOnce 部署使用多目標應用程式
description: 瞭解如何使用 ClickOnce 部署技術，部署以多個 .NET Framework 版本為目標的應用程式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: c87ed73d2c3a26ecc4522c6497ac71e33e46a6c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889118"
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>如何：使用 ClickOnce 來部署可在多個 .NET Framework 版本上執行的應用程式
您可以使用 ClickOnce 部署技術，部署以多個 .NET Framework 版本為目標的應用程式。 這需要您產生和更新應用程式和部署資訊清單。

> [!NOTE]
> 在您將應用程式變更為以 .NET Framework 的多個版本為目標之前，您應該確定您的應用程式是使用多個版本的 .NET Framework 來執行。 .NET Framework 4 和 .NET Framework 2.0、.NET Framework 3.0 和 .NET Framework 3.5 之間的 common language runtime 版本不同。

 此程式需要執行下列步驟：

1. 產生應用程式和部署資訊清單。

2. 變更部署資訊清單，以列出多個 .NET Framework 版本。

3. 變更 *app.config* 檔案，以列出相容的 .NET Framework 執行階段版本。

4. 變更應用程式資訊清單，將相依元件標示為 .NET Framework 元件。

5. 簽署應用程式資訊清單。

6. 更新和簽署部署資訊清單。

### <a name="to-generate-the-application-and-deployment-manifests"></a>產生應用程式和部署資訊清單

- 使用 [發佈嚮導] 或 [專案設計工具] 的 [發行] 頁面，即可發行應用程式，並產生應用程式和部署資訊清單檔案。 如需詳細資訊，請參閱 [如何：使用發行嚮導](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) 或 [發行頁面、專案設計](../ide/reference/publish-page-project-designer.md)工具發行 ClickOnce 應用程式。

### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>若要變更部署資訊清單以列出多個 .NET Framework 版本

1. 在 [發行] 目錄中，使用 Visual Studio 中的 XML 編輯器開啟部署資訊清單。 部署資訊清單具有 *應用程式* 副檔名。

2. 將與專案之間的 XML 程式碼取代為 `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` `</compatibleFrameworks>` 會列出應用程式支援之 .NET Framework 版本的 xml。

     下表顯示一些可用的 .NET Framework 版本，以及您可以新增至部署資訊清單的對應 XML。

    |.NET Framework 版本|XML|
    |----------------------------|---------|
    |4 Client|\<framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />|
    |4 Full|\<framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />|
    |3.5 Client|\<framework targetVersion="3.5" profile="Client" supportedRuntime="2.0.50727" />|
    |3.5 Full|\<framework targetVersion="3.5" profile="Full" supportedRuntime="2.0.50727" />|
    |3.0|\<framework targetVersion="3.0" supportedRuntime="2.0.50727" />|

### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>若要變更 app.config 檔案，以列出相容的 .NET Framework 執行階段版本

1. 在方案總管中，使用 Visual Studio 中的 XML 編輯器開啟 *app.config* 檔案。

2. 取代 (，或在和元素之間新增) 的 XML 程式碼， `<startup>` `</startup>` 其中 xml 會列出應用程式的支援 .NET Framework 執行時間。

     下表顯示一些可用的 .NET Framework 版本，以及您可以新增至部署資訊清單的對應 XML。

    |.NET Framework 執行階段版本|XML|
    |------------------------------------|---------|
    |4 Client|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0,Profile=Client" />|
    |4 Full|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0" />|
    |3.5 Full|\<supportedRuntime version="v2.0.50727"/>|
    |3.5 Client|\<supportedRuntime version="v2.0.50727" sku="Client"/>|

### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>變更應用程式資訊清單以將相依元件標示為 .NET Framework 元件

1. 在 [發行] 目錄中，使用 Visual Studio 中的 XML 編輯器開啟應用程式資訊清單。 部署資訊清單的副檔名為 *.manifest* 。

2. 將 `group="framework"` sentinel 元件的相依性 XML 加入 (`System.Core` 、 `WindowsBase` 、 `Sentinel.v3.5Client` 和 `System.Data.Entity`) 。 例如，XML 看起來應該如下所示：

   ```xml
   <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">
   ```

3. 將 CommonLanguageRuntime 專案的版本號碼更新為 `<assemblyIdentity>` 最低的一般分母 .NET Framework 的版本號碼，。 例如，如果應用程式是以 .NET Framework 3.5 和 .NET Framework 4 為目標，請使用 [2.0.50727.0 版本號碼，而 XML 應如下所示：

   ```xml
   <dependency>
     <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
       <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />
     </dependentAssembly>
   </dependency>
   ```

### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>更新並重新簽署應用程式和部署資訊清單

- 更新並重新簽署應用程式和部署資訊清單。 如需詳細資訊，請參閱[如何：重新簽署應用程式和部署資訊清單](../deployment/how-to-re-sign-application-and-deployment-manifests.md)。

## <a name="see-also"></a>另請參閱
- [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [\<compatibleFrameworks> 元素](../deployment/compatibleframeworks-element-clickonce-deployment.md)
- [\<dependency> 元素](../deployment/dependency-element-clickonce-application.md)
- [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)
- [組態檔結構描述](/dotnet/framework/configure-apps/file-schema/index)
