---
title: 安全性和當地語系化附屬組件
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- key pairs for strong-named assemblies
- strong-named assemblies, security considerations
- satellite assemblies, localized
- code signing, assemblies
- security [Visual Studio], assemblies
- strong-named assemblies, localized
- assemblies [Visual Studio], security
- localization, satellite assemblies
ms.assetid: 6d953840-b301-47d5-8d34-30c1b29b5071
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4d0c38ae4353c7761b1cff4173b995ab6c89e0a4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53892049"
---
# <a name="security-and-localized-satellite-assemblies"></a>安全性和當地語系化附屬組件

如果您的主要組件使用強式命名，則必須使用與主要組件相同的私密金鑰來簽署附屬組件。 如果主要與附屬組件的公開/私密金鑰組不符，則不會載入資源。 如需簽署組件的詳細資訊，請參閱[如何：使用強式名稱簽署組件](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)。

 一般而言，您可能需要讓組織的簽署群組或外部簽署組織使用私密金鑰進行簽署。 原因是私密金鑰具有機密本質︰通常只有少數人才能進行存取。 您可以在開發期間使用延遲簽署。 如需詳細資訊，請參閱 [延遲簽署組件](/dotnet/framework/app-domains/delay-sign-assembly)。

## <a name="see-also"></a>另請參閱

- [組件安全性考量](/dotnet/framework/app-domains/assembly-security-considerations)  - [重要的安全性概念](/dotnet/standard/security/key-security-concepts)
- [以 .NET Framework 為基礎的國際應用程式簡介](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)
- [當地語系化應用程式](../ide/localizing-applications.md)
- [全球化和當地語系化應用程式](../ide/globalizing-and-localizing-applications.md)