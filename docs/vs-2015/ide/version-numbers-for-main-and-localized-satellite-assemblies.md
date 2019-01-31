---
title: 主要和當地語系化附屬組件的版本號碼 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- satellite assemblies, version numbers
- SatelliteContractVersionAttribute
- version numbers, assemblies
- assemblies [Visual Studio], version numbers
- versioning, assemblies
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: eb699c7b5ab2aec928bf83ada5dd8824f93f3006
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790135"
---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>主要和當地語系化附屬組件的版本號碼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:System.Resources.SatelliteContractVersionAttribute> 類別針對透過資源管理員使用當地語系化資源的主要組件提供了版本控制支援。 將 <xref:System.Resources.SatelliteContractVersionAttribute> 套用至應用程式的主要組件，可讓您更新和重新部署該組件，而不需要更新其附屬組件。 例如，您可以搭配未引進新資源的 Service Pack 使用 <xref:System.Resources.SatelliteContractVersionAttribute> 類別，而不需要重建和重新部署您的附屬組件。 若要使用當地語系化資源，主要組件的附屬合約版本必須與附屬組件的 <xref:System.Reflection.AssemblyVersionAttribute> 類別相符。 您必須在 <xref:System.Resources.SatelliteContractVersionAttribute> 中指定確切的版本號碼；不允許萬用字元，例如 "*"。 如需詳細資訊，請參閱[擷取資源](http://msdn.microsoft.com/library/eca16922-1c46-4f68-aefe-e7a12283641f)。  
  
## <a name="updating-assemblies"></a>更新組件  
 <xref:System.Resources.SatelliteContractVersionAttribute> 類別可讓您更新主要組件，而不需要更新您的附屬組件，反之亦然。 更新主要組件時，即會變更其組件版本號碼。 如果您要繼續使用現有附屬組件，請變更主要組件的版本號碼，但保留附屬合約版本號碼不變。 例如，第一次發行時，您的主要組件版本可能是 1.0.0.0。 附屬合約版本和附屬組件的組件版本也會是 1.0.0.0。 如果您因為 Service Pack 而需要更新主要組件，您可以將組件版本變更為 1.0.0.1，但將附屬合約版本和附屬組件版本保留為 1.0.0.0。  
  
 如果您需要更新附屬組件而不是主要組件，可以變更附屬組件的 <xref:System.Reflection.AssemblyVersionAttribute>。 除了交付附屬組件之外，您還必須附上原則組件來說明新的附屬組件與舊的附屬組件相容。 如需原則的詳細資訊，請參閱[執行階段如何找出組件](http://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34)。  
  
 下列程式碼示範如何設定附屬合約版本。 您可以將這段程式碼放入建置指令碼或是 AssemblyInfo.vb 或 AssemblyInfo.cs 檔中。  
  
```vb  
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>  
  
```  
  
```csharp  
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]  
```  
  
## <a name="see-also"></a>請參閱  
 [執行階段如何找出組件](http://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34)   
 [設定組件屬性](http://msdn.microsoft.com/library/36a98a81-b5b5-4c19-912a-11f91eff7f4e)   
 [安全性和當地語系化附屬組件](../ide/security-and-localized-satellite-assemblies.md)   
 [當地語系化應用程式](../ide/localizing-applications.md)   
 [全球化和當地語系化應用程式](../ide/globalizing-and-localizing-applications.md)
