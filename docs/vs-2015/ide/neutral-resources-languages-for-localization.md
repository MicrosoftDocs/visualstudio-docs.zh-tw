---
title: 當地語系化的中性資源語言 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- localization [Visual Studio], resources
- NeutralResourcesLanguageAttribute class
- globalization [Visual Studio], resources
- resources [Visual Studio], fallback system
- culture, locating resources
- neutral resources
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85e0be0172f27732f8efeb882cbcde5b9c6aef3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670381"
---
# <a name="neutral-resources-languages-for-localization"></a>當地語系化的中性資源語言
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:System.Resources.NeutralResourcesLanguageAttribute> 類別指定主要組件中所含資源的文化特性 (Culture)。 此屬性用作效能增強，因此 <xref:System.Resources.ResourceManager> 物件不會搜尋主要組件中所含的資源。

 下列程式碼示範如何設定中性資源語言。 您可以將這段程式碼放入建置指令碼或是 AssemblyInfo.vb 或 AssemblyInfo.cs 檔中。

```vb
' Set neutral resources language for assembly.
<Assembly: NeutralResourcesLanguageAttribute("en")>

```

```csharp
// Set neutral resources language for assembly.
[assembly: NeutralResourcesLanguageAttribute("en")]
```

## <a name="see-also"></a>另請參閱
 <xref:System.Resources.ResourceManager>[根據 .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md) [階層式組織資源的階層式組織簡介當地語系化](../ide/hierarchical-organization-of-resources-for-localization.md)[應用程式](../ide/localizing-applications.md)[全球化和當地語系化應用](../ide/globalizing-and-localizing-applications.md)程式
