---
title: 安全性和當地語系化附屬組件 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b4c153697d95f1496ee3380f63c48d0e4521c05a
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54781017"
---
# <a name="security-and-localized-satellite-assemblies"></a>安全性和當地語系化附屬組件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您的主要組件使用強式命名，則必須使用與主要組件相同的私密金鑰來簽署附屬組件。 如果主要與附屬組件的公開/私密金鑰組不符，則不會載入資源。 如需簽署組件的詳細資訊，請參閱[如何：使用強式名稱簽署組件](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67)。  
  
 一般而言，您可能需要讓組織的簽署群組或外部簽署組織使用私密金鑰進行簽署。 原因是私密金鑰具有機密本質︰通常只有少數人才能進行存取。 您可以在開發期間使用延遲簽署。 如需詳細資訊，請參閱[延遲簽署組件](http://msdn.microsoft.com/library/9d300e17-5bf1-4360-97da-2aa55efd9070)。  
  
## <a name="see-also"></a>請參閱  
 [組件安全性考量](http://msdn.microsoft.com/library/1b5439c1-f3d5-4529-bd69-01814703d067)   
 [重要的安全性概念](http://msdn.microsoft.com/library/3cfced4f-ea02-4e66-ae98-d69286363e98)   
 [以 .NET Framework 為基礎的國際應用程式簡介](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [當地語系化應用程式](../ide/localizing-applications.md)   
 [全球化和當地語系化應用程式](../ide/globalizing-and-localizing-applications.md)
