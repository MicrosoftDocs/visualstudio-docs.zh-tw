---
title: 當地語系化的中性資源語言
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- localization [Visual Studio], resources
- NeutralResourcesLanguageAttribute class
- globalization [Visual Studio], resources
- resources [Visual Studio], fallback system
- culture, locating resources
- neutral resources
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e246d31a3c3126f28cd6be383b368a1373118504
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916805"
---
# <a name="neutral-resources-languages-for-localization"></a>當地語系化的中性資源語言

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

- <xref:System.Resources.ResourceManager>
- [以 .NET Framework 為基礎的國際應用程式簡介](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)
- [階層式組織當地語系化的資源](../ide/hierarchical-organization-of-resources-for-localization.md)
- [當地語系化應用程式](../ide/localizing-applications.md)
- [全球化和當地語系化應用程式](../ide/globalizing-and-localizing-applications.md)