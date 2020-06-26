---
title: ClickOnce 部署中必要條件的支援 URL
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf474e4926403a9475860bfdc620ee4a6860f8aa
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85381726"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>如何：在 ClickOnce 部署中指定個別必要條件的支援 URL
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署可以測試用戶端電腦上必須提供的幾個必要條件， [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式才能執行。 這些相依性包括所需的最小 .NET Framework 版本、作業系統版本，以及必須預先安裝在全域組件快取（GAC）中的任何元件。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]不過，無法自行安裝任何必要條件;如果找不到必要條件，它只會中止安裝，並顯示對話方塊說明安裝失敗的原因。

 有兩種方法可以安裝必要條件。 您可以使用啟動載入器應用程式來安裝它們。 或者，您也可以指定個別必要條件的支援 URL，如果找不到先決條件，就會在對話方塊上對使用者顯示。 該 URL 所參考的頁面可以包含安裝必要必要條件的指示連結。 如果應用程式未指定個別必要條件的支援 URL，則會 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 顯示整個應用程式的部署資訊清單中指定的支援 url （如果已定義的話）。

 雖然 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 、 *Mage.exe*和*MageUI.exe*都可以用來產生 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署，但這些工具都不直接支援針對個別必要條件指定支援 URL。 本檔說明如何修改部署的應用程式資訊清單和部署資訊清單，以包含這些支援 Url。

### <a name="specify-a-support-url-for-an-individual-prerequisite"></a>指定個別必要條件的支援 URL

1. 在文字編輯器中，開啟應用程式的應用程式資訊清單（ *.manifest*檔案） [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。

2. 針對作業系統必要條件，請將屬性新增 `supportUrl` 至 `dependentOS` 元素：

   ```xml
    <dependency>
       <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">
         <osVersionInfo>
           <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />
         </osVersionInfo>
       </dependentOS>
     </dependency>
   ```

3. 針對特定版本通用語言執行平臺的必要條件，請將 `supportUrl` 屬性加入至 `dependentAssembly` 指定 common language runtime 相依性的專案：

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">
         <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />
       </dependentAssembly>
     </dependency>
   ```

4. 對於必須預先安裝在全域組件快取中之元件的必要條件，請 `supportUrl` 針對 `dependentAssembly` 指定所需元件的元素設定：

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">
         <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />
       </dependentAssembly>
     </dependency>
   ```

5. 選擇性。 若是以 .NET Framework 4 為目標的應用程式，請在文字編輯器中開啟應用程式的部署資訊清單（*應用程式*檔）。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]

6. 針對 .NET Framework 4 必要條件，請將 `supportUrl` 屬性新增至 `compatibleFrameworks` 元素：

   ```xml
   <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">
     <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />
     <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />
   </compatibleFrameworks>
   ```

7. 當您手動變更應用程式資訊清單之後，您必須使用數位憑證重新簽署應用程式資訊清單，然後再更新並重新簽署部署資訊清單。 使用*Mage.exe*或*MageUI.exe* SDK 工具來完成這項工作，因為使用清除手動變更重新產生這些檔案 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。 如需有關如何使用 Mage.exe 來重新簽署資訊清單的詳細資訊，請參閱 < [如何：重新簽署應用程式和部署資訊清單](../deployment/how-to-re-sign-application-and-deployment-manifests.md)。

## <a name="net-framework-security"></a>.NET Framework 安全性
 如果應用程式標示為在部分信任中執行，則支援 URL 不會顯示在對話方塊中。

## <a name="see-also"></a>另請參閱
- [Mage.exe （資訊清單產生和編輯工具）](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [\<compatibleFrameworks>元素](../deployment/compatibleframeworks-element-clickonce-deployment.md)
- [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)
- [應用程式部署必要條件](../deployment/application-deployment-prerequisites.md)