---
title: ClickOnce 部署中必要條件的支援 URL
description: 瞭解 ClickOnce 部署如何測試要執行 ClickOnce 應用程式的必要條件，以及部署如何處理遺漏的必要條件。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 585ea1a558b91ac733670ad94a9a3e0be33f1348
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876312"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>如何：在 ClickOnce 部署中指定個別必要條件的支援 URL
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署可以測試用戶端電腦上必須提供的一些必要條件， [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式才能執行。 這些相依性包括必要的最小 .NET Framework 版本、作業系統版本，以及必須預先安裝在全域組件快取 (GAC) 中的任何元件。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]但是，無法安裝任何這些必要條件，如果找不到必要條件，它只會中止安裝，並顯示一個對話方塊來說明安裝失敗的原因。

 有兩種方法可以安裝必要條件。 您可以使用啟動載入器應用程式來安裝它們。 或者，您可以指定個別必要條件的支援 URL，如果找不到必要條件，則會在對話方塊中顯示給使用者。 該 URL 所參考的頁面可以包含安裝必要必要條件之指示的連結。 如果應用程式未指定個別必要條件的支援 URL，則會 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 顯示整個應用程式的部署資訊清單中所指定的支援 url （若已定義）。

 雖然 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 、 *Mage.exe* 和 *MageUI.exe* 都可以用來產生 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署，但是這些工具都不是直接支援指定個別必要條件的支援 URL。 本檔說明如何修改部署的應用程式資訊清單和部署資訊清單，以包含這些支援 Url。

### <a name="specify-a-support-url-for-an-individual-prerequisite"></a>指定個別必要條件的支援 URL

1. 開啟應用程式資訊清單 (在文字編輯器中針對應用程式) 的 *資訊清單* 檔。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]

2. 針對作業系統必要條件，將 `supportUrl` 屬性新增至 `dependentOS` 元素：

   ```xml
    <dependency>
       <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">
         <osVersionInfo>
           <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />
         </osVersionInfo>
       </dependentOS>
     </dependency>
   ```

3. 針對特定版本的 common language runtime，請將 `supportUrl` 屬性新增至 `dependentAssembly` 指定 common language runtime 相依性的專案：

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">
         <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />
       </dependentAssembly>
     </dependency>
   ```

4. 針對必須預先安裝在全域組件快取中之元件的必要條件，請為 `supportUrl` `dependentAssembly` 指定必要元件的元素設定：

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">
         <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />
       </dependentAssembly>
     </dependency>
   ```

5. 選擇性。 針對以 .NET Framework 4 為目標的應用程式，請 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 在文字編輯器中開啟應用程式的 [應用程式檔] () 的部署資訊清單。

6. 針對 .NET Framework 4 必要條件，請將 `supportUrl` 屬性新增至 `compatibleFrameworks` 元素：

   ```xml
   <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">
     <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />
     <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />
   </compatibleFrameworks>
   ```

7. 當您手動變更應用程式資訊清單之後，您必須使用數位憑證重新簽署應用程式資訊清單，然後再更新並重新簽署部署資訊清單。 使用 *Mage.exe* 或 *MageUI.exe* SDK 工具來完成這項工作，因為使用清除手動變更來重新產生這些檔案 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。 如需有關如何使用 Mage.exe 來重新簽署資訊清單的詳細資訊，請參閱 < [如何：重新簽署應用程式和部署資訊清單](../deployment/how-to-re-sign-application-and-deployment-manifests.md)。

## <a name="net-framework-security"></a>.NET Framework 安全性
 如果應用程式標示為在部分信任中執行，則不會在對話方塊上顯示支援 URL。

## <a name="see-also"></a>另請參閱
- [Mage.exe (資訊清單產生和編輯工具) ](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [\<compatibleFrameworks> 元素](../deployment/compatibleframeworks-element-clickonce-deployment.md)
- [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)
- [應用程式部署必要條件](../deployment/application-deployment-prerequisites.md)