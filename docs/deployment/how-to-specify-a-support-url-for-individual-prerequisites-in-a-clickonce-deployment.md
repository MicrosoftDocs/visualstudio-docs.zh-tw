---
title: 如何： 指定 ClickOnce 部署中的個別必要條件的支援 URL |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02dfd64d7a6b3a2ffae49e5693bdac8ebdf2ad0f
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815645"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>如何：在 ClickOnce 部署中指定個別必要條件的支援 URL
A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署可以測試數目的用戶端電腦必須要有的必要條件[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]執行應用程式。 這些相依性包括必要的最小版本[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]，作業系統，必須預先安裝在全域組件快取 (GAC) 中的任何組件的版本。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]不過，無法安裝這些必要條件的任何本身;如果找不到必要元件，它只是中止安裝，並顯示對話方塊，說明安裝失敗的原因。  
  
 有兩種方法來安裝的必要條件。 您可以使用啟動載入器應用程式進行安裝。 或者，您可以指定個別必要條件的支援 URL 找不到必要條件時，會顯示在對話方塊中的使用者。 參考該 URL 的頁面可以包含安裝必要的先決條件的指示連結。 如果應用程式未指定為個別的必要條件的支援 URL[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]顯示整個應用程式的部署資訊清單中指定的支援 URL，如果已定義。  
  
 雖然[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，Mage.exe 和 MageUI.exe 都用來產生[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署中，這些工具不直接支援指定個別必要條件的支援 URL。 本文件說明如何修改您部署的應用程式資訊清單和部署資訊清單，以包含這些支援 Url。  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>指定個別必要條件的支援 URL  
  
1.  開啟應用程式資訊清單 (`.manifest`檔案) 的程式[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]文字編輯器中的應用程式。  
  
2.  若是作業系統必要條件，新增`supportUrl`屬性`dependentOS`項目：  
  
    ```xml  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3.  通用語言執行平台特定版本的必要條件，如新增`supportUrl`屬性`dependentAssembly`指定通用語言執行階段相依性的項目：  
  
    ```xml  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  對於必須預先安裝在全域組件快取中的組件的必要條件、 設定`supportUrl`如`dependentAssembly`項目，指定必要的組件：  
  
    ```xml  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  選擇性。 .NET Framework 4 為目標的應用程式開啟部署資訊清單 (`.application`檔案) 的程式[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]文字編輯器中的應用程式。  
  
6.  .NET Framework 4 必要條件，新增`supportUrl`屬性`compatibleFrameworks`項目：  
  
    ```xml  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  一旦您手動變更應用程式資訊清單，您必須重新簽署應用程式資訊清單使用數位憑證，然後更新並重新簽署部署資訊清單。 使用 Mage.exe 或 MageUI.exe SDK 工具來完成這項工作，以重新產生這些檔案使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]會清除您手動變更。 如需有關使用 Mage.exe 重新簽署資訊清單的詳細資訊，請參閱[如何： 重新簽署應用程式和部署資訊清單](../deployment/how-to-re-sign-application-and-deployment-manifests.md)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 支援 URL 不會顯示在對話方塊中，如果應用程式標示為在部分信任中執行。  
  
## <a name="see-also"></a>另請參閱  
 [Mage.exe (資訊清單產生和編輯工具)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<w > 項目](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)   
 [應用程式部署必要條件](../deployment/application-deployment-prerequisites.md)