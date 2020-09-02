---
title: 如何：在 ClickOnce 部署中指定個別必要條件的支援 URL |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1907b619bcc616c73d9b9e37af30722c02bf100e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65679963"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>如何：在 ClickOnce 部署中指定個別必要條件的支援 URL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]部署可以測試用戶端電腦上必須提供的一些必要條件， [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式才能執行。 這些包括所需的最低版本 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 、作業系統版本，以及必須預先安裝在全域組件快取 (GAC) 中的任何元件。 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]但是，無法安裝任何這些必要條件，如果找不到必要條件，它只會中止安裝，並顯示一個對話方塊來說明安裝失敗的原因。  
  
 有兩種方法可以安裝必要條件。 您可以使用啟動載入器應用程式來安裝它們。 或者，您可以指定個別必要條件的支援 URL，如果找不到必要條件，則會在對話方塊中顯示給使用者。 該 URL 所參考的頁面可以包含安裝必要必要條件之指示的連結。 如果應用程式未指定個別必要條件的支援 URL，則會 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 顯示整個應用程式的部署資訊清單中所指定的支援 url （若已定義）。  
  
 雖然 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 、Mage.exe 和 MageUI.exe 都可以用來產生 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 部署，但是這些工具都不是直接支援指定個別必要條件的支援 URL。 本檔說明如何修改部署的應用程式資訊清單和部署資訊清單，以包含這些支援 Url。  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>指定個別必要條件的支援 URL  
  
1. 在文字編輯器中開啟應用程式的 (清單檔) 的應用程式資訊清單。 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]  
  
2. 針對作業系統必要條件，將 `supportUrl` 屬性新增至 `dependentOS` 元素：  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3. 針對特定版本的 common language runtime，請將 `supportUrl` 屬性新增至 `dependentAssembly` 指定 common language runtime 相依性的專案：  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4. 針對必須預先安裝在全域組件快取中之元件的必要條件，請為 `supportUrl` `dependentAssembly` 指定必要元件的元素設定：  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5. 選擇性。 針對以 .NET Framework 4 為目標的應用程式，請 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 在文字編輯器中開啟應用程式) 的應用程式檔 (的部署資訊清單。  
  
6. 針對 .NET Framework 4 必要條件，請將 `supportUrl` 屬性新增至 `compatibleFrameworks` 元素：  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7. 當您手動變更應用程式資訊清單之後，您必須使用數位憑證重新簽署應用程式資訊清單，然後再更新並重新簽署部署資訊清單。 您必須使用 Mage.exe 或 MageUI.exe SDK 工具來完成這項工作，因為重新產生這些檔案時，會 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 清除手動變更。 如需有關如何使用 Mage.exe 來重新簽署資訊清單的詳細資訊，請參閱 < [如何：重新簽署應用程式和部署資訊清單](../deployment/how-to-re-sign-application-and-deployment-manifests.md)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 如果應用程式標示為在部分信任中執行，則不會在對話方塊上顯示支援 URL。  
  
## <a name="see-also"></a>另請參閱  
 [Mage.exe (資訊清單產生和編輯工具) ](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks> 元素](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)   
 [應用程式部署必要條件](../deployment/application-deployment-prerequisites.md)
